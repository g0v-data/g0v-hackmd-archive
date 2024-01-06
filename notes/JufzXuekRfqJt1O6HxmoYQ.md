---
title: "大型社群活動發送通知信注意事項"
tags: hackpad
---

# 大型社群活動發送通知信注意事項

> [點此觀看原始內容](https://g0v.hackpad.tw/I6MfE6jHOsq)



### 流程

- 確認信件範本內容
- 使用現成發信平台 or 自幹發信程式 + API
        - 確認是否符合「地雷區」提出問題，並解決
- 試發 mail
- dump KKTIX 報名資訊
- 寄發

### 地雷區

    - 編碼問題
        - mail header should be encoding in base64
        - utf-8 content
    - 特殊字元被退信或標為 spam  ☞ ⓘ
    - 重複寄信狀況：
        - google 會把重複內容隱藏
        - 要改標題，否則會跟前信 group 起來

### 現成發信平台

- mandrill [https://mandrill.com/](https://mandrill.com/)
    - ex: COSCUP2014
        - 會加上 tracking image 追蹤開信與否
        - 自幹簡單範例 [https://github.com/CrBoy/python-mailer-example](https://github.com/CrBoy/python-mailer-example)
- mailchimp [http://mailchimp.com/](http://mailchimp.com/)
- **AWS | Amazon Simple Email Service (SES)** [**http://aws.amazon.com/tw/ses/**](http://aws.amazon.com/tw/ses/)
    - ex: COSCUP 2013, g0v Summit 2014

### g0v 信件範本加 tag

- g0v Summit 2014 活動與票種複雜，通知信希望參與者只收到一封，所以加了兩個變數以條件方式嵌入（有Conference, Unconference, 晚宴等組合）
    - 範本模組 \- \> 一般行前通知、晚宴通知、Unconference 通知
    - 會眾：一般行前通知
    - VIP：一般行前通知 + Unconference 通知
    - 講者：一般行前通知 \+ 晚宴通知 \+ Unconference 通知

### \[註\] Library / 小工具

    - PHPMailer [https://github.com/PHPMailer/PHPMailer](https://github.com/PHPMailer/PHPMailer)
> PHPMailer 會加上他自己的 header，會在意的人要去改他 code 拿掉
> [name=CrBoy]

    - 小工具 [https://github.com/toomore/COSCUP2013Secretary-Toolkit](https://github.com/toomore/COSCUP2013Secretary-Toolkit)
- [https://www.phplist.com/](https://www.phplist.com/)
    - 許多正式上線的電子報系統都用這個，有許多進階功能，就是程式碼髒了些 ;)
    - ex: [http://epaper.ntu.edu.tw/](http://epaper.ntu.edu.tw/)



