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

- ans:picoCTF{1|\/|_4_p34|\|ut_502b984b}
## hard