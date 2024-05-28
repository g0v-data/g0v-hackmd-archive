##### vertex.cpp


```cpp=
#include <SFML/Graphics.hpp>
#include <iostream>

int main() {
    // 創建一個視窗
    sf::RenderWindow window(sf::VideoMode(800, 600), "SFML Vertex Example");

    // 創建兩個頂點來表示一條直線
    sf::Vertex line[] = {
        sf::Vertex(sf::Vector2f(100, 100), sf::Color::Red),
        sf::Vertex(sf::Vector2f(700, 500), sf::Color::Blue)
    };

    // 主循環
    while (window.isOpen()) {
        sf::Event event;
        while (window.pollEvent(event)) {
            if (event.type == sf::Event::Closed)
                window.close();
        }

        // 清除視窗
        window.clear();

        // 繪製直線
        window.draw(line, 2, sf::Lines);

        // 顯示內容
        window.display();
    }

    return 0;
}
```
