Install apache:
- download: https://www.apachehaus.com/cgi-bin/download.plx?dli=gTYJEShBTQ41ERNhnSHZkNRNlVUNlVSZ0StJ1MWd1b
- extract *httpd-2.4.52-o111m-x86-vc15.zip* to *C:\*
- open *Apache24* folder // this is the application directory
- open *bin* folder
- run *C:\Apache24\bin\httpd.exe*
Get rid of unneeded stuff
- go back to *Apache24* then open *conf* folder
- edit *httpd.conf* with either notepad/notepad++ [other programs may cause errors]

Paste:
```
LoadModule proxy_http_module modules/mod_proxy_http.so
LoadModule proxy_module modules/mod_proxy.so
LoadModule proxy_connect_module modules/mod_proxy_connect.so
LoadModule ssl_module modules/mod_ssl.so
LoadModule socache_shmcb_module modules/mod_socache_shmcb.so


<VirtualHost *:80>
ProxyPreserveHost On
ProxyPass "/" http://<remoteip>:80/
ProxyPassReverse "/" http://<remoteip>:80/
</VirtualHost>
```
to bottom then go to conf/extra and delete all but httpd-vhosts.conf

hold shift and right click and open cmd to run httpd.exe back in bin folder

Comment out lines that show up as errors and keep running and program until you get an error that doesn't show a line then kill the program in task manager and then run httpd.exe again.


- 

define a vhost

make a proxy

demonstrate it works




- 