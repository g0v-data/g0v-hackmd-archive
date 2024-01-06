第四實作
w=float(input("請輸入體重(kg)"))
h=float(input("請輸入身高(m)"))
BMI=w/(h*h)
if BMI<18.5:
    print("體重過輕")
elif BMI>=18.5 and BMI<24:
    print("正常範圍")
elif BMI>=24 and BMI<27:
    print("過重")
elif BMI>=27 and BMI<30:
    print("輕度肥胖")
elif BMI>=30 and BMI<35:
    print("中度肥胖")
else:
    print("重度肥胖")

第五-1實作
sum=0
n=1
while sum<=10**6:
  sum+=n
  n+=1
print(n)

第五-2實作
for i in range(1,10,1):
  for j in range(1,10,1):
    print(i,"*",j,"=",i*j)
    
    def a(m,r):
  return(m*r)
  
m=float(input("請輸入本金(萬)"))
r=float(input("請輸入年利率"))
t=float(input("請輸入貸款年數"))
while(t>=0):
  m=a(m,r)
  t-=1
print(m)