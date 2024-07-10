# Sprite and Texture 實作

> ###### 先下載圖片:
>  * [download](https://drive.google.com/file/d/1J_kQ2iGQOq4kDr2FpHDvZJnTfZK8T0si/view?usp=drive_link)
> 
> ###### ⭐️ 把圖片放到當前資料夾
> 
---

### 1.匯入圖片/材質

##### Sprite就是Texture經過裁減所獲得的物件，所以在建立Sprite之前，首先我們要匯入Texture
```clike
sf::Texture texture;
if (!texture.loadFromFile("pic.png")) {

// Error handle
}
```
---
 ### 2.建立Sprite

##### 有了Texture之後我們就能很快的建立Sprite了
```clike
sf::Sprite sprite;
sprite.setSprite(texture);
```
---
### 3.畫在螢幕上的方法
```clike
window.draw(sprite);
```
---
### 4.更改Sprite的屬性或是操控它
##### 更改sprite的顏色
```clike
sprite.setColor(sf::Color(0, 255, 0));
sprite.setColor(sf::Color(255, 255, 255, 128));
```
##### 調整sprite的位置
```clike
sprite.setPosition(sf::Vector2f(10.f, 50.f)); // absolute position
sprite.move(sf::Vector2f(5.f, 10.f)); // offset relative to the current position
```
##### 旋轉sprite
```clike
sprite.setRotation(90.f); // absolute angle
sprite.rotate(15.f); // offset relative to the current angle
```
---
## 開始實作
###### 手動操作一次看看吧！會對Sprite and Texture的概念更熟悉。

#### 請完成下列空格。

```cpp=
#include <SFML/Graphics.hpp>
#include <iostream>

int main() {
    // 創建一個視窗
    sf::RenderWindow window(sf::VideoMode(800, 600), "SFML Sprite and Texture Example");
    
    // 加載紋理
    [ 空 格 一 ] 
    if ([ 空 格 二 ]) {
        std::cerr << "Error loading texture" << std::endl;
        return -1;
    }

    // 創建精靈並設置紋理
    [ 空 格 三 ]
    [ 空 格 四 ]

    // 設置精靈的位置
    sprite.setPosition(100.f, 100.f);
    //sprite.setColor(sf::Color(255, 100, 255, 128));
    //sprite.setPosition(sf::Vector2f(10.f, 50.f)); // absolute position

    // 主循環
    while (window.isOpen()) {
        sf::Event event;
        while (window.pollEvent(event)) {
            if (event.type == sf::Event::Closed)
                window.close();
        }

        // 清除視窗
        window.clear();

        //sprite.move(sf::Vector2f(5.f, 10.f)); // offset relative to the current position
        //sf::sleep( sf::milliseconds(500));

        // 繪製精靈
        [ 空 格 五 ]

        // 顯示內容
        [ 空 格 六 ]
    }

    return 0;
}
```

###### 解答

`[ 空 格 一 ] sf::Texture texture;`
`[ 空 格 二 ] !texture.loadFromFile("ball.png")`
`[ 空 格 三 ] sf::Sprite sprite;`
`[ 空 格 四 ] sprite.setTexture(texture);`
`[ 空 格 五 ] window.draw(sprite);`
`[ 空 格 六 ] window.display();`
    