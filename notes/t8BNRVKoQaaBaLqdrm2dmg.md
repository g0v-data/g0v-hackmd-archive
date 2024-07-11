WSL2
===
SFML installation
---
##### 使用apt-get下載SFML
```
sudo apt-get install libsfml-dev
```

##### 查看安裝版本資訊＆路徑
```
apt info libsfml-dev
```

創建一個測試用的sfml.cpp檔案
---

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

##### 編譯指令
```
g++ sfml.cpp -o prog  -lsfml-graphics -lsfml-window -lsfml-system 
```
##### 執行
```
./prog
```

###### 跑出視窗即為成功
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a52d7d3b16b8a96ae3cc39c7fe3bc43c.png)

錯誤：跑不出執行畫面，切回cmd執行
---
```
wsl --update
wsl --shutdown
sudo apt update
sudo apt install gedit -y
gedit
```
##### refrence:
https://stackoverflow.com/questions/73045053/failed-to-open-x11-display-how-to-execute-sfml-output-on-wsl-load-wsl-gui-ap



