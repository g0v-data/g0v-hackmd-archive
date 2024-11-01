# OpenBMC callback std::forward & std::move

## R value & L Value
就我的理解 
lvalue 就是可以被叫出名字的 例如 x, struct t...
rvalue 則是臨時產生的 例如 10 , string("hello")
也可以不精確地說成 lvalue都在左邊 而 rvalue都在右邊 (非常不精確但比較白話點)

## 右值引用 和 左值引用

假設有一個段程式碼如下:
```
#include <iostream>
#include <string>

void process(const std::string& s) {
    std::cout << "Lvalue reference: " << s << std::endl;
}

void process(std::string&& s) {
    std::cout << "Rvalue reference (moved): " << s << std::endl;
}


std::string createString() {
    return "Hello";
}

int main() {
    std::string str = "World";
    callProcess(str);             // str 是左值，調用左值版本
    callProcess(createString());   // createString() 是右值，調用右值版本
}
```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bc874b9a35a7dfd5e2496c0d499615cd.png)


---

## 特別提到右值引用
這段程式碼在OBMC內 callback 中有相當多學問
```
template <typename Callback>
void getObjectsWithConnection(
    const std::shared_ptr<SensorsAsyncResp>& sensorsAsyncResp,
    const std::shared_ptr<std::set<std::string>>& sensorNames,
    Callback&& callback)
{
    BMCWEB_LOG_DEBUG << "getObjectsWithConnection enter";
    const std::string path = "/xyz/openbmc_project/sensors";
    const std::array<std::string, 1> interfaces = {
        "xyz.openbmc_project.Sensor.Value"};

    // Response handler for parsing objects subtree
    auto respHandler =
        [callback{std::forward<Callback>(callback)}, sensorsAsyncResp,
         sensorNames](const boost::system::error_code ec,
                      const dbus::utility::MapperGetSubTreeResponse& subtree) {
        BMCWEB_LOG_DEBUG << "getObjectsWithConnection resp_handler enter";
        
        ... 省略

        // Make unique list of connections only for requested sensor types and
        // found in the chassis
        std::set<std::string> connections;
        std::set<std::pair<std::string, std::string>> objectsWithConnection;

        ... 省略
        
        BMCWEB_LOG_DEBUG << "Found " << connections.size() << " connections";
        callback(std::move(connections), std::move(objectsWithConnection));
        BMCWEB_LOG_DEBUG << "getObjectsWithConnection resp_handler exit";
    };
    // Make call to ObjectMapper to find all sensors objects
    crow::connections::systemBus->async_method_call(
        std::move(respHandler), "xyz.openbmc_project.ObjectMapper",
        "/xyz/openbmc_project/object_mapper",
        "xyz.openbmc_project.ObjectMapper", "GetSubTree", path, 0, interfaces);
    BMCWEB_LOG_DEBUG << "getObjectsWithConnection exit";
}
```

這裡有兩個重點討論

    auto respHandler =
        [callback{std::forward<Callback>(callback)}, sensorsAsyncResp,
         sensorNames](const boost::system::error_code ec,
                      const dbus::utility::MapperGetSubTreeResponse& subtree)
                      
    AND
    
    callback(std::move(connections), std::move(objectsWithConnection));

首先是 ```respHandler``` 這個callback 使用到的 ```std::forward```
和 ```callback``` 內使用的 ```std::move```


以下這段程式碼來解釋 ```std::forward``` 的用意

```
#include <iostream>
#include <string>
#include <utility>  // for std::forward

void process(const std::string& s) {
    std::cout << "Lvalue reference: " << s << std::endl;
}

void process(std::string&& s) {
    std::cout << "Rvalue reference (moved): " << s << std::endl;
}

template <typename T>
void callProcess(T&& s) {
    // 使用 std::forward 保留 s 的原始屬性
    process(std::forward<T>(s));
}

std::string createString() {
    return "Hello";
}

int main() {
    std::string str = "World";
    callProcess(str);             // str 是左值，調用左值版本
    callProcess(createString());   // createString() 是右值，調用右值版本
}

```
簡單來說就是 ```std::foward``` 可以自動判斷進來的是右值還是左值並保留其特性
好處就是避免了額外的拷貝或非必要的轉換。
```callProcess``` 的模板參數 ```T``` 使用 ```T&&```（稱為「通用引用」或「轉發引用」）是必要的，這是 ```std::forward``` 能夠完美轉發的關鍵所在。如果改為 ```T&```，則無法達到相同的效果，無法實現「保留右值屬性」的功能。

若改成 ```T&``` 的話，就限制了右值引用 **(變相地限制「只接受左值引用，不接受複製」)**

第二個 ```std::move``` 的使用在這邊用在了兩個 ```std::set``` 上面， 有在做題的人可能清楚當這些container內的資料龐大時，複製所帶來的資源消耗大，而這邊兩個 ```std::move``` 被用來將 ```connections``` 和 ```objectsWithConnection``` 移動到 ```callback``` 中。這意味著這些集合將以右值的形式傳遞給回調函數，這樣的設計避免不必要的拷貝。

話是這麼說但我和ChatGPT來回確認了好多次這邊是否有使用 ```std::move``` 的必要，因為原始的callback定義是用左值引用
```
template <typename Callback>
void getConnections(std::shared_ptr<SensorsAsyncResp> sensorsAsyncResp,
                    const std::shared_ptr<std::set<std::string>> sensorNames,
                    Callback&& callback)
{
    auto objectsWithConnectionCb =
        [callback](const std::set<std::string>& connections,
                   const std::set<std::pair<std::string, std::string>>&
                   /*objectsWithConnection*/) { callback(connections); };
    getObjectsWithConnection(sensorsAsyncResp, sensorNames,
                             std::move(objectsWithConnectionCb));
}
```
既然兩個 ```std::set``` 都已經是左值引用了，這邊理論上不需要在用 ```std::move``` 才對
希望我的理解沒有錯誤

附上ChatGPT的回答:

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4baab28df8cabf43e9c409f171e63dee.png)



