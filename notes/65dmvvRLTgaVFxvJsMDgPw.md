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