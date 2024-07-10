## event type 實作

## 開始實作
**描述**: 方才上課提到的了「事件屬性」的物件，他會有許多可能的類型，例如滑鼠點擊、調整視窗大小、打鍵盤等等。

#### 請完成下方程式碼空格。

#####

```cpp
#include <SFML/Graphics.hpp>
#include <iostream>

int main() {
    // 創建一個視窗
    sf::RenderWindow window(sf::VideoMode(800, 600), "SFML Event Example");

    // 主循環
    while (window.isOpen()) {
        sf::Event event;
        while (window.pollEvent(event)) {
            switch (event.type) {
                // 視窗關閉事件
                case [ 空 格 一 ]:
                    window.close();
                    break;

                // 鍵盤按下事件
                case [ 空 格 二 ]:
                    if (event.key.code == sf::Keyboard::Escape) {
                        window.close();
                    } else {
                        std::cout << "Key pressed: " << event.key.code << std::endl;
                    }
                    break;

                // 滑鼠按下事件
                case [ 空 格 三 ]:
                    if (event.mouseButton.button == sf::Mouse::Left) {
                        std::cout << "Left mouse button pressed at (" << event.mouseButton.x << ", " << event.mouseButton.y << ")" << std::endl;
                    }
                    break;

                // 視窗大小改變事件
                case [ 空 格 四 ]:
                    std::cout << "Window resized to " << event.size.width << "x" << event.size.height << std::endl;
                    break;

                // 預設情況
                default:
                    break;
            }
        }

        // 清除視窗
        window.clear();

        // 顯示內容
        window.display();
    }

    return 0;
}
```

###### 解答：
`[ 空 格 一 ] sf::Event::Closed`
`[ 空 格 二 ]  sf::Event::KeyPressed`
`[ 空 格 三 ] sf::Event::MouseButtonPressed`
`[ 空 格 一 ] sf::Event::Resized`



