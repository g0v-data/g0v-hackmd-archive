# install cowrie
`1.sudo apt update`+`sudo apt upgrade`

`2.sudo apt-get install python3-virtualenv libssl-dev build-essential libpython3-dev python3-minimal authbind virtualenv`
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5bdf2e539ac58f86d064f6a2202d8541.png)

`3.sudo adduser --disabled-password cowrie`
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3e4603c6523eba8ab3e335204748b549.png)

4.`sudo apt-get install git`
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9abb0c31840132a0694c109ca8fafb22.png)

5.`sudo git clone http://github.com/cowrie/cowrie
`
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b34afe34ef0b2a4214a74ede53534108.png)

6.`ls(確認有cowrie)`
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_528cb48e20d26a9095611f57472ddf8d.png)

7.`cd cowrie/`+`ls`
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_39e3207b6ddfc621174ed501f86041f6.png)

8.`sudo virtualenv --python=python3 cowrie-env`
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_18b63f6e364c876e137bbfa58d970f62.png)

9.`source cowrie-env/bin/activate `
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_73bb299394f5f16806e8ba69559136e6.png)


10.`sudo pip install --upgrade pip`
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_22463e445984aa06845dc6a8f1949745.png)

11.`ls`(注意要有requirements.txt)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5ebed9a2bd4b0f29da627ede94b5659b.png)

12.`pip install --upgrade -r requirements.txt`
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5ebe5e382e04d3a4585bbc24fecf04ec.png)
遇到問題
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_340d1d32df0fe6a86925917dd530e186.png)
`ls -l /home/kali/cowrie/cowrie-env`
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cb9ed6067af86d408ed815721b5c8b13.png)
`sudo chown -R kali:kali /home/kali/cowrie/cowrie-env`

`source /home/kali/cowrie/cowrie-env/bin/activate`

`pip install --upgrade -r /home/kali/cowrie/requirements.txt`
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a08bf100434d390810217be306a656e5.png)
這樣就ok了
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3d655855ff0841ae5d581f428819d483.png)

13.`sudo bin/cowrie start
`(ERROR: You must not run cowrie as root!
)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_64bbc4362ef7640528af067dc30acf9b.png)

14.`exit`

15.`cd cowrie/
`
16.`sudo passwd root`(設置root用戶密碼)+`su`(切換成root帳號)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e5706e94fb2532b9bf4df73e7acb7d6b.png)
17.`cd ..`+`sudo chmod -R 777 cowrie/`
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ec471adfb1d4c32dfd1942d2fca71c8b.png)


18.`virtualenv --python=python3 cowrie-env/
`![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b9ef4b94c5d5de3c85934a21d9cfdf83.png)


19.exit+`bin/cowrie start `
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_714c4aefa4c5a4992e1f1d28f811dff6.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2d7a6374c79aea40ae277eb5d486cc92.png)

20.`sudo iptables -t nat -A PREROUTING -p tcp --dport 22 -j REDIRECT --to-port 2222
`+`sudo iptables -t nat -A PREROUTING -p tcp --dport 23 -j REDIRECT --to-port 2223`
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c1062f441ade1c67938048e0b9657ad9.png)

21.apt-get install authbind
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4b43099ac96eb435c84e239f29ef3198.png)

22.`cd ..`+` touch /etc/authbind/byport/22`![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c0c792db25abdd46d5b813d0445bee56.png)

23.`sudo chown cowrie:cowrie /etc/authbind/byport/22`

24.`sudo chmod 770 /etc/authbind/byport/22`

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c5c0dc89bbef9d7e91a0da4ad8b1a55b.png)

25.`virtualenv --python=python3 cowrie-env/`

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a9532bb431f6308d866d7249c6a4ae80.png)

26.`bin/cowrie start`
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0012c002d374a40d8deba075b98d759b.png)
27.`ls`
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6c75ca8b39199e7e2802c421235f2adf.png)
**cd cowrie/var/log/cowrie**
開啟root權限(su)
28.`tail cowrie.log`
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4905858fc2ddf7a443590a9ab7821f80.png)













`
