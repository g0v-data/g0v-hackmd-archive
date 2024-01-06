台灣賄選實價登錄地圖
===
###### tags: `台南小松`

舊版地圖： https://kiang.github.io/bribes_map/
新資料研究： https://github.com/kiang/bribes_data
Howard 完成的前端介面： http://bribes.goodideas-campus.com/
kiang 做的 api ： http://bribes.olc.tw/
repo: https://github.com/kiang/bribes_api
api 取得任務： http://bribes.olc.tw/issues/task

過去是由 ptt 網友 jaystar0423 所整理， kiang 協助把多個地圖拼在一起方便一次檢視，當時只能人工方式進行各種判決書的檢索，因此沒辦法大規模實做，最近這幾年資料開放了，應該可以振作了（嘆）



司法院開放資料： http://data.judicial.gov.tw/

問題：
1. 如何找出賄選相關的判決書資料
    1. "JTITLE": "選舉罷免法"
    2. sample: 201907/臺灣苗栗地方法院刑事/MLDM,108,選訴,5,20190703,1.json

```
<?php
$fh = fopen(__DIR__ . '/targets.csv', 'w');
fputcsv($fh, array('file', 'title'));
foreach(glob(__DIR__ . '/extract/*/*') AS $host) {
    if(mb_substr($host, -2, 2, 'utf-8') === '刑事') {
        foreach(glob($host . '/*.json') AS $jsonFile) {
            $json = json_decode(file_get_contents($jsonFile));
            if(false !== strpos($json->JTITLE, '選')) {
                $pos = strpos($jsonFile, '/extract/') + 9;
                fputcsv($fh, array(substr($jsonFile, $pos), $json->JTITLE));
            }
        }
    }
}
```

2. 初步產出的目標清單(9112 件) https://gist.github.com/kiang/8ef35ea6e2cc2a9815734b482172b55a
3. 例外： 201601/臺灣桃園地方法院刑事/TYDM,104,選易,2,20160120,1.json
    1. 這份也有提到賄選金額，但 JTITLE 是 "妨害投票"
    2. 找了一下，全國的 "選易" 案件只有 277 件，數量不多
4. 如何從判決書資料找到實際用來賄選的金額與標的
5. （群眾外包）如何讓大家參與資料的審核，配對特定候選人，以及如何找出個別判決書的點位資料，類似 https://campaign-finance.g0v.ctiml.tw/
    1. 地理點位
    2. 賄選金額
    3. 候選人(不一定要，因為行情地圖應該就可以達到目的)

需要的協助：
1. 大資料處理 - 法院判決書資料檔案共約 34GB ，解壓縮後約 112 GB ，透過程式處理比較吃力，如果有語意分析處理背景或是人工智慧相關領域的朋友協助應該會好很多
2. 對判決資料感興趣
3. 希望幫忙整理資料
4. 視覺設計

補充資訊：
* 有"賄"字的案號字，不過 "TPSM,85,台上,386,19960125" 看起來也是賄選相關案件？JCASE 有 "選" 字從資料上看好像是從 2000 年開始，有選字的資料包含民事與刑事，大約 11461 件( https://gist.github.com/kiang/62e14b5b6ab83e882fc07f360d240a6a )
    * 選上重訴
    * 選上訴
    * 選上易
    * 選簡上
    * 選簡
    * 選訴
    * 選重訴
    * 選易
* 有"上"字的都一定是二審
* `"JID": "TYDM,108,選訴,2,20191007,1"`
    * 分別為: Court,YearOfTrial,Case,Number,TrialDate,SeriesNumber
* Court的部分包含法院別（縮寫3碼）與案件類別（縮寫1碼）
舉例：NTDM
    * NTD代表南投地方法院，M代表刑事案件。NTDA是南投地院行政案件，NTDV是南投地院民事案件。
    * TPS是最高法院，M是刑事案件
    
相關資訊：
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c11bc6dd00c42e9f99adc606de14ad59)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_94bcf9c1b241e4da34aa56fb062ee42c)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_7d0a64b331429357320c06e39fcf26ee)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f2f24f21861492947c3897c256e9f639)
* [廉政](https://www.mjib.gov.tw/FileUploads/eBooks/2728713e8ee64054aa8c80b29425e8b8/Book_file/0a80b4834f2445a0a49a494845a3851f.pdf)101~105年賄選統計，蠻有趣的

相關專案：
1. https://github.com/biglawtw - 過去是透過爬蟲抓取所有判決書資料進行處理，現在網站已經消失，裡面有些判決書處理的程式碼，主要是 javascript / python