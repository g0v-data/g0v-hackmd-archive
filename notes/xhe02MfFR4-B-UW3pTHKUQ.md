廢文編碼器 @ g0v-hackath33n
==========================

本日是第一次提案並開始製作，為了在第一次大松有個展示，打算先以最簡單的規則

文件
----
* [常用800詞CSV](https://gist.github.com/ronnywang/bec5ca97b2b6f30c6c37cbb3effa6812)
* [華語8000詞](https://www.sc-top.org.tw/download/8000zhuyin.zip) 
    * [來源](https://www.sc-top.org.tw/chinese/download.php)
* [中文情感分析语料库大全-带下载地址]( https://mlln.cn/2018/10/11/%E4%B8%AD%E6%96%87%E6%83%85%E6%84%9F%E5%88%86%E6%9E%90%E8%AF%AD%E6%96%99%E5%BA%93%E5%A4%A7%E5%85%A8-%E5%B8%A6%E4%B8%8B%E8%BD%BD%E5%9C%B0%E5%9D%80/)
* [中文NLP福利！大规模中文自然语言处理语料](https://mp.weixin.qq.com/s/NuU5p2mLG4Ln-s3-6chACg)
* [中研院中文斷詞系統](http://ckipsvr.iis.sinica.edu.tw/)
* [mozilla voice web 語料庫](https://github.com/mozilla/voice-web/tree/master/server/data/zh-TW)

可能流程 (需轉成js)
----
* encode :

    3 dict of size 256
    dict[0][0 ~ 255] : 主詞 (兩個字)
    dict[1][0 ~ 255] : 動詞 (兩個字)
    dict[2][0 ~ 255] : 受詞 (兩個字)

    廢文 = ""

    count = 0 // for 語句順序 主詞 + 動詞 + 受詞
    // byte : 0 ~ 255
    for byte in originial encrypted code :
        廢文 += dict[count % 3][byte]
        count += 1
        // random add 詞 not in any dict

* decode :

    dict[0][兩字主詞] : 0 ~ 255
    dict[1][兩字動詞] : 0 ~ 255
    dict[2][兩字受詞] : 0 ~ 255

    原文 = ""
    count = 0
    for 兩個字組成的詞 in 廢文 :
        if 兩個字組成的詞 in dict[count % 3]
            原文 += to_ascii_char(dict[count % 3][兩個字組成的詞])
            count += 1

TODO : 增加識別句 -> 規則 (句型 mapping 變化)、混淆句

字典
=======
* [兩字名詞](https://drive.google.com/file/d/1h9Lz8ZZPeKkj9DTe7GotgVLYUk_tEU6n/view?usp=sharing)
* [兩字動詞](https://drive.google.com/file/d/1MbxZrk1a2ZrDDAGBxyKyyGXtUoZZDPAM/view?usp=sharing)
* [兩字名詞 json (from 8000)](https://drive.google.com/file/d/12B_RG6QVCdQUivFEoRLDtrJ5jfi9z10F/view?usp=sharing)
* [兩字動詞 json (from 8000)](https://drive.google.com/file/d/1mklSYhuX_N7bn5WhRXN2uKM_kKp1MdSe/view?usp=sharing)
* [自建字庫](https://gist.github.com/CYLin1991/94019c868070f06d170af02c0184a223)

本日Q&A
=======
* Q: 請問規則是公開的嗎？如果公開的不就連監控者都可以解開嗎？
    * A: 在使用廢文編碼器時，應該拿已經加密後的亂碼來編碼，而不是拿原文來編碼，而不是用原文來編碼，這樣子監控者拿來解碼時解出來是亂碼，他也無法分辨這到底是不是有隱藏資訊的廢文編碼出來的東西還是真的是廢文。另外，廢文編碼器的解碼功能應該也要做成任何正常的中文語句也要都能夠產生出解碼結果，但是解出來也是無意義的亂碼，這樣更增加監控者分辨是不是廢文編碼產生的難度。
