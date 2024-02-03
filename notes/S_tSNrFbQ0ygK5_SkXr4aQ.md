# picoCTF(page 10)
[toc]
## Permissions
Can you read files in the root file?
Additional details will be available after launching your challenge instance.
- 題目一開始將說能在根目錄找到檔案嗎? 所以先cd到根目錄
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_19098b36c983c1f4d8f05196b4cecee2.png)
- 查看根目錄有哪些檔案和權限，發現challenge這個路徑有問題，權限不夠無法cd
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_662f7a48fccbc3db395a3277505348b7.png)
- 查看sudo 發現使用者可以用sudo權限使用vi
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3bb9e3625f6e4438d60bc896f7fc11f6.png)
- 輸入sudo vi
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ef84f11576ff54fbf880b73ce2e92742.png)
- 啟動一個新的 shell 並暫時離開 vi
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c7cbdba033fdda13c9ae29379a873f75.png)
- 查看目前身分
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_123ecb02f31bac5a0101ac54083cdae4.png)
- cd challenge+ls，發現有個json檔
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a09484a6026ce0b57c92713a30d13b0c.png)
- `cat metadata.json`
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b79da13823a5c77c7c04230d43c3adcc.png)

- ans:picoCTF{uS1ng_v1m_3dit0r_1cee9dcb}

## HideToSee
How about some hide and seek heh?
Look at this image here.
[steghide](https://seamiloak.github.io/2020/08/24/Steghide%E4%BD%BF%E7%94%A8%E6%95%99%E7%A8%8B%E5%8F%8A%E5%85%B6%E5%AF%86%E7%A0%81%E7%88%86%E7%A0%B4/)
hint:Download the image and try to extract it.
- 下載圖檔
```
wget https://artifacts.picoctf.net/c/239/atbash.jpg
```
- 從atbash.jpg中解出
```
steghide extract -sf atbash.jpg
```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_be7387e318f59d952244a7620215a7ea.png)

- 解出了一個encrypted.txt，cat出來後是一段加密後的文字
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a300dba2b02b18c399e5b3b37e2a0b48.png)
- 推測是透過atbash
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2d8eb996e11fc13f924fe647fe054422.png)
- ans:picoCTF{atbash_crack_1f84d779}

## find me
Help us test the form by submiting the username as test and password as test!
Additional details will be available after launching your challenge instance.
- 利用burp suite打開網站後 輸入test、test!
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7ecdac5fb22c8e8dc417f0e302f937dd.png)
- 在login頁面的response可看到id=cGljb0NURntwcm94aWVzX2Fs
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_475a687bf0df28007ec8b2448dffa654.png)
- 提示說「有重定向嗎？」，進入登入畫面後，burp suite有收到兩個next page，另一個的id與上一個不同，id=bF90aGVfd2F5X2RmNDRjOTRjfQ==
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3bd0d6a4d4c3823633109c3c8fb863e0.png)
- 將這兩個id合併(cGljb0NURntwcm94aWVzX2FsbF90aGVfd2F5X2RmNDRjOTRjfQ==)進行base64解碼
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_24668d8473c859ec32c4f8f04a5baf2d.png)
- ans:picoCTF{proxies_all_the_way_df44c94c}