# sf::Vector2<T> Class 實作

#### include正確的module
```clike
#include <SFML/System/Vector2.hpp>
```

#### 宣告二維向量
###### Vector2<int> 可以縮寫成 Vector2i
###### Vector2<int> 可以縮寫成 Vector2i
```cpp=
sf::Vector2<int> v1(1, 2);
sf::Vector2i v2(3, 4);
sf::Vector2<float> v3(3.3, 4.4);
sf::Vector2f v4(5.5, 6.6);
```

#### 向量運算
```cpp=
sf::Vector2i v5 = v1 + v2;
sf::Vector2i v6 = v2 - v1;
sf::Vector2f v7 = v3 + v4;
sf::Vector2f v8 = v4 - v3;
sf::Vector2<float> v9 = 3.0f * v3;
sf::Vector2<int> v10 = 3 * v1;
```

#### 輸出
```cpp=
std::cout << '(' << v5.x << ',' << v5.y << ')' << std::endl;
std::cout << '(' << v6.x << ',' << v6.y << ')' << std::endl;
std::cout << '(' << v7.x << ',' << v7.y << ')' << std::endl;
std::cout << '(' << v8.x << ',' << v8.y << ')' << std::endl;
std::cout << '(' << v9.x << ',' << v9.y << ')' << std::endl;
std::cout << '(' << v10.x << ',' << v10.y << ')' << std::endl;
```

##### 完整範例code
```cpp=
#include<iostream>
#include <SFML/System/Vector2.hpp>

int main() {
    sf::Vector2<int> v1(1, 2);
    sf::Vector2i v2(3, 4);
    sf::Vector2<float> v3(3.3, 4.4);
    sf::Vector2f v4(5.5, 6.6);

    sf::Vector2i v5 = v1 + v2;
    sf::Vector2i v6 = v2 - v1;
    sf::Vector2f v7 = v3 + v4;
    sf::Vector2f v8 = v4 - v3;
    sf::Vector2<float> v9 = 3.0f * v3;
    sf::Vector2<int> v10 = 3 * v1;

    std::cout << '(' << v5.x << ',' << v5.y << ')' << std::endl;
    std::cout << '(' << v6.x << ',' << v6.y << ')' << std::endl;
    std::cout << '(' << v7.x << ',' << v7.y << ')' << std::endl;
    std::cout << '(' << v8.x << ',' << v8.y << ')' << std::endl;
    std::cout << '(' << v9.x << ',' << v9.y << ')' << std::endl;
    std::cout << '(' << v10.x << ',' << v10.y << ')' << std::endl;

    return 0;
}
```

    