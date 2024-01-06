---
title: '題目：WHEN LIGHT CURVES THROW US CURVE BALLS 當光變曲線向我們投射曲線球時 '
---

:::success
[回 2021 NASA 黑客松挑戰中文翻譯 Challenge](https://g0v.hackmd.io/4DIbh5k4R-SNBq3FdGMIjQ?both)
:::

題目：WHEN LIGHT CURVES THROW US CURVE BALLS 當光變曲線向我們投射曲線球時 
===
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1809a3e9e72cd6a361b31c92399f26c1.jpeg)

[官網原文](https://2021.spaceappschallenge.org/challenges/statements/when-light-curves-throw-us-curve-balls/details)

# Full Details 完整說明
## Summary 概述
> From Earth, the Trojan asteroids appear to be single points of light; their light curves—the way their observed brightness varies with time—are one of the few clues available to scientists working to determine the shapes of these distant bodies. Your challenge is to design a tool that allows users to explore how the shape of an asteroid affects the appearance of its light curve.

從地球上來看，特洛伊小行星似乎是小光點，它們的光變曲線（一種隨著時間觀察星體亮度的方法）是一種讓科學家能夠確認遙遠天體形狀的線索。你的挑戰是要設計一種工具，讓使用者能夠去探索小行星的形狀，是如何影響其外觀的光變曲線。

## Details 詳細描述
### Background 背景說明
> This fall the NASA Lucy Mission will begin its 12-year journey to investigate a record-breaking eight asteroids in the first-ever mission to the Trojan asteroids—a population of small bodies that lead and follow Jupiter in its orbit around the Sun. Many asteroids (especially small ones) have interesting, irregular shapes. But as these asteroids are both small (less than 100 miles or 160 km wide) and very far away (hundreds of millions of miles or kilometers) they appear as unresolved points of light, even when viewed using our largest Earth-based and Earth-orbiting telescopes. Consequently, we won't know for sure what these asteroids look like until the Lucy spacecraft flies by these enigmatic bodies in 2027-2033. However, that won't stop us from working to collect as many clues as possible about these bodies today, from here on Earth.
> 
> One of the few ways scientists can try to estimate an asteroid's shape from an extreme distance is by looking at its light curve—i.e., examining how bright the asteroid is and how that brightness changes with time. As an irregularly shaped asteroid spins, the amount of light it reflects changes. If you watch an asteroid long enough, the brightness changes repeat, and that repeating light curve can help scientists determine its rotation speed and its shape. And if you watch the asteroid even longer, the light curve can change as the Earth and asteroid orbit around the Sun, revealing how the asteroid is oriented in space.
> 
> However, the relationship of a light curve to the asteroid shape is not necessarily unique. Asteroids of different shapes could generate indistinguishable light curves.

今年秋天，美國太空總署露西任務將開始其為期12年的旅程，在首次對特洛伊小行星的任務中調查破紀錄的八顆小行星——特洛伊小行星是一群在木星圍繞太陽的軌道上，引導和跟隨木星的小天體。許多小行星（尤其越小的）會有有趣的不規則形狀。但由於這些小行星既小（不到100英里或160公里寬）又很遠（數億英里或公里），即使使用我們在地球上且在運行軌道中最大的望遠鏡，它們看起來像是未解析的光點，因此，在2027-2033年露西太空船飛過這些神秘天體之前，我們無法確定這些小行星的樣子。然而，這不會阻止我們從地球上盡可能多收集關於這些天體的線索。

科學家可以嘗試從極遠距離估計小行星形狀，其中一種方法是觀察它的光變曲線——即檢查小行星的亮度以及亮度如何隨時間變化。當一顆形狀不規則的小行星旋轉時，它反射的光量會發生變化。如果你觀察小行星的時間夠長，亮度會重複變化，而重複的光變曲線可以幫助科學家確定其旋轉速度和形狀。如果你觀察小行星的時間更長，光變曲線會隨著地球和小行星圍繞太陽運行而發生變化，透露小行星在太空中的方向。

然而，光變曲線與小行星形狀的關係不一定是唯一的。不同形狀的小行星可以產生難以區分的光變曲線。

### Objectives 目標
> Your challenge is to develop a tool that allows users to explore how the shape of an asteroid affects the appearance of its light curve.
> 
> Note that many celestial objects have light curves; as you are researching this topic you may come across discussions of light curves of binary stars, transiting exoplanets, and other stellar objects like supernovae. This challenge focuses on the (visible) light curves of asteroids that are illuminated by reflected sunlight—not on self-luminous objects.

你的挑戰是要設計一種工具，讓使用者能夠去探索小行星的形狀，是如何影響其外觀的光變曲線。

請注意，許多天體都有光變曲線；在你研究這個主題時，你可能會遇到關於雙星、過境的系外行星和其他恆星物體（如超新星）光變曲線的討論。這項挑戰的重點是被反射陽光照射的小行星的（可見）光變曲線，而不是自發光天體。

### Potential Considerations 潛在考量
> As you develop your tool, you may (but are not required to) consider the following:
> - Some useful definitions:
> - Light Curve - A graph that shows the brightness of an object over a period of time
> - Shape Model - A 3D model of an object (like an asteroid)
> - Rotational Phase – A number (from zero to one) representing the angle in a periodic pattern
> - There are a number of properties that affect the appearance of a light curve including the rotation rate and axis of rotation, shape, surface texture, and variations in surface reflectance (albedo). You likely only want to consider a few of these as variables.
> - There are numerous online programs (including both proprietary and open source) that render 3D shape models and allow you to illuminate the objects with a defined light source. Potential search terms include: 3D modeling, 3D rendering, and ray tracing.
> - One way to turn a resolved image of a 3D model into a point for a light curve is to render a resolved image and then add up the brightness of the pixels in the image; just make sure that you only illuminate the 3D object from a single direction (sometimes called a "Sun" light) without ambient light (i.e., on a black background).
> - A matte (Lambertian) reflectance is a fine assumption for the surface of the asteroids. If you want to use a more complex model, see the papers in the example resources.
> - If you are not familiar with 3D modeling software, you can also generate light curves in the real world with an object, a light source, and a camera!
> - You might start by examining the light curves of simple ellipsoids (a sphere has a rather dull light curve) then explore what happens with the more complex shapes of real or imagined asteroids.
> - While the main focus is asteroids, feel free to have fun with the concept. For example, your tool could allow users to upload their own 3D model of a teapot and see what that light curve would look like!
> - As it is often impossible to observe an asteroid continually over a single rotation, scientists take advantage of the fact that asteroid light curves often repeat themselves each rotation. By using this repetition they can "fold" the data and plot it as a function of the rotational phase instead of time. However, as the seasons change on the body the light curve may change.
> - To take this challenge to the next level, you could make a tool that allows users to modify the shape of an object or add brightness variations to the object’s surface to make it match an existing light curve.
> - Potential keywords you can search include: 3D asteroid models, asteroid light curve databases, asteroid light curve photometry database.

在開發工具時，你可以（但不是必須）考慮以下事項：
* 一些有用的定義:
* 光度曲線 - 顯示物體在一段時間內的亮度的圖表
* 形狀模型 - 物體的3D模型（如小行星）
* 自轉相位—一個數字（從 0 到 1）代表週期性模式中的角度
* 有許多屬性會影響光變曲線的外觀，包括自轉速率和旋轉軸、形狀、表面紋質地以及表面反射率（反照率）的變化。你可能只想將其中的一些視為變量。
* 有許多線上程式（包括專有和開放原始碼）可以做3D形狀模型，並允許你使用定義的光源照亮對象。潛在搜索詞包括：3D建模、3D製作和光線追蹤。
* 將3D模型的解析圖像轉換為光變曲線點的一種方法是繪製解析圖像，然後將圖像中像素的亮度相加。只要確保你在沒有環境光下（即在黑色背景上），並從單一方向（有時稱為“太陽”光）照亮 3D物體。
* 無光澤（朗伯）反射率是小行星表面的一個很好的假設。如果你想使用更複雜的模型，請參閱範例資源中的論文。
* 如果你不熟悉3D建模軟體，你也可以使用一個物體、一個光源和一個相機在現實世界中生成光變曲線！
* 你可以先從檢查簡單橢圓體的光變曲線(球體的光變曲線相當暗淡)開始，然後探索真實或想像的小行星的更複雜形狀會發生什麼。
* 雖然主要重點是小行星，但請自由享受這個概念的樂趣。例如，你的工具可以允許用戶上傳他們自己的茶壺3D模型並查看光變曲線會是什麼樣子！
* 由於通常不可能在單次自轉中持續觀察小行星，科學家利用了小行星光變曲線在每次自轉中經常重複這一事實。通過利用這種重複，他們可以“折疊”數據並將其繪製為自轉相位而不是時間。但是，隨著天星體的季節變化，光變曲線可能會發生變化。
* 要將這一挑戰提升到一個新的水平，你可以製作一個工具，允許用戶修改物體的形狀，或為物體的表面添加亮度變化，使其與現有的光變曲線相匹配。
* 你可以搜索的潛在關鍵詞包括：3D小行星模型、小行星光變曲線數據庫、小行星光變曲線測光數據庫。

# Resources 相關資源
> <https://2021.spaceappschallenge.org/challenges/statements/when-light-curves-throw-us-curve-balls/resources>

