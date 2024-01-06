### 均一2022AW Python Basic
### 2022/11/30作業練習
---
作業繳交例
完成後請到右上角加入分隔線🙂
程式碼貼上後反白點選上方"</>"符號，在"```"符號後輸入python=
```python=
# Aaron 11/23
print("Hello World")
```
---
```
題目一

某停車場停車一小時50元，未滿一小時收25元
當日停車費最高收300元。
請設計一個程式，告知使用者總共需付多少錢
輸入: 輸入停車時間
輸出: 金額
備註: 不需計算至隔日。
```
```python=
# Rolly 12/05
time = int(input())

if time < 1:
    print("25")
if time >= 1 and time <= 6:
    print(time * 50)
if time > 6:
    print("300")

```
```
題目二

輸入分數後，做出分數區間表(90分以上、80分以上、70分以上、60分以上、以及 不及格 的判斷)
1.數入介於0~100的整數
2.print出該分數對應之結果(90分以上、80分以上、70分以上、60分以上、以及 不及格 的判斷
(ex.93分 屬於 “90分以上”，且不屬於其他結果)
```
```python=
# Rolly 12/05
print("請輸入成績:")
score = int(input())

if score > 90:
    print("90分以上")
elif score > 80:
    print("80分以上")
elif score >70:
    print("60分以上")
else:
    print("不及格")
```
---
