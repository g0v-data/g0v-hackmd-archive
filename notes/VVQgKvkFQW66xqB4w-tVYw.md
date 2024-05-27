macOS
===

SFML installation
---
##### 使用brew套件下載SFML
```
brew install sfml
```

##### 查看安裝版本資訊＆路徑
```
brew info sfml
```

創建一個測試用的sfml.cpp檔案
---

##### 創建一個sfml.cpp檔案
```
vim sfml.cpp
```

:::info
:bulb: **Hint:** **按 i --> insert mode**
:::

##### 填入sfml.cpp
```cpp
#include <SFML/Graphics.hpp>

int main()
{
    sf::RenderWindow window(sf::VideoMode(200, 200), "SFML works!");
    sf::CircleShape shape(100.f);
    shape.setFillColor(sf::Color::Green);

    while (window.isOpen())
    {
        sf::Event event;
        while (window.pollEvent(event))
        {
            if (event.type == sf::Event::Closed)
                window.close();
        }

        window.clear();
        window.draw(shape);
        window.display();
    }

    return 0;
}
```

測試編譯與執行
---

##### 找到lib路徑

```
brew info sfml
```
###### 由圖片中，以此電腦為例，我們會知道路徑是 
`include 的路徑:` `/opt/homebrew/Cellar/sfml/2.6.1/include`
`sfml lib 的路徑:` `/opt/homebrew/Cellar/sfml/2.6.1/lib`

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1a727d3536e6d5d6716bbd50f1bbd031.png)

##### 編譯指令
```
g++ sfml.cpp -I<你的include路徑> -o prog -L/<你的lib路徑> -lsfml-graphics -lsfml-window -lsfml-system 
```

##### 執行
```
./prog
```




Documentation
---
- [Features](/s/features)
- [YAML Metadata](/yaml-metadata)
- ### Publish mode
  - [Slide example](/p/slide-example)
  - [Book example](/book-example)
  - [Release notes](/s/release-notes)

Information
---
- [Terms](/s/terms)
- [Privacy](/s/privacy)

External Link
---
You could also add `[target=_blank]` to force the link open in new tab, like this:
- [Release Notes](/s/release-notes) [target=_blank]

**If you add a link starts with http (non-SSL), we'll also make it open in new tab.**
