# OBMC 內的 callback

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