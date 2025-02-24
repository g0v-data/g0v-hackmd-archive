# Reverse Engineering
[toc]
## easy
### Transformation
I wonder what this really is... enc ''.join([chr((ord(flag[i]) << 8) + ord(flag[i + 1])) for i in range(0, len(flag), 2)])
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e6181830badac6613a926c36a2029839.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fde4d6a510873a10f840f31c0d8e3801.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7612643297f56c0cdbd83c64c5449ac0.png)
ans:picoCTF{16_bits_inst34d_of_8_75d4898b}
## medium
### crackme-py
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_20cd754015df300ffee7ee2156052d49.png)
- 將A:4@r%uL`M-^M0c0AbcM-MFE0d_a3hgc3N進行ROT47
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bab94d213a96af95f44889b516c013e3.png)

- ans:picoCTF{1|\/|_4_p34|\|ut_502b984b

### speeds and feeds
There is something on my shop network running at nc mercury.picoctf.net 20301, but I can't tell what it is. Can you?
hint:What language does a CNC machine use?
眾所周知，CNC工具機使用G代碼進行運作。因此，當我們在終端機上執行命令時，我們就有了 G 程式碼：nc Mercury.picoctf.net 33596
```
nc mercury.picoctf.net 20301
```
因此，我們將嘗試尋找可以幫助將 G 程式碼轉換為我們可以理解的內容的資源。

我們將首先儲存 g 程式碼，以便我們可以透過以下方式在某個地方使用它：nc Mercury.picoctf.net 33596 > g-code.txt

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9128c9bacf12ae4a23416aedc60c0279.png)
- 使用[網站進行轉換](https://cnc-apps.com/en/app/convert2svg)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c54faa1b04527debb813e1b9180328c4.png)
- ans: picoCTF{num3r1cal_c0ntr0l_e7749028}
## hard