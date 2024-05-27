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

#### 向量運算
```clike
sf::Vector2<int> v4 = v1 + v2;//加法
sf::Vector2<int> v5 = v2 - v2;//減法
sf::Vector2<float> v6 = 3 * v3
```

#### 輸出
```clike
std::cout << "v1: (" << v1.x << ", " << v2.y << ")" << std::endl;
std::cout << "v3: (" << v3.x << ", " << v3.y << ")" << std::endl;
```

    