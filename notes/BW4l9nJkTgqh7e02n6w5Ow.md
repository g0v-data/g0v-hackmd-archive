# 使用一個涵式抓取想要數值--適用於物件，如創立會員表單

首先假設user為下述物件 
```
const[user,setUser]=useState({name:"", phone:"", email:"" })
```
當我要抓取使用者在網頁打的數據使用涵式
```
const handleUser=(e)=>{
const{name,value}=e.target
}
```
上述為抓取使用該涵式的name及數值
```
setUser((prevUser)=>{
...prevUser,
[name]:value
})
```
...prevUser為保留物件原有數值
[name]:value為更改數值中為name變數的數值


為何使用 ...prevUser
假設 user 是這樣的一個狀態對象：

```


{
  account: 'user123',
  password: 'mypassword',
  confirmPassword: 'mypassword',
  phone: '1234567890',
  gender: 'male'
}
```
當你只想更新 account 的時候，...prevFormData 可以幫助你保留 password、confirmPassword、phone 和 gender 的值，然後只修改 account。

若有單選的話則可以使用checked=user.gender==="女"的方式去綁定所選擇的值