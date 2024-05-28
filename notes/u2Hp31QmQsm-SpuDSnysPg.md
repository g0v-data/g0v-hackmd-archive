##### windows.cpp

```cpp=
#include <SFML/Graphics.hpp>


int main() {
    // 使用 Style::None
    sf::RenderWindow windowNone(sf::VideoMode(800, 600), "No Title Bar", sf::Style::None);
    // 使用 Style::Titlebar
    sf::RenderWindow windowTitlebar(sf::VideoMode(800, 600), "Title Bar", sf::Style::Titlebar);
    // 使用 Style::Resize
    sf::RenderWindow windowResize(sf::VideoMode(800, 600), "Resizable Window", sf::Style::Resize);
    // 使用 Style::Close
    sf::RenderWindow windowClose(sf::VideoMode(800, 600), "Close Button", sf::Style::Close);
    // 使用 Style::Default
    sf::RenderWindow windowDefault(sf::VideoMode(800, 600), "Default Style", sf::Style::Default);

    // 簡單的遊戲循環
    while (windowDefault.isOpen()) {
        sf::Event event;
        while (windowDefault.pollEvent(event)) {
            if (event.type == sf::Event::Closed) {
                windowDefault.close();
            }
        }

        windowDefault.clear();
        // 在這裡繪製圖形
        windowDefault.display();
    }

    return 0;
}
```
