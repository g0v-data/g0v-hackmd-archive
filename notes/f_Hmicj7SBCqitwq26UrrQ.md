#    Windows Service打包安裝檔





windows Service加入後同一個方案下會產生ProjectInstaller.cs
裡面包含了serviceProcessInstaller1跟serviceInstaller1這兩個項目
沒有的話
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_292294b6410e47d1d57dd2efb614884e.png)
右鍵>設計工具檢視
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c2d405c6a511c21fb2b6647f41e2daa3.png)
右鍵>加入安裝程式
即可看到ProjectInstaller.cs與其下面兩個物件 如下圖兩個
### ServiceProcessInstaller
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7825c249d696833f2c4b0498e1e8879b.png)

通常會修改的只有Account這個屬性
關係到該服務使用的帳戶類型，預設User時在安裝會要求輸入登入的帳密
如果是LocalSystem類型就會要求Administrator權限
### ServiceInstaler
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ecc28567132735875d751bd1d6ef3b2d.png)
ServiceName - 服務名稱
DisplayName - 顯示名稱
Description - 描述
StartType - 服務的啟動類型，分為自動、手動、停用
如果是常駐型的服務，請選擇Automatic
DelayedAutoStart - 延遲開始，一般選False

### Setup屬性
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_886ae0e016c650ad93a8569a22d5215b.png)
Product Name - 軟體名稱，會顯示在安裝畫面上
Manufacturer - 製造商名稱，注意這個項目會變成預設安裝的路徑
InstallAllUsers - 預設安裝給所有使用者，安裝時可修改
RemovePreviousVersions - 重新安裝時是否要先把舊版本移除
Title - Metadata的標題，注意不會顯示在安裝程式中
Author - Metadata的作者
TargetPlatform - 安裝平台，會影響預設安裝路徑

預設安裝目錄為C:\Program Files (x86)\(Manufacturer)\(ProduectName)
其中TargetPlatform若為x86會裝在Program Files (x86)，反之是Program Files

# 重點
加入自訂動作，讓服務自動安裝
如果只修改了以上參數就直接安裝
應該會發現雖然安裝成功了，但是服務卻沒有裝進系統
這是因為我們目前的操作僅是把專案輸出檔案給複製過去，沒有設定安裝服務
所以我們需要加入自訂動作，安裝檔就會自動安裝/解除安裝服務了
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_816a8e052ec097111fba9bb28723846e.png)

安裝專案按右鍵，選[檢視]-[自訂動作]
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_db94bc36886548120a95856191196fc5.png)
出現畫面後，在自訂動作按右鍵選[加入自訂動作]
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8b371942f7aa45826d43bf2a89a4b1b8.png)
跳出詢問視窗後，雙擊[應用程式資料夾]，再選[主要輸出]
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3a0dee10ef6b70e96438301c04b18041.png)

## 安裝
方案上右鍵屬性
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a4dcccebc378222b940ead4d540d0c81.png)
**注意不可選功能表的建置方案**
setup預設的建置沒有打勾 需要打勾後在建置 建置完再Setup上右鍵安裝

## 安裝目錄會在 \開發單位\安裝專案名稱
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bb8abfe7b10dd8164b42133428eb59c1.png)



安裝完後，服務沒有啟動？
這是正常的
不知道為什麼沒有安裝完後自動啟動服務的選項
但沒關係，如果真的想要自動啟動，可以靠額外code達成

## 自動啟動服務
安裝完後，服務沒有啟動？
這是正常的
不知道為什麼沒有安裝完後自動啟動服務的選項
但沒關係，如果真的想要自動啟動，可以靠額外code達成
在ProjectInstaller.cs的程式碼內加入
using System.ServiceProcess;

public ProjectInstaller()
        {
            InitializeComponent();
            AfterInstall += (sender, e) =>
            {
                ServiceController sc = new ServiceController(serviceInstaller1.ServiceName);
                if (sc != null)
                    sc.Start();
            };
        }
        
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_81d27c00c5439e3c19044406a202402f.png)

## 加入專案額外的檔案

某些專案可能需要額外的資料檔
這些檔案也要在編譯時輸出到目錄

加入方式跟前面相同，[加入]-[專案輸出]，選擇[內容檔]

不過當你檢查輸出後會發現，有些檔案竟沒有被加入，這是怎麼回事呢？
我檢查了一陣子才知道，原來需要設定資料檔的屬性
建置動作需設定為[內容]才會加入
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6ebf5b820727bc741646f600a7c9045a.png)
順便一提，如果這些資料檔要跟執行檔放在同個目錄的話
複製到輸出目錄這一項請把[不要複製]改成別的選項

# 修改SetUp專案的必要安裝FrameWork
1.右鍵屬性
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4e745dbfd8d44020f537c0a19ceafcfb.png)
2.Prerequisites...後選版本
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ee051a965137135f941851d293840c31.png)
參考:https://stackoverflow.com/questions/6090913/make-an-installation-program-for-c-sharp-applications-and-include-net-framework




參考資料
https://catchtest.pixnet.net/blog/post/30397914-%E5%9C%A8visual-studio%E5%B0%87windows-service%E6%89%93%E5%8C%85%E6%88%90%E5%AE%89%E8%A3%9D%E6%AA%94
http://jengting.blogspot.com/2017/01/Windows-Service-Start-After-Install.html

https://blog.csdn.net/L120305q/article/details/98210048