## `sf::Vector2<T>`  實作


### 1. include正確的module
```clike
#include <SFML/System/Vector2.hpp>
```

### 2. 宣告二維向量
###### Vector2<int> 可以縮寫成 Vector2i
###### Vector2<int> 可以縮寫成 Vector2i
```cpp
    sf::Vector2<int> v1(1, 2);
    sf::Vector2i v2(3, 4);
    sf::Vector2<float> v3(3.3, 4.4);
    sf::Vector2f v4(5.5, 6.6);
```
### 3. 運算&輸出
#### 向量運算
```cpp
    sf::Vector2i v5 = v1 + v2;
    sf::Vector2i v6 = v2 - v1;
    sf::Vector2f v7 = v3 + v4;
    sf::Vector2f v8 = v4 - v3;
    sf::Vector2<float> v9 = 3.0f * v3;
    sf::Vector2<int> v10 = 3 * v1;
```

#### 輸出
```cpp
    std::cout << '(' << v5.x << ',' << v5.y << ')' << std::endl;
    std::cout << '(' << v6.x << ',' << v6.y << ')' << std::endl;
    std::cout << '(' << v7.x << ',' << v7.y << ')' << std::endl;
    std::cout << '(' << v8.x << ',' << v8.y << ')' << std::endl;
    std::cout << '(' << v9.x << ',' << v9.y << ')' << std::endl;
    std::cout << '(' << v10.x << ',' << v10.y << ')' << std::endl;
```
## 開始實作

**描述**: 方才上課提到的類別 `sf::Vector2<T>`，代表一個向量，我們可以用`(x, y)`來代表。讓我們來使用一次向量資料吧！

#### 請完成下方程式碼空格。

##### 
```cpp=
#include<iostream>
#include <SFML/System/Vector2.hpp>

int main() {
    // 請宣告四個向量v1(1, 3), v2(2, 4), v3(1.1, 2.2), v4(3.3, 4.4)
    [ 空 格 一 ]
    [ 空 格 二 ]
    [ 空 格 三 ]
    [ 空 格 四 ]
    
    // 宣告一個 v5 為 v1 加上 v2
    // 宣告一個 v7 為 v3 加上 v4
    [ 空 格 五 ]
    sf::Vector2i v6 = v2 - v1;
    [ 空 格 六 ]
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

`[ 空 格 一 ] sf::Vector2<int> v1(1, 2);`
`[ 空 格 二 ] sf::Vector2i v2(3, 4);`
`[ 空 格 三 ] sf::Vector2<float> v3(3.3, 4.4);`
`[ 空 格 四 ] sf::Vector2f v4(5.5, 6.6);`
`[ 空 格 五 ] sf::Vector2i v5 = v1 + v2;`
`[ 空 格 六 ] sf::Vector2f v7 = v3 + v4;`
    