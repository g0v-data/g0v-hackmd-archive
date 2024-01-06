# 網站筆記

## 官方網站
- 2023 coscup 已使用 vue3，資料可通 oPass
    - [coscup 2023 網站](https://github.com/COSCUP/2023)


## 徵件系統
- Kirby 贊助 grantdash v2 [name=kirby]
- 跟零時小學校架設在同一台 server
- SeanGau 負責前端 [name=SeanGau]
### 流程
1. 在 grantdash 徵件、提案討論
2. 在 grantdash 進行內部審查，確定要選得議程
3. 在？？？安排議程（目前暫定4軌）
4. 透過 api 轉成 oPass 和網站吃的 json 格式

---

> 首頁
> - 身為一個由多個工作小組共同維護的會議網站，我覺得可以拿 [2020 網站需求/使用者故事](https://g0v.hackmd.io/@ODrkl-1rScWpK6S1uQCQDw/g0v-summit-2020-marketing/%2FJPneelL6Snqa_1WnB4WT1g)當作討論的素材，像是：
>   -「你覺得裡面提到的八個使用者故事，可以用什麼方式達到？」
>   - 「針對這八個使用者故事，有什麼事可以合併，或是不需要的嗎？理由是什麼」
> - 2020 的實做：
>   - vue2/nuxt2 ，但因為 vue2 今年年底 EOL ，原則上 git repo 只能參考，不建議直接沿用
> - [後台倉儲與說明](https://g0v.hackmd.io/@ddio/summit-2020-articles/%2FSphmcJemS5CyIuwa1KtN2w)
> - [大會後的檢討](https://g0v.hackmd.io/@ODrkl-1rScWpK6S1uQCQDw/g0v-summit-2020-marketing/%2F13NummLcTSGMDaOqOBf4ZQ)
> - 徵件網站
>   - 我會建議直接拿小學校徵件網站來用，重造輪子痛苦指數有點高
>   
> [name=ddio]

> 資料要考慮用我們在用的上稿系統嗎？定義好 schema 就可以直接用
> https://github.com/mirror-media/Lilith
> 有人可以提供 GCP credit 的話，CI/CD 也可以直接串好
> 也可以直接生好 GQL 讓 FE 用
> 補充一下，這個權限可以根據不同的 roles 控制到 fields 權限
> 那我就只先提供可選擇方案，看有人需要我可以再幫忙解釋 www
> [name=hcchien]

> 補個極限情境！2020 時議程資料流是這樣：
>
> 徵件網站，是拿來讓投稿者該資料、補資料用的
> 議程組，可以從工人的後台，覆寫指定議程的指定欄位，像是（大多講者懶得填的）英語欄位
> 議程的場地、時間，一樣放在工人後台，這張表會持續更動到活動開始前一刻
> [name=ddio]

> 2020 原本有有打算用 jothon 版的 grantdash 但後來決定自己改一個比較快。要維議一個徵稿系統確實比較需要單獨的人力
> [name=pm5]

> COSCUP Pretalx 是由網站組協助維運自架的版本（今年度改用自架） @denny 看能否補充
> [name=yanyiyi]

> 正確，Pretalx 是 open source project 可以自架維護，COSCUP 是由 IU 在管理和維護
> https://github.com/pretalx
> [name=denny]
