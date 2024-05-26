# Sprite and Texture 實作

### 1.匯入圖片/材質

##### Sprite就是Texture經過裁減所獲得的物件，所以在建立Sprite之前，首先我們要匯入Texture
```clike
sf::Texture texture;
if (!texture.loadFromFile("pic.png")) {

// Error handle
}
```

 ### 2.建立Sprite

##### 有了Texture之後我們就能很快的建立Sprite了
```clike
sf::Sprite sprite;
sprite.setSprite(texture);
```

### 3.畫在螢幕上的方法
```clike
window.draw(sprite);
```

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


    