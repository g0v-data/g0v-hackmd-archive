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
