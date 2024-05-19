# 5/22
[toc]
# ch 09
## IPv4 Subnetting
- If a part has N bits, it can represent 2N - 2 subnets or hosts per subnet.
- 全部都是0或1不算，所以要-2
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_29c1dbc36ee14be081e3765a59b74bf5.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1093de98d4feea55f8f84b43bfa3550d.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_622401521d7abed0e66f3bf969f942d7.png)

==ans:6,62,62==

## Private IP Addresses
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_50ffcbd3e8942cd050cde6476f8744b7.png)

- 這些只能在公司內使用 ，永遠不會在互聯網上使用

## Network Address Translation (NAT)
- 在私人網路和公共網路之間轉換ip address
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9b1e3fbbe8e7bb7ce1d9fca52b4c2f9e.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_dd8367551376b07cd903db7944f7539c.png)

- 使用NAT的好處
    - 外部監聽者無法得知內部IP
    - 擴大可用IP地址的數量:一個ip可用的port大約有4000個，假設有248個ip address，表有248*4000個 external connection
        
## VPN

