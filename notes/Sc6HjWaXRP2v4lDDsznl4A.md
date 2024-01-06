---
tags: 逐字稿, 直播,
---

# audio loopback 基本的訪談逐字稿

https://g0v.hackmd.io/HBaW9cBhRo6qYbCZhvnHvg?view

## 做法搜集

- IBM Watson 批次語音轉文字網站：[https:/](https://speech-to-text-demo.mybluemix.net/)[Python SpeechRecognition 套件](https://speech-to-text-demo.mybluemix.net/)[/speech-to-text-demo.mybluemix.net/](https://speech-to-text-demo.mybluemix.net/)
> Watson 目前需要廣播節目等級的收音（硬體、空間）條件，才能達到「人工校正比重新打字快」。
> [name=Audrey T]

- Linux 系統 audio loopback：
    - [https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/Modules/](https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/Modules/#index63h3)[#index63h3](https://g0v.hackpad.tw/ep/search/?q=%23index63h3&via=y9IPMAkKfj2)
- Python 的 SpeechRecognition 套件
    - [https://youtu.be/31DZfkYRvI4](https://youtu.be/31DZfkYRvI4)

- https://g0v-tw.slack.com/archives/C02G2SXKX/p1543249498560600
- 使用OpenAI的Whisper API，幫4個小時的錄音產生逐字稿與時間軸字幕
- Macpaul Lin> it works! 透過一條音源線，把Speaker out put導到 MIC去，然後就可以一邊放youtube，然後另外一邊用Google語音辨識，讓電腦幫你作逐字稿！（Firefox x Chrome) 但是Google語音辨識速度明顯比人講話慢。猜測應該跟網路頻寬，以及計算能力有關。所以理論上，對於這種背景雜音乾淨的語音檔，可以接Google web 語音辨識的API，就能輕鬆做出基本的訪談逐字稿
    - [https://www.facebook.com/photo.php?fbid=10152824899882910&set=a.172718147909.122769.532627909&type=1&theater&notif\_t=comment\_mention](https://www.facebook.com/photo.php?fbid=10152824899882910&set=a.172718147909.122769.532627909&type=1&theater&notif_t=comment_mention)
    - 註記：
        - 視窗需要持續保持在 google doc 視窗上，無法進行其他使用
        - 仍會出現中斷情形，可能是該段落收音太弱
- Cloud Speech API is now generally available
    - [https://cloudplatform.googleblog.com/2017/04/Cloud-Speech-API-is-now-generally-available.html?m=1](https://cloudplatform.googleblog.com/2017/04/Cloud-Speech-API-is-now-generally-available.html?m=1)
- Scott Tsai> 自製做法 [https://www.facebook.com/700484037/posts/10153115500289038](https://www.facebook.com/700484037/posts/10153115500289038)
- 若只有一個音源孔
    - 買：有音效卡的 splitter
        - ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_67821bfa7f95847037a38d13291ed9c0)
- 透過複述，讓GOOGLE聽打
    - [https://bit.ly/2LdoXaT](https://bit.ly/2LdoXaT)
- https://www.facebook.com/95279542107/posts/10156670187772108?d=n&sfns=mo



## 辨識服務

- IBM Watson 批次語音轉文字網站
    - [https://speech-to-text-demo.mybluemix.net/](https://speech-to-text-demo.mybluemix.net/)
> Watson 目前需要廣播節目等級的收音（硬體、空間）條件，才能達到「人工校正比重新打字快」。
> [name=Audrey T]

- Google 語音辨識網頁
    - [https://www.google.com/intl/en/chrome/demos/speech.html](https://www.google.com/intl/en/chrome/demos/speech.html)
    - 運用 audio loopback 3-4 分鐘後，網頁會自動停止辨識？
    - 影片聲音導入 Google 翻譯 將語音轉成文字 [https://youtu.be/pdnwuZ6wMjM](https://youtu.be/pdnwuZ6wMjM)
- Google Docs 新增中文語音輸入功能
    - [http://www.playpcesor.com/2015/09/google-docs.html](http://www.playpcesor.com/2015/09/google-docs.html)
    - 影片聲音導入 Google Docs 翻譯 將語音轉成文字，操作說明影片
        - [https://youtu.be/trHHrXZye4Y](https://youtu.be/trHHrXZye4Y)
        - [https://youtu.be/b0uPpojHppU](https://youtu.be/b0uPpojHppU)
- Web Speech to Text 
    - https://www.playpcesor.com/2019/12/Web-Speech-to-Text.html
- Voice Dictation
    - [http://www.playpcesor.com/2018/01/voice-dictation.html](http://www.playpcesor.com/2018/01/voice-dictation.html)
- Speechnotes
    - [https://free.com.tw/speechnotes/?utm\_content=bufferc9a7a&utm\_medium=social&utm\_source=facebook.com&utm\_campaign=buffer](https://free.com.tw/speechnotes/?utm_content=bufferc9a7a&utm_medium=social&utm_source=facebook.com&utm_campaign=buffer)
- 讯飞听见网站 / 听见录音宝
    - [http://www.playpcesor.com/2017/11/podcast-to-txt-in-evernote.html](http://www.playpcesor.com/2017/11/podcast-to-txt-in-evernote.html)
    - [http://www.iflyrec.com/](http://www.iflyrec.com/)
- 搜狗
    - [http://dictation.sogou.com/](http://dictation.sogou.com/)
- Trint
    - [https://trint.com/](https://trint.com/)
- SwiftScribe
    - [https://www.inside.com.tw/2017/03/15/baidu-swiftscribe](https://www.inside.com.tw/2017/03/15/baidu-swiftscribe)
    - [https://swiftscribe.ai/](https://swiftscribe.ai/)
- Wrappup 聰明手機錄音 App：免費語音轉中文與自動聽寫筆記
    - [http://www.playpcesor.com/2017/10/wrappup-AI-Voice-Recorder-app.html](http://www.playpcesor.com/2017/10/wrappup-AI-Voice-Recorder-app.html)


- app https://www.facebook.com/groups/277170570759/permalink/10158048441330760/
- UD talk http://udtalk.jp/post-3463/
- ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9328b2a8cda6f36bad8683611c7130e4)
- https://www.facebook.com/story.php?story_fbid=pfbid0TwM7UGRSEeZgF6giwg4vVNqrbCM4ACoFg66ty4L7dM9wh8GdhQpT5iKDjqN273mQl&id=100063560691696&mibextid=tejx2t
- 語音檔案轉逐字稿工具 https://mygoodtape.com/


-  接逐字稿 case 的單位
    - [https://g0v.hackpad.tw/udPZVnSyCou#:h=逐字稿](https://g0v.hackpad.tw/udPZVnSyCou#:h=逐字稿)

- 工作坊，用筆電收音，轉成逐字稿 https://www.facebook.com/story.php?story_fbid=pfbid0rM6z6Qk7KNKJLj6vA3u5513m3FMnQgpBz4udKz9t2yiHGQnebWAqAc8XJY2E53bQl&id=100000313135685&mibextid=qC1gEa

## 其他

- 逐字稿品質
    - 若想要「直播」同時產出文字？
    - 收音效果是不是要夠好才能有較好的逐字稿品質？
- 是否可能結合視訊通話
- 關於「音源線」
- youtube 自動字幕功能？
- Mac｜自動會停止？
- Mac｜如果所選音訊裝置回覆為另一個音訊裝置｜如果您在「聲音」偏好設定的「輸出」或「輸入」面板中選擇一個音訊裝置，但是音訊輸出或輸入立即回覆為另一個音訊裝置，請嘗試下列解決方案：
    - 如果您將耳機或外接揚聲器插入連接至顯示器的 Mac，並在「聲音」偏好設定的「輸出」面板中選擇顯示器的內建揚聲器，則您的選擇會回覆為耳機或外接揚聲器。若要選擇顯示器的揚聲器，請先拔除耳機或外接揚聲器。
    - 如果您將耳麥插入連接至顯示器的 Mac，並在「聲音」偏好設定的「輸入」面板中選擇顯示器的內建麥克風，則您的選擇會回覆為耳麥。若要選擇顯示器的內建麥克風，請先拔除耳麥。
> 不太懂他的概念，可以多解釋一些嗎？
> [name=淑華]

- Researcher Breaks ReCAPTCHA Using Google's Speech Recognition API [http://m.slashdot.org/story/323117](http://m.slashdot.org/story/323117)
- 手機變錄音筆 可對錄line-in
    - [http://chdolodocha.pixnet.net/blog/post/31226423-%E6%89%8B%E6%A9%9F%E8%AE%8A%E9%8C%84%E9%9F%B3%E7%AD%86-%E5%8F%AF%E5%B0%8D%E9%8C%84line-in](http://chdolodocha.pixnet.net/blog/post/31226423-%E6%89%8B%E6%A9%9F%E8%AE%8A%E9%8C%84%E9%9F%B3%E7%AD%86-%E5%8F%AF%E5%B0%8D%E9%8C%84line-in)
- [https://www.facebook.com/humansofthefuture/videos/804090486415299/](https://www.facebook.com/humansofthefuture/videos/804090486415299/)
- 翻譯、字幕、逐字稿，多國語言素材處理相關工具收集區
    - [https://g0v.hackpad.tw/Tk13P0vMS9g](https://g0v.hackpad.tw/Tk13P0vMS9g)
- 待整理
    - https://www.facebook.com/573275047/posts/10165538104760048/

