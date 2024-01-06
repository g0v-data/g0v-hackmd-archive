# 2022.05.02 觀念題

---
### 201703第22題
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e83914c07b054bec745ea19fc2cd5388.png)
> !的意思是將後面的東西反過來
> ||在c++的意思 跟python中or的意思一樣
**依題意希望  !(x1||x2)為True
進而希望    (x1||x2)為False
因此選(A)**

---
### 201703第13題
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_78fda9f7f90cfc77bc2e01c2e006983f.png =80%x)
右側程式片段無法正確列印 20 次的"Hi!"，請問下 列哪一個修正方式仍無法正確列印 20 次的"Hi!"？
A) 需要將 i<=100 和 i=i+5 分別修正為 i<20 和 i=i+1
B) 需要將 i=0 修正為 i=5
C) 需要將 i<=100 修正為 i<100;
D) 需要將 i=0 和 i<=100 分別修正為 i=5 和 i<100
```cpp=
原題i=0→輸出一次; i<=100; i=i+5→每次執行完後i+5 5~100總共20次，所以題目code輸出21次
A)i<20 → 執行19次 i=i+1→每次執行完+1
B)i=5 → 起始為5~100總計20次
C)i<100 → 不含100，總計20次
D)i=5 i<100 → 起始為5少一次，小於100少一次，總計19次 
```
---
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2beb217a0a4f8eec0209c91ff93c3251.png =40%x)
若以 F(15)呼叫右側 F()函式，總共會印出幾行 數字？ 
A)16 行 
B)22 行
C)11 行
D)15 行
```cpp=
條件if(n%2 == 1) →奇數，return F(5*n+1)
else n%2 == 0 →偶數，returnF(n/2)
F(15)帶入 → 輸出15 
→ F(5*15+1) = 76
F(76)=38
F(38)=19
→F(19)=(5*19+1) = 96
F(96)=48
F(48)=24
F(24)=12
F(12)=6
F(6)=3
→F(3)=(5*3+1) = 16
F(16)=8
F(8)=4
F(4)=2
F(2)=1 → n大於1
總計15次
```
---
### 106.03.04 第七題
若以 B(5,2)呼叫 B()函式，總共會印出幾次 “base case”？
```C=
int B (int n, int k) {
    if (k == 0 || k == n){
        printf ("base case\n");
        return 1;
    }
    return B(n-1,k-1) + B(n-1,k);
 }
 ```
(A) 1
(B) 5
(C) 10
(D) 19
* 把int n代入5，int k 代入2，將每次return的結果再代入B(n, k)，直到return 1為止，寫在紙上記錄下來即可得到答案。(以下附上Python詳解)
```python=+
print("請計算共有幾次k==0或k==n，以獲得解答: ")


def B(c: int, n: int, k: int):
    print(f"{'  ' * (c - 1)}第{c}次呼叫B函式: n={n} k={k}")
    if k == 0 or k == n:
        # print("base case")
        return 1

    return B(c + 1, n - 1, k - 1) + B(c + 1, n - 1, k)


print(f"A: 總共會印出{B(1, 5, 2)}次 base case")
```
* 延伸學習:
- [ ]遞迴
- [ ]C與Python的運算子優先順序
---


