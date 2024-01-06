---
tags: g0v-summit, 2020
---
# g0v Summit 2020 議程後台使用說明

本文件包含以下資訊：

- 給議程組：
  1. 議程上線前的代辦事項
  2. 如何填寫議程時間表
  3. 如何審核講者新修改的稿件
  4. 如何覆寫講者的議程
  5. 如何新增邀稿的議程
  6. 方便確認議程時間的方式
- 給主網站工程師：
  1. 如何使用議程資訊

## `議程組` - 議程上線前的代辦事項

議程正式上線前，請協助完成以下工作：

- [ ] 將負責審核稿件修改的帳號們，提供給 Howard 。（id or email）
    - [ ] brucelee: brucelee.ntu@gmail.com 
    - [ ] bobbyho: angela.bobby@gmail.com
- [ ] 9/11 前，取得 Airtable 權限，邀請連結請見 slack
- [ ] 填完 Airtable 上的[議程時間](https://airtable.com/tblPeDJPEOSlECfJI/viwNqVPw2XhqXbnWP?blocks=hide) ，讓宣傳組可以製作議程頁面

## `議程組` - 如何填寫議程時間表

議程組可在[此表](https://airtable.com/tblPeDJPEOSlECfJI/viwNqVPw2XhqXbnWP)編輯議程時間、分類說明、虛擬議程，例如開幕、午休等
- 分類主題、議程場地需要支援華英雙語，由半形 `,` 區隔
- 新增虛擬議程時，請一併提供英語標題
- 虛擬議程的 ID 隨意打，不要重複即可

## `議程組` - 如何審核講者新修改的稿件

1. 進入徵件網站，點選右上角的「審核更新」 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9933482081fb0cf8496551a6cc93ab49.png)
2. 頁面分為上下兩半，上半部為所有需要審核的更新，下半部則是其餘的入選議程 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f59806b8d5472fa7cb1ba20b31e1317c.png)
3. 點選議程的「詳細資訊」後，就可以看到
   - 變更的相關資訊
   - 是否通過審核
   - 作者（提交此稿件的帳號）的信箱

## `議程組` - 如何覆寫講者的議程

1. 查詢想要修改的稿件的 ID
   - 可以到[議程時間](https://airtable.com/tblPeDJPEOSlECfJI/viwNqVPw2XhqXbnWP?blocks=hide)搜尋
   - 或到[審核更新](https://propose.summit2020.g0v.tw/proposal-admin)頁面， ID 在每則稿件的右上角 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f59806b8d5472fa7cb1ba20b31e1317c.png)
3. 進入 Airtable 的[議程組覆寫專用表](https://airtable.com/tblG8Xxy36aRoP34U/viwSevNkqvMUsCCPs?blocks=hide)
4. 找到想要覆寫的稿件（以 ID 為準，因為稿件標題也是可以被覆寫的～）
5. 找到想要覆寫的欄位，填上新資料
   - 講者大頭照請先自行上傳到 imgur
   - 講者資訊是結構化資料，範例長這樣：
     ```yaml
     display_name: 外星人
     organization: 冥王星 中山路 36 號 2 弄 7 樓
     avatar_url: https://img.omdbapi.com/?i=tt0113497&h=600&apikey=b5ac9e3d
     city: 冥王星
     info_url: https://wikipedia.org
     bio: 在冥王星 中山路 36 號 2 弄 7 樓工作的外星人
     bio_en: ???
     ```
6. 台灣時間每天早上九點，機器人會將新的內容更新到 [staging](https://g0v.github.io/summit2020) 上，宣傳組會視情況手動更新到正式網站
   - 如果講者被審核的更動，比這邊的更動時間還要晚的話，會完全採用講者的更動
   - 反之，則會採用講者 + 這邊的所有非空白欄位的資料
8. 如果想要緊急更新，請在工人群組戳網站相關工人，例如 ddio, mango

## `議程組` - 如何新增邀稿的議程

1. 進入 Airtable 的[議程組覆寫專用](https://airtable.com/tblG8Xxy36aRoP34U/viwSevNkqvMUsCCPs?blocks=hide)
2. 新增一行，填入==所有==欄位資訊，講者至少一人
   - 講者大頭照請先自行上傳到 imgur
   - 講者資訊是結構化資料，範例長這樣：
     ```yaml
     display_name: 外星人
     organization: 冥王星 中山路 36 號 2 弄 7 樓
     avatar_url: https://img.omdbapi.com/?i=tt0113497&h=600&apikey=b5ac9e3d
     city: 冥王星
     info_url: https://wikipedia.org
     bio: 在冥王星 中山路 36 號 2 弄 7 樓工作的外星人
     bio_en: ???
     ```
4. 台灣時間每天早上九點，機器人會將新的內容更新到 [staging](https://g0v.github.io/summit2020) 上，宣傳組會視情況手動更新到正式網站
5. 如果想要緊急更新，請在工人群組戳網站相關工人，例如 ddio, mango

## `議程組` - 方便確認議程時間的方式

可以使用已經設定好的[這個表格](https://airtable.com/tblPeDJPEOSlECfJI/viwGCU7ftHTKbt6FL?blocks=hide)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_26971fae2a080a046ba1a442311e67da.png)


## `工程師` - 如何使用議程資訊

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0baf1a894fd2729a22e0f76eb89d6fc9.png)

由於議程的資料結構較複雜，目前僅提供以 ID 為索引的 map ，還沒有其他的資料結構。
- 目前的資料請見 [assets/proposals.json](https://github.com/g0v/summit2020/blob/master/assets/proposals.json)
- 資料結構說明，請見 [README.md](https://github.com/g0v/summit2020#%E7%A8%BF%E4%BB%B6%E8%B3%87%E6%96%99%E7%B5%90%E6%A7%8B)
- 待議程頁面設計確定後，可視情況增加用其他方式排序、整理的資料結構

範例程式可參考 [proposal-demo](https://g0v.github.io/summit2020/proposal_demo/)

或以下程式：

### Vue HTML
```html
  <div class="proposal mw8 center ph3 mv5">
    <div
      v-for="proposal in proposals"
      :key="proposal.id"
      class="br3 ba b--moon-gray mv3 pa3 flex-l items-between"
    >
      <div class="flex-auto">
        <h2 class="f4 b flex items-center">
          {{ proposal.title }}
          <span v-if="proposal.timeSheet.分類主題" class="f6 br2 bg-light-green ml2 lh-solid pv1 ph2 normal dark-green">
            {{ proposal.timeSheet.分類主題 }}
          </span>
        </h2>
        <p class="dark-gray">
          {{ proposal.summary }}
        </p>
      </div>
      <div class="pl3-l ml3-l bl-l b--moon-gray">
        <div>{{ proposal.timeSheet.議程場地 }}</div>
        <div class="gray">
          {{ proposal.timeSheet.議程開始時間 }}-{{ proposal.timeSheet.議程長度 }}
        </div>
      </div>
    </div>
  </div>
```

### Vue Javascript
```javascript
import moment from 'moment'

export default {
  data () {
    return {
      proposals: Object
        .values(this.$t('proposal/map'))
        .sort((l, r) => moment(l.timeSheet.議程開始時間) - moment(r.timeSheet.議程開始時間))
    }
  }
}
</script>
```


{%hackmd jfvbUuzyQtOVjnWUOW1peQ %}