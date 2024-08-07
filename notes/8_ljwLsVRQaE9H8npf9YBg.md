---
title: "部件樣態:分析與測試"
tags: 萌典,moedict,hackpad
---

# 部件樣態:分析與測試

> [點此觀看原始內容](https://g0v.hackpad.tw/hT0D4mUgg2a)


- 源自零時字引([簡報](https://docs.google.com/presentation/d/16MzEnhGiWYH2e5WMudW6Sc49BTWDf1_aicbFMU9nSrU/edit#slide=id.ga3b6a90a6_1_20))與個人心理學研究心得
- 從必學的基礎中文字歸納的部件樣態(外形,結構,位置)，能否應付現代中文的組字需求?
- 台灣教學學者建立的中文字部件資料庫與分析研究
    - Cool Chinese[漢字、部件五項線上查詢平台](http://140.122.109.78/COOL/2011/)
    - 部件結構與分析報告: 陳學志*、張瓅勻、邱郁秀、宋曜廷、張國恩（2011）。中文部件組字與形構資料庫之建立及其在識字教學上之應用。**教育心理學報，43卷**，閱讀專刊，269-290。
    - 必學的中文字有6,097字(對照簡體字5,793字)，包含在[IDS-Basic](http://git.chise.org/gitweb/?p=chise/ids.git;a=blob_plain;f=IDS-UCS-Basic.txt;hb=HEAD)之內
    - IDS 字形結構([from wiki](https://en.wikipedia.org/wiki/Chinese_character_description_languages)) vs. Cool Chinese 字形結構(from paper)
    -
| 碼號 | 字符 | 意義 | 例字 | 範例 |
| --- | --- | --- | --- | --- |
| 2FF0 | ⿰ | 兩個部件由左至右組成 | 相 | ⿰木目 |
| 2FF1 | ⿱ | 兩個部件由上至下組成 | 志 | ⿱士心 |
| 2FF2 | ⿲ | 三個部件由左至右組成 | 湘 | ⿲氵木目 |
| 2FF3 | ⿳ | 三個部件由上至下組成 | 糞 | ⿳米田共 |
| 2FF4 | ⿴ | 兩個部件由外而內組成 | 回 | ⿴囗口 |
| 2FF5 | ⿵ | 三面包圍，下方開口 | 冋 | ⿵冂口 |
| 2FF6 | ⿶ | 三面包圍，上方開口 | 凶 | ⿶凵㐅 |
| 2FF7 | ⿷ | 三面包圍，右方開口 | 叵 | ⿷匚口 |
| 2FF8 | ⿸ | 兩面包圍，兩個部件由左上至右下組成 | 病 | ⿸疒丙 |
| 2FF9 | ⿹ | 兩面包圍，兩個部件由左下至右上組成 | 戴 | ⿹⦏異 |
| 2FFA | ⿺ | 兩面包圍，兩個部件由右上至左下組成 | 起 | ⿺走巳 |
| 2FFB | ⿻ | 兩個部件重疊 | 巫 | ⿻工从 |
| 結構關係 | 代表符號 | 示例 |
| --- | --- | --- |
| 單獨存在 | X | 木 = X、阜 = X、內 = X |
| 垂直組合 | - | 貢 ＝ -（工，貝） |
| 水平組合 | | | 烤 ＝ |（火，考） |
| 封閉包圍 | 0 | 困 ＝ 0（囗，木） |
| 左上包圍 | / | 仄 ＝ /（厂，人） |
| 右上包圍 | \ | 或 ＝ \\（戈，-（口，一）） |
| 左下包圍 | L | 超 ＝ L（走，-（刀,口）） |
| 上方三面包圍 | ^ | 凰 ＝ ^（几，-（白,王）） |
| 下方三面包圍 | V | 凶 ＝ V（凵，乂） |
| 左方三面包圍 | < | 匪 ＝ <（匚，非） |
| 左右夾擊 | T | 夾 ＝ T（大，人，人） |
- 還需要進行的資料處理
1.  IDS資料的處理
    \* 只有特殊序號的部件中文字(&...;) => 查找可對應的實際字符 =\> 沒有者以簡易編碼代替
2.結構差異的字條分析
    \* 比較結構分類不同的字條之結構分類差異
    \* 比較結構分類不同的字條之部件分析差異
3.結構相同的字條分析
    \* 結構分類相同的字條，比較部件分析差異

4.決定部件樣態:
    \* 從結構相同的字條，歸納經過前三步驟，透過以下分析程序所得到的部件樣態
第一層結構 -> 可分析部件位置(?) -> 第二層結構 -> 可分析部件位置 (?) -> ... -\> 第n層結構 -> 可分析部件 位置(無) end

ex1. 佶: 第一層⿰ -> 可分析部件 (右) -> 第二層⿱ ->  可分析部件(無)
ex2. 蛇: 第一層⿰ -> 可分析部件 (右) -> 第二層⿱ ->  可分析部件(無)

    \* 範圍內字條經過以上程序，得到構成部件的部件樣態資訊。部件樣態必須包含外形、結構與位置資訊。

5.部件樣態定義與測試
    \* 單一部件，統計結構+位置的樣態
    e.g., "心"在"態","心" 在 "愛","心" 在 "沁"分為三種樣態
    e.g., "宀"在"安","宀"在"實","宀"在"蛇"分為三種樣態
Validation Test
    \* 測試樣本:IDS-Basic 6,097字之外的字條
```
              非Basic的字集
```
    \* 測試方法: (1)從測試樣本隨機抽樣一定規模的字條
```
               (2)可用部件樣態成功組字的字條比例

