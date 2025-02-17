# 密碼最短使用期限
* 忘記密碼API:
    *重設密碼通知信
    *進入更改密碼頁面的token驗證
    *進行密碼重設與
* 重設密碼(修改會員資料)

#### 紀錄
* 在**重設密碼通知信**，**進行密碼重設**(忘記密碼)與**修改會員資料**(重設密碼)中，加上**密碼最短使用期限**(1天)的驗證與限制(throw exception)
* 目前忘記密碼與重設密碼(修改會員資料)皆存在同一個db中

在前面加上:
```
List<MemberChangePass> memberChangePassList = memberChangePassRepository.findByMemberIdOrderByChangePassTimeAsc(member);
        	//密碼最短使用期限:1天
        	Long cantChangePassWordTime = new Date(System.currentTimeMillis()).getTime()-memberChangePassList.get(memberChangePassList.size()-1).getChangePassTime().getTime()-24*60*60*1000L;
        	if (cantChangePassWordTime < 0) {
        		long mins = -cantChangePassWordTime/1000/60;
        		long hr  = mins/60;
        		long min = mins%60+1;
        		throw new CustomException("您的密碼最短使用期限為 1 天。請等待 "+hr+"小時"+min+"分鐘"+"，然後再試一次。");
        	}
```