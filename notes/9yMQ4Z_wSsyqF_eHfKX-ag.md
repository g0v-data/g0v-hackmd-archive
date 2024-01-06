# 2019 / 06 / 28 - 2019/ 07 / 01

## COURSE4 - MVC


### First MVC Probject - Hello World

1. 新增專案 -> Visual C# Web -> ASP.Net -> FrameWork
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_41a04ff7e42a67ee1ba3bedac01a740d)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_cf02c2acd949e1713ac0673ff74744b3)





2. 創建 Controller
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2ad6620a4836267a00948691f83c4462)



![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8faf878859e6557406c4cc8ab65661dc)





---

==MVC-3==

相同的新增的專案，對Model新增類別(Employee)。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d666f3bd0f1bd110cc3f83fc005dce4d)




**C# 定義一個class裡面屬性的寫法**
```csharp=
    public int EmployeeID {get; set;}
    
    public string LastName {get; set;}
    
```



---
## ==MVC-6 View==

### Visual Stdio 2017一些debug的小技巧
- 可以直接將游標位置移至想要查看的函數上，點右鍵後查看定義（Ｇ），就能夠直接移至宣告它的檔案處
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_83c29fae5e05f6c8a6a9633018f266e9)
**若要退回的話，點選畫面左上角的箭頭向後巡覽即可。**
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5b0105a73d6db9d6774e4d3c91890792)


- 移動中斷點
中斷點：中斷程式的位置。
透過中斷點，可以在程式運行的過程中中斷執行緒，並取得目前記憶體中的物件內容。
    1. 按F5跳至下一個中斷點，就可以略過中斷點之間的步驟。
    2. 中斷點按得太快，想要再回頭看一次剛剛到底做了什麼。將左側中斷點紅點中間的黃色往上拉回想要看的地方
    

- 在設計網頁上有些部分無論網頁怎麼切都會有，例如最上面的banner，最下面的資訊欄位、快速連結。試想，若每一支網頁都要獨立劃分這些部分，在改版版的時候很麻煩、辛苦。故可使用小技巧-> layout主板頁面
使用情境：頁面上的某些部分，不論切到什麼畫面都會出現。
寫Layout和view的各自專心設計自己的部分，等到runtime的時候透過MVC的架構，會自己combime在一起。那user看到的頁面就會是完整的。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ad86b1d84a025e63cdf12b4c880643ec)

在處理主板頁面的時候，大家都有一個滿統一的命名規則。
（Shared資料夾＋主板頁面的命名最前加底線＿）
1. 在view處建立一個資料夾，通常會叫做Shared。
2. 接著在資料夾裡加入MVC5版面配置頁（Razor）
3. 產生出主板頁面
開發設計階段，寫程式的人focus在Content，主板頁面（Header、Menu、Footer...）會有人處理好。那麼對應到程式碼內：
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_1ac1b0caba730c8057fef145a543c836)

**＠RenderBody()就是寫單支功能的就會甜入到這塊裡面**

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_edf72efb663988540f4bb806e3d4ebc5)

創建好主板頁面後，像之前一樣新建controller，並新建view。特別注意的是使用版面配置頁（Use a layout page）處，若要引用剛剛設計好的主板頁面，可以電選左側（點點點）按鈕選擇相對應主板頁面檔案（_LayoutPage1.cshtml）引入

---
### ==- View Engine==
在view的部分（cshtml）一直在使用前面帶＠的東西，其實就是 .Net MVC提供的一種view engine（Razor）
**View Engine運作過程**：
1. Controller：從action拋出一些資料給view（在server端）
2. view engine接收，將cshtml的那些語法翻譯成user看得懂的html。（此動作是在server side跑的），並把html拋給user
3. html在client端呈現

**使用者看到的結果是 .Net逐行根據cshtml內的語法逐行翻成的html**

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_258029e9ac9c9f23e8ff98df63a201e3)

**若訊息從server端拋出來**
當設計師要寫的razer會跟很多JavaScript、jQuery混在一起的時候，又發現跑出來的結果跟預想的不同，可以看一下翻譯出來的html檔長成什麼樣子。
<運作流程：**在Controller.cs檔拋出訊息給view的cshtml，.Net razer會逐行翻譯成client端的html呈現給user**>


---
### ==HtmlHelper==

新增檢視，選擇一個範本，並指定模型類別，直接把controller長出去。接著裡頭長出來的用razer包起來的。

**TextBoxFor就是其中的一種htmlhelper**
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8095a5b7b7018ceaef147d042cb27775)

---
### ActionLink 超連結

---

### Html.EditorFor v.s. Html.TextBoxFor

如果透過visual studio預設建立出來的樣板，會使用Html.EditorFor，而 如果mdoel的型別是strin，建出的就會是text。而bool就會建成checkbox。若是integer，就會綁上html驗證，只能是數字。而EditorFor雖方便，但因擴充性不夠，故不建議使用。還是建議使用＠Html.TextBoxFor。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4a72807f472f7653b164f83e4912df90

---

### @HTml.OOO v.s. @Html.OOOFor 有for與沒for的差別

- Html.OOO
若要Mapping Action的參數，要自行指定Dom Name
- Html.OOOFor
可直接繫結Model強型別。


---

實作DropDownList
1. 對應到view
