##### vertexarray.cpp
```cpp=
#include <SFML/Graphics.hpp>
#include <iostream>

int main() {
    // 創建一個視窗
    sf::RenderWindow window(sf::VideoMode(800, 600), "SFML Vertex Example");

    // 創建一個三角形，由三個頂點組成
    sf::VertexArray triangle(sf::Triangles, 3);

    // 設定頂點的位置和顏色
    triangle[0].position = sf::Vector2f(400, 100);
    triangle[0].color = sf::Color::Red;

    triangle[1].position = sf::Vector2f(200, 500);
    triangle[1].color = sf::Color::Green;

    triangle[2].position = sf::Vector2f(600, 500);
    triangle[2].color = sf::Color::Blue;

    // 主循環
    while (window.isOpen()) {
        sf::Event event;
        while (window.pollEvent(event)) {
            if (event.type == sf::Event::Closed)
                window.close();
        }

        // 清除視窗
        window.clear();

        // 繪製三角形
        window.draw(triangle);

        // 顯示內容
        window.display();
    }

    return 0;
}
```
