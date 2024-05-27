WSL2
===
SFML installation
---
##### 使用apt-get下載SFML
```
sudo apt-get libsfml-dev
```

##### 查看安裝版本資訊＆路徑
```
apt-get info libsfml-dev
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
:::info
:bulb: **Hint:** **按 esc -> : -> wq 退出**
:::

測試編譯與執行
---

##### 找到lib路徑

```
不確定是不是要這樣找跟編譯
```
###### 由圖片中，以此電腦為例，我們會知道路徑是 
`include 的路徑:` `/opt/homebrew/Cellar/sfml/2.6.1/include`
`sfml lib 的路徑:` `/opt/homebrew/Cellar/sfml/2.6.1/lib`

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1a727d3536e6d5d6716bbd50f1bbd031.png)

##### 編譯指令
```
g++ sfml.cpp -I<你的include路徑> -o prog -L/<你的lib路徑> -lsfml-graphics -lsfml-window -lsfml-system 
```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6b66202c8251e54f8ae322ede6619bef.png)


##### 執行
```
./prog
```

###### 跑出視窗即為成功
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b958d67392a6fda8f2b89ddadb80d036.png)



