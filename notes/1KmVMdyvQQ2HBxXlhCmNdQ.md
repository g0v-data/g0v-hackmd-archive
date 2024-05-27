# sf::Vector2<T> Class 實作

#### include正確的module
```clike
#include <SFML/System/Vector2.hpp>
```

#### 宣告二維向量
###### Vector2<int> 可以縮寫成 Vector2i
###### Vector2<int> 可以縮寫成 Vector2i
```clike
sf::Vector2<int> v1(1, 2);
sf::Vector2i v2(3, 4)
sf::Vector2<float> v3(3.3, 4.4);
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

    