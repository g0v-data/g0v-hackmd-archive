---
title: "法規正規化 (Law Formalization) 2.0"
tags: hackpad
---

# 法規正規化 (Law Formalization) 2.0

> [點此觀看原始內容](https://g0v.hackpad.tw/L7laAVrpoF6)


## 來由

[https://github.com/g0v/laweasyread-data](https://github.com/g0v/laweasyread-data)
[https://github.com/g0v/twlaw](https://github.com/g0v/twlaw)
年久失修，需要統整各種 parser 與規劃統一的法條機讀格式。

現在的正規化 toolchain:
TWLaw (HTML) -> (JSON) -> (Git) -> TW-Law-Corpus (Markdown)
TWLaw (HTML) -> LawEasyRead-Data (JSON) -> LawEasyRead (MongoDB)

立法院法律系統與全國法規資料庫不一致。

## 考量

扁平／組織
分條分項／增修／Metadata
~盡可能不要XML~

## 暫時提案

擬似 Markdown 的人讀格式，有嚴謹的 spec：
```
《提審法》

1935-06-21: 中華民國二十四年六月二十一日國民政府制定公布全文 11 條；並自三十五年三月十五日起施行
1948-04-26: 中華民國三十七年四月二十六日國民政府修正公布全文 10 條
1999-12-15: 中華民國八十八年十二月十五日總統（88）華總（一）義字第 8800299070 號令修正公布第 1、3、4、6、9 條條文
2014-01-08: 中華民國一百零三年一月八日總統華總一義字第 10300000651 號令修正公布全文 12 條；並自公布後六個月施行

第一條 (提審之聲請)
　　人民被法院以外之任何機關逮捕、拘禁時，其本人或他人得向逮捕、拘禁地之地方法院聲請提審。但其他法律規定得聲請即時由法院審查者，依其規定。
　　前項聲請及第十條之抗告，免徵費用。

```
或是充滿 metadata 的 JSON 格式。

## 參考資料

USLM: [http://uscode.house.gov/download/resources/USLM-User-Guide.pdf](http://uscode.house.gov/download/resources/USLM-User-Guide.pdf)


