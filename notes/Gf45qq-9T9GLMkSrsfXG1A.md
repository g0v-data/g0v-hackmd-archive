---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220617 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, mrorz, nonumpa
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

還沒空處理 [media-manager merge](https://github.com/cofacts/rumors-api/pull/284) 後的 migration⋯⋯

### :eye: Under review

- rumors-api: `articleReply` filter https://github.com/cofacts/rumors-api/pull/283
- Media manager [1](https://github.com/cofacts/media-manager/pull/1) [2](https://github.com/cofacts/media-manager/pull/2) [3](https://github.com/cofacts/media-manager/pull/3)
- rumors-db: https://github.com/cofacts/rumors-db/pull/59

## Media support
> https://github.com/orgs/cofacts/projects/9

- Need to migrate existing images on staging site
- Need to merge media-manager PRs and publish 0.1.0
    - Manually published [0.0.1](https://www.npmjs.com/package/@cofacts/media-manager) for [passing test on rumors-api](https://github.com/cofacts/rumors-api/pull/284)

## Trend and Contribution
> https://github.com/orgs/cofacts/projects/10

- Postponed: https://github.com/cofacts/rumors-api/issues/280

## 大松

- Good first issues on Websites
- Expertise: ReactJS, nextjs, react-apollo

For React developers 
https://github.com/cofacts/rumors-site/issues?q=is%3Aopen+is%3Aissue+label%3A%22good+first+issue%22

- [UX] 未登入使用特定功能時，請使用者登入 https://github.com/cofacts/rumors-site/issues/491
- [RWD 排版] 「我想補充」RWD 排版：https://github.com/cofacts/rumors-site/issues/425
- [Bug] "Add category" 按鈕點按後會送出分類，但須重新整理才會更新 UI: https://github.com/cofacts/rumors-site/issues/481
- [排版] 在關於 Cofacts 頁面插入 youtube video https://github.com/cofacts/rumors-site/issues/462

## Moderation discussion

### 已執行

- CIB https://github.com/cofacts/takedowns/pull/72
- 手機號碼露出 https://github.com/cofacts/takedowns/blob/master/2022/0617-privacy.md

### 「程秀蘭」LINE 看診詐騙

- 詐騙集團寄了一封 P 過的身分證截圖 (?????) 給 Cofacts 要求下架
- Cofacts 檢視文章，發現有詐騙集團 CIB 痕跡
    - https://cofacts.tw/article/1ljap64bbx6e4
    - https://cofacts.tw/article/354zu5u9gl4wr
    - https://cofacts.tw/article/1ncz4eisymvwo
- 打算不回信，但封鎖詐騙集團的 CIB

:::success
https://github.com/cofacts/takedowns/pull/74/files?short_path=cbe893b#diff-cbe893b351fb5a2ab8bbab0071d046a52fe628f6d30f82d88fa1d772a21117ab
:::

### 針對 Lopi 的檢舉

匿名檢舉者填寫的附註：

> 1.運用資料佐證區散佈爭議訊息及報導，刻意誤導視聽，及意圖加深政治類可疑訊息(或假訊息)真實性。(例如下列即時查核報告，引用黃國昌相關爭議指控，但可疑訊息原委為質疑政府調查境外可疑訊息動機，不僅文不對題，甚至意圖製造不實輿論風向誤導視聽)
>
> (1)	https://cofacts.g0v.tw/article/2br7f7v039jbi
> (2)	https://cofacts.g0v.tw/article/3liu0azhwddz2
>
> 2.同上，針對部份政治可疑訊息(大多為親統派立場文章及新聞報導)，意圖驗證訊息正確或協助操作輿論風向誤導視聽等行為，例如這篇文章源自PTT八卦版，但原始內容留言區大多散佈不實訊息(酸文及影響防疫威信言論)，並針對可疑訊息部份，引用特定新聞報導企圖誤導視聽。
> https://cofacts.g0v.tw/article/11vtuzdu9fbuj
> 
> 3.意圖驗證反疫苗文章為正確訊息(或個人意見，但意圖表達內容屬實)，即使事後台灣事實查核中心(經IFCN認證查核機構)查證為不實訊息。
>
> (1)	https://cofacts.g0v.tw/article/3bcxdjpl38wrq
> (2)	https://cofacts.g0v.tw/article/1dm8lhmw8u151
> (3)	https://cofacts.g0v.tw/article/2fj06675q1n9i
>
> 其中可疑訊息(3)，網友回報補充事項，疑似為該網友蓄意引導訊息，意圖誤導視聽影響查證結果。
>
> 本人曾在幾天前向貴網站工作小組成員回報，疑似發現有不肖份子利用即時查核網站驗證反疫苗文章為正確訊息、下不實查核結論誤導視聽及引用爭議(政治、疫情或疫苗)新聞報導充當查證來源，並意圖回報訊息屬實。假訊息傳播速度比一般廣播媒體傳播速度更快更廣，事實查核(包括IFCN認證查核網站或即時查核網站)應扮演提供民眾正確資訊，及防制假訊息之重大責任。如果不肖人士利用即時查核網站回報不實訊息為正確資訊，利用「用官方的資料或看起來圖文並茂專業資料來打擊官方的政策」，或運用佐證資訊投放爭議或不實訊息，藉此影響民眾配合防疫及施打新冠肺炎疫苗意願，不僅危害民眾生命健康，造成社會問題，甚至破壞查核公信力，希望貴網站應加以調查，如有違反查核規範及原則，應取消資格以示公信。

文中「前幾天」應是指 6/4 的檢舉，是針對[此回應](https://cofacts.tw/reply/olLkK4EBZ4FY5vnAM_Pd)，當時的檢舉附註為：

> 查核內容意圖誤導「政府採購快篩試劑不法」、「政府採購快篩試劑準確度不足」，及帶有政治色彩長臂審查。認為整體操作手法類似該案例(網址：https://tfc-taiwan.org.tw/articles/7065)，須請貴單位調查及確認相關目的。

當時回應為「不予處理」：
> 遭舉報的回應有針對原始訊息提供更多資訊，所提供英文資訊確實如回應中所述，是德國衛生主管機關用於評斷市面上快篩產品是否可補助的實驗資料。同樣接受此實驗的廠商台灣福爾（ http://www.foracare.com.tw/%E6%8A%97%E5%8E%9F%E5%BF%AB%E7%AF%A9/ ）也確實因為沒有通過此實驗而失去補助，不過由於當地市場對台灣快篩廠商來說不具吸引力，所以沒有要求進行複測。
> 
> 另外，檢舉人認為此訊息回應類似 https://tfc-taiwan.org.tw/articles/7065 （【烏俄戰爭】親俄造謠者新手法：發布假查核報告來嫁禍烏克蘭）之情事，該文係介紹親俄人士針對根本沒有在傳播的「假謠言」來發布查核報告的造謠手法。不過，Cofacts 真的假的的謠言搜集來源為 Cofacts LINE bot，該文在 2022/6/4 回應前，已經在 LINE 上流傳多時才被回應，故此情事與親俄造謠者的樣態並沒有相似之處。
>
> 綜合以上，Cofacts WG 認為此回應與原訊息有關、有附上合理參考資料，並且針對參考資料，也沒有錯誤的解讀，並無「侮辱、毀謗、散佈不實資訊」，也沒有其他違反 Cofacts 真的假的網站使用者條款之情事。如果檢舉人認為現有回應在推論上不夠精確，可以針對原始訊息回一則新的回應。

- 是 NF 嗎？[name=bil]
  - 我猜是，語氣很像 [name=mrorz]
- 他們會互相按 downvote，但不至於會用回應吵架 [name=mrorz]
  - 一開始好像有用回應回回應，但後來就沒有了 [name=mrorz]
  - 是正確的用法 [name=bil]
  - 有不同立場的人是好事 [name=mrorz]

:::success
- 應該還是會不予處理，因為只是意見不同，但都有附出處，沒有到造謠 [name=mrorz]
- 針對檢舉內容回應 [name=mrorz]
:::

### ＨＣＲ 腦控

https://cofacts.tw/reply/fVMaXIEBZ4FY5vnAxSmd

2022/3/24, 25 已被檢舉一次，當時判定：
> 遭檢舉內容確實屬於陰謀論範疇。不過，此回應內容與原始訊息尚能呼應，經會議討論（https://g0v.hackmd.io/bTVlJ8yYRb2nfDmGz09Psg#%E8%85%A6%E6%8E%A7%E6%B4%97%E7%89%88 ）後決議先擱置觀察，讓外界以現行 upvote / downvote 機制，合理評價此等回應。若爾後此等回應擴散至其他無關訊息，再行封鎖。

此次的檢舉附註為
> 意圖查證偽科學理論，刻意扭曲為正確訊息，誤導民眾視聽。這是即時查核網站，應提供民眾正確資訊，製造假查核報告不僅誤導大眾，甚至危害事實查核公信力，應予以停權。


- 當時是認為放著就不會繼續回，結果一直回 [name=bil]
  - 移到社團討論 [name=bil]
  - 問大家怎麼回應好 [name=mrorz]
  - https://www.youtube.com/watch?v=UPkaB8YvD9k [name=mrorz]
    - 陰謀論者可能還真的比 default skeptism 的人懂一些偏門的歷史事件
    - 但有幾個歷史案件不代表它可以合理運作
    - 由於陰謀論的不可證否性，哲學家也認為很難理性的與陰謀論者溝通
- 回應的範圍還是那幾篇文，沒有擴散到其他文章，也沒人在查這些文章，就是一個人在唱獨角戲 [name=mrorz]
  - 會覺得花時間在他身上有點不值 [name=mrorz]

:::success
移至社團討論
:::

## Google 停用帳號與文件

- Thanks to Stimim for help
- No updates from accounts team
