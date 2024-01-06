# CH9 Public-Key Encryption

---

**特點**
1. asymmetric(非對稱)
2. key distribution : 不像對稱加密會有鑰匙要怎麼傳送的問題
3. digital sinature : 數位簽證
4. 兩把鑰匙:任一把鑰匙可以用來加密或解密，另一把做相對的事情(public key,private key)
5. Secrecy:保密性,Authentication:認證(要用誰的鑰匙組合)


## RSA 
公式:
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_50626a68b409cfc34fb268159655bd30.png)
C is Ciphertext ; M is plaintext 
**requirements**
1. M<n 這樣e,d,n才有可能
2. e&d 在modulo 尤拉(n)下互為乘法反元素
### complexity of computation
1. Encryption/Decryption
2. Key generation
3. 

