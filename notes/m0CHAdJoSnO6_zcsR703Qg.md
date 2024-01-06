# opencv_D01-D05(1/3讀書會)
講義跟作業連結：https://drive.google.com/open?id=1enpPAko-dountF_vou_5ZVShoqiYyCRT

#### [TOC]
---

## * Day1 - OpenCV基礎
  把圖片用三原色呈現，一樣是3個維度，(0,0,255)、(0,255,0)、(255,0,0)


### 顯示圖片
```python
cv2.imshow('My Image', img)
```

### 按下任意鍵則關閉所有視窗
```python
cv2.waitKey(0) #等待時間
cv2.destroyAllWindows() #關閉視窗
```
這裡 cv2.waitKey 函數是用來等待與讀取使用者按下的按鍵，而其參數是等待時間（單位為毫秒），若設定為 0 就表示持續等待至使用者按下按鍵為止，這樣當我們按下任意按鍵之後，就會呼叫 cv2.destroyAllWindows 關閉所有 OpenCV 的視窗。

### 讓視窗可以自由縮放大小
在預設的狀況下，以 cv2.imshow 所開啟的視窗會依據圖片來自動調整大小，但若是圖片太大、佔滿整個螢幕時，我們會希望可以自由縮放視窗的大小，這時候就可以使用 cv2.namedWindow 將視窗設定為 cv2.WINDOW_NORMAL：
```python
cv2.namedWindow('My Image', cv2.WINDOW_NORMAL)
cv2.imshow('My Image', img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
### 輸出圖檔
cv2.imwrite 可透過圖片的副檔名來指定輸出的圖檔格式：
```python
cv2.imwrite('output.jpg', img)
cv2.imwrite('output.png', img)
cv2.imwrite('output.tiff', img)

# 設定 JPEG 圖片品質90（可用值0~100）
cv2.imwrite('output.jpg', img, [cv2.IMWRITE_JPEG_QUALITY, 90]) 

# 設定 PNG 壓縮層級為5（可用值為0~9）
cv2.imwrite('output.png', img, [cv2.IMWRITE_PNG_COMPRESSION, 5])
```

### 指定圖檔格式

OpenCV 的 `cv2.imread `在讀取圖片時，可以在第二個參數指定圖片的格式，可用的選項有三種：

* `cv2.IMREAD_COLOR` 此為預設值，這種格式會讀取 RGB 三個 channels 的彩色圖片，而忽略透明度的 channel。
* `cv2.IMREAD_GRAYSCALE` 以灰階的格式來讀取圖片。
* `cv2.IMREAD_UNCHANGED` 讀取圖片中所有的 channels，包含透明度的 channel。
```python
#以灰階的方式讀取圖檔
img_gray = cv2.imread('image.jpg', cv2.IMREAD_GRAYSCALE)
```
### 參考連結

> * 關於33提到的destroyAllWindows：https://blog.gtwang.org/programming/opencv-basic-image-read-and-write-tutorial/
---

## * Day2

### 直方圖均衡(equalizeHist)
假如是一般常見的 RGB 或是 BGR 對每個 channel 做 equalizeHist 比較像是色彩平衡

但是如果我們想樣針對明按度或是飽和度做平衡的話可以先轉適合的 color space 再對特定 channel 做 equalizeHist

* HW: 如何設定HSV/HSL/LAB的參數


---

## * Day3

### img_hls_down[..., -1]
```python
img_hls = cv2.cvtColor(img, cv2.COLOR_BGR2HLS)
img_hls_down = img_hls.astype('float32')
```
在 Python 的 list  或是矩陣裏面 -1 代表「最後一個」
在這邊我們知道 img_hls_down 是一個三維矩陣
前面兩個維度代表長跟寬，第3個維度在這邊分別是 H, L, S channel

所以 img_hls_down[..., -1] 這邊應該要看兩件事情

* [..., -1] 代表我們 -1 指的是「最後一個維度」的「最後一個 channel」
* img_hls_down[..., -1] 代表我們希望拿這個矩陣的 S channel (飽和度)

Note:「...」 的用法在 Day4 會有可以再看看

