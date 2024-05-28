sf::Clock  Class 實作
---

#### include正確的module
```clike
#include <SFML/System/Clock.hpp>
#include <SFML/System/Time.hpp>
```

#### 創建一個時鐘對象
```clike
sf::Clock clock;
```

#### 暫停500毫秒
```clike
 sf::sleep(sf::milliseconds(500)); 
```

#### 重置時鐘並獲取重置前的時間
```clike
sf::Time elapsed = clock.restart();
```

    