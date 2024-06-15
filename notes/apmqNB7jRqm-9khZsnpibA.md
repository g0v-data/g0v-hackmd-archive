# Denian Package 打包教程筆記

source code打包內容
dpkg 指令打包流程
install 方式
實際例子


1. download現有package 
download source code -> https://sourceforge.net/projects/cscope/

2. tar xvzf cscope-15.1.tar.gz

3. dh_make --createorig -s -> 
若沒有.tar.xz，dh_make --createorig -s會建立 cscope_15.1.orig.tar.xz 和 debian/
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bc6b83afa245f6406daab48d3c21a605.png)

4. tree -> dh_make產生的debian files
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7233c51bb37521087cbbb12b6f3439b0.png)


5. 自建一個package
source code
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_61f79ef7beb28486488c2b607d399a7d.png)

tar -zcvf
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fd6f339ad1b095a1d7298fdd13647587.png)

dh_make
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8c715ee69eebef6784218213a946f408.png)

tree debian
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5b64f24a72cf3bf010e21a0f01396ccd.png)




kernel
make KERNELRELEASE="$(make kernelversion)" KDEB_PKGVERSION="$(make kernelversion)" -j"$(nproc)" bindeb-pkg

u-boot
dpkg-buildpackage -a "$(cat debian/arch)" -T build -d -uc -nc
dpkg-buildpackage -a "$(cat debian/arch)" -T binary -d -uc -nc


# control: package的資訊檔
$DEBEMAIL、 $DEBFULLNAME： 識別用於維護package的姓名和電子郵件地址。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2edaf524010773706b7b0d77d34fca13.png)

# copyright: 版權申明
# changlog: 紀錄跟上一版的差別
# rules: 類似於Makefile，會呼叫很多dh_xxx command
https://www.debian.org/doc/manuals/packaging-tutorial/packaging-tutorial.en.pdf
https://www.debian.org/doc/manuals/packaging-tutorial/packaging-tutorial.zh_TW.pdf
https://www.debian.org/doc/manuals/maint-guide/dreq.zh-tw.html#rules
http://www.study-area.org/cyril/opentools/opentools/x1447.html
