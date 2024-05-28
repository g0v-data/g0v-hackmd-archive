##### eventtype.cpp
```cpp=
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
                case sf::Event::Closed:
                    window.close();
                    break;

                // 鍵盤按下事件
                case sf::Event::KeyPressed:
                    if (event.key.code == sf::Keyboard::Escape) {
                        window.close();
                    } else {
                        std::cout << "Key pressed: " << event.key.code << std::endl;
                    }
                    break;

                // 滑鼠按下事件
                case sf::Event::MouseButtonPressed:
                    if (event.mouseButton.button == sf::Mouse::Left) {
                        std::cout << "Left mouse button pressed at (" << event.mouseButton.x << ", " << event.mouseButton.y << ")" << std::endl;
                    }
                    break;

                // 視窗大小改變事件
                case sf::Event::Resized:
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
