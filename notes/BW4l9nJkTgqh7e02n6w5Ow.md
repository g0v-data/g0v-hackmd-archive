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
上述註解為 抓取使用該涵式的name及數值
