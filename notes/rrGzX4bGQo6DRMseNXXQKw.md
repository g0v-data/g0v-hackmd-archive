---
title: "情境網頁遊戲框架"
tags: hackpad
---

# 情境網頁遊戲框架

> [點此觀看原始內容](https://g0v.hackpad.tw/J84agQVmxG7)


這是一個情境式網頁遊戲的框架，只要把圖片放置好、把遊戲架構json寫好，放到網頁裡，就可以成為一個全新的情境式遊戲，或是心理測驗！

> 看起來很適合用 [http://twinery.org/](http://twinery.org/) 做，想要的功能都有
> [name=Poga P]

> [http://renpy.org/](http://renpy.org/)
> [name=雨蒼 林]

> [http://www.nvlmaker.net/](http://www.nvlmaker.net/)
> [name=雨蒼 林]

> 有企劃的話可以幫忙填 code 的部份 (一個留名佔坑的概念)
> [name=lanfon]



## 設定檔格式


- steps:
    - 過程，其中的"start"項目為第一張
    - bg:
        - 背景圖片
        - 範例："images/xxx.jpg"
> 如果settings的bg有指定，這裡可省略，將會使用settings的bg作為背景圖片
> [name=雨蒼 林]

    - characters
        - 角色圖片
        - 範例：\["images/xxx.png", "images/yyy.png"\]
    - place:
        - 地點（可省略）
        - "高雄市美麗島站"
    - datetime:
        - 時間（可省略）
        - 2015年8月17日 10:30
    - animate:
        - 轉場動畫
        - "fading" or "fliping"....
    - next:
        - 下一張
        - \["steps", "1"\]
> 如果沒有question，就跳next，沒有next，就跳results進行計算
> [name=雨蒼 林]

> 如果有多個內容，則亂數選一個。
> [name=雨蒼 林]

    - talks:
        - 說的話
        - \["first sentent", "second"\]
    - question:
        - 要問的問題
        - \["你要去哪裡？"\]
    - answer_type:
        - 答案格式
        - "radio" or "checkbox"
> 答案格式是radio的時候，點答案就直接進去了；
> [name=雨蒼 林]

> 如果答案格式是checkbox，要多一個確認的對話框給玩家點擊
> [name=雨蒼 林]

    - answers:
        - 答案選項，下面還會拆分
        -   \[answer: "", score: \["a": \[3, "plus"\], "b": \[5, "times"\]\], next: \["steps", "1"\]\]
            - answer
                - 答案內容
                - "我要去黑客松"
            - score
                - 計分方式
                - \[\["a", "+", 3\], \["b" "*", 5\]\]
> 以這邊為例，a + 3, b * 5
> [name=雨蒼 林]

> 這邊分數可以有多個，分開計算，計算模式看後面的plus、times
> [name=雨蒼 林]

            - next
                - 下一個要跳哪個選項
                -  \["steps", "1"\]
> 意思是跳到 steps 的第"1"項
> [name=雨蒼 林]

> next如果只有\["results"\]，則透過計算決定要顯示哪個結果。
> [name=雨蒼 林]

> 如果有指定，如\["results", "1"\]，不計算直接顯示該結果。
> [name=雨蒼 林]


- results:
    - 結果群組的呈現
    - calculate:
        - 計算方法，符合的才呈現
        - \[\[ "a", ">", 3 , "and" \], \[ "b", ">", 5 , "or" \]\]
> 必須符合 a > 3 或 b > 5才會呈現此結果
> [name=雨蒼 林]

> 根據計算結果來呈現答案。如果是在next中直接指定，則不用計算。
> [name=雨蒼 林]

    - title
        - 標題
        - "要去黑客松"
    - contents:
        - 呈現內容
        - \["result string", "result string"\]
        - 可以有多個
    - next:
        - 如果結果呈現後還要繼續問，可以放入next
        - \["steps", "1"\]

- settings
    - 遊戲的設定
    - cover
        - 一開始畫面的封面
    - bg
        - 遊戲預設場景的圖片
    - website
        - 遊戲相關網站
    - version
        - 本遊戲版本
    - code
        - 程式碼放哪裡
    - license
        - 網站授權
    - score
        - 設定預設分數

## 網頁格式與設定檔對照


### 遊戲進入的樣式

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_fbad11f47ecc525d459b069a1ab15cad)

### 對話狀況


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_35ce4e7baeadbabeb24ab3212e97fba8)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_32f20a40209dd170fe2eb6ad34bc37fb)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_bd235cf0360aa005597fdfdeaae17630)

### 提出問題


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a5f92fb640f913088c14db6f8438fbc9)

### 結果


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_489599c602b485bc91fa2b209468d599)

## 設定檔範例


這個設定檔，以CC授權小幫手為基底製作

```
{
  "settings": {
    "bg": "images/123.jpg",
 "website": "http://g0v.tw",
    "cover": "images/123.jpg",
 "code": "http://github.com/g0v.tw/1234.jpg",
    "license": "MIT"
    "score": [
      ["by", "=", 0],
      ["sa", "=", 0],
      ["nc", "=", 0],
      ["nd", "=", 0],
    ],
    "version": "0.01"
  }
  "steps": {
    "start": {
   "characters": ["images/aaa.png", "images/bbb.png"],
      "talks": [
        "不知道該如何選擇CC授權嗎？",
        "來選擇你的想像，再來看看要用哪個授權吧！"
      ],
      "next": ["steps", "by"]
    },
    "by": {
      "questions": [
        "需要標示姓名嗎？"
      ],
      "answers": [{
        "answer": "我要標示姓名",
        "score": [
          ["sa", "=", 1]
        ],
        "next": ["steps", "nd"]
      }, {
        "answer": "不用標示姓名",
        "score": [
          ["sa", "=", 0]
        ],
        "next": ["results"]
      }]
    },
    "nd": {
      "questions": [
        "別人可以改作嗎？"
      ],
      "answers": [{
        "answer": "可以改作",
        "score": [
          ["nd", "=", 1]
        ],
        "next": ["steps", "sa"]
      }, {
        "answer": "不能改作",
        "score": [
          ["nd", "=", 0]
        ],
        "next": ["steps", "sa"]
      }]
    },
    "sa": {
      "questions": [
        "分享後要用同樣授權嗎？"
      ],
      "answers": [{
        "answer": "要用同樣授權",
        "score": [
          ["sa", "=", 1]
        ],
        "next": ["steps", "nc"]
      }, {
        "answer": "不用使用相同授權",
        "score": [
          ["sa", "=", 0]
        ],
        "next": ["steps", "nc"]
      }]
    },
    "nc": {
      "questions": [
        "是否可以商業使用？"
      ],
      "answers": [{
        "answer": "可以商業使用",
        "score": [
          ["nc", "=", 1]
        ],
        "next": ["results"]
      }, {
        "answer": "不能商業使用",
        "score": [
          ["nc", "=", 0]
        ],
        "next": ["results"]
      }]
    }
  },
  "results": {
    "no-cc": {
      "calculate": [
        ["sa", "!=", 1, "and"]
      ],
      "title": "你不適用CC授權",
      "contents": [
        "您選擇了不做姓名標示。",
        "所以CC授權不適合你喔！"
      ]
    },
    "cc-by": {
      "calculate": [
        ["by", "==", 1, "and"],
        ["nc", "==", 0, "and"],
        ["nd", "==", 0, "and"],
        ["sa", "==", 0, "and"]
      ],
      "title": "CC-BY適合你！",
      "contents": [
        "因為你沒有做太多限制。",
        "CC-BY授權適合你喔！"
      ]
    },
    "cc-by-nc": {
      "calculate": [
        ["by", "==", 1, "and"],
        ["nc", "==", 1, "and"],
        ["nd", "==", 0, "and"],
        ["sa", "==", 0, "and"]
      ],
      "title": "CC-BY-NC適合你！",
      "contents": [
        "因為你只有加上商業限制。",
        "CC-BY-NC授權適合你喔！"
      ]
    },
    "cc-by-nc-sa": {
      "calculate": [
        ["by", "==", 1, "and"],
        ["nc", "==", 1, "and"],
        ["nd", "==", 0, "and"],
        ["sa", "==", 1, "and"]
      ],
      "title": "CC-BY-NC-SA適合你！",
      "contents": [
        "因為你限制商業使用，又要求修改後要以相同授權釋出。",
        "CC-BY-NC-SA授權適合你喔！"
      ]
    },
    "cc-by-nd": {
      "calculate": [
        ["by", "==", 1, "and"],
        ["nc", "==", 0, "and"],
        ["nd", "==", 1, "and"],
        ["sa", "==", 0, "and"]
      ],
      "title": "CC-BY適合你！",
      "contents": [
        "因為你禁止別人改作。",
        "所以CC-BY-ND授權適合你喔！"
      ]
    },
    "cc-by-nc-nd": {
      "calculate": [
        ["by", "==", 1, "and"],
        ["nc", "==", 1, "and"],
        ["nd", "==", 1, "and"],
        ["sa", "==", 0, "and"]
      ],
      "title": "CC-BY-NC-ND適合你！",
      "contents": [
        "你限制了商業授權，也禁止改作。",
        "所以CC-BY-NC-ND授權適合你喔！"
      ]
    },
    "cc-by-sa": {
      "calculate": [
        ["by", "==", 1, "and"],
        ["nc", "==", 0, "and"],
        ["nd", "==", 0, "and"],
        ["sa", "==", 1, "and"]
      ],
      "title": "CC-BY-SA適合你！",
      "contents": [
        "因為你只要求要用相同方式分享",
        "所以CC-BY-SA授權適合你喔！"
      ]
    }
  }
}


```
## 操作方法


可以用滑鼠點擊，也可以用右、Enter、空白選下一步；
上下左右可以在選項中跳躍，enter、空白選擇

## 適用場合

憲動盟議題推廣
CC授權選擇
各種議題介紹

## 這個坑需要


- [ ] 網頁設計師
- [ ] UI設計師
- [ ] 對議題有興趣、有劇本的朋友
```
 請問可以環境議題加入嗎？

