sf::Clock  Class 
---

#### include正確的module
```clike
#include <SFML/System/Clock.hpp>
#include <SFML/System/Time.hpp>
```

#### 創建一個時鐘對象
###### 時鐘一創建即開始計時
```clike
sf::Clock clock;
```
#### 重置時鐘
###### 重置時間
###### 並回傳時鐘重置前經過的時間
```clike
sf::Time elapsed = clock.restart();
```

#### 獲取重置後的經過時間
```clike
int elapsed = clock.getElapsedTime();
```

#### 暫停500毫秒
```clike
 sf::sleep(sf::milliseconds(500)); 
```

##### clock.cpp
```cpp=
#include <SFML/System/Clock.hpp>
#include <SFML/System/Time.hpp>
#include <SFML/System/Sleep.hpp>
#include <iostream>

int main() {
    // 創建一個時鐘對象
    sf::Clock clock;

    // 模擬一些工作
    sf::sleep(sf::milliseconds(500)); // 暫停500毫秒

    // 重置時鐘並獲取重置前的時間
    sf::Time elapsed = clock.restart();
    std::cout << "Elapsed time before restart: " << elapsed.asMilliseconds() << " milliseconds" << std::endl;

    // 再次模擬一些工作
    sf::sleep(sf::milliseconds(300)); // 暫停300毫秒

    // 獲取重置後的經過時間
    elapsed = clock.getElapsedTime();
    std::cout << "Elapsed time after restart: " << elapsed.asMilliseconds() << " milliseconds" << std::endl;

    return 0;
}
```
