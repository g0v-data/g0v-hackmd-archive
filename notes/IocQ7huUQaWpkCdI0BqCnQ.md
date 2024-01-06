# Eason homeworks
```
for db in `mysql -u root -s -e "show databases"|grep -Ev '不要1|不要2|不要3' `
do
	mysqldump --single-transaction --add-drop-database  --add-drop-table --add-locks ${db} | gzip > ${BACKUP_FOLDER}/mysql-$(date "+%Y%m%d%H")-${db}.gz 2>/dev/null
	echo "$(date) backup ${db}"
done
```

# openvpn
```
 1005  wget https://swupdate.openvpn.org/community/releases/openvpn-2.5.3.tar.gz
 1006  tar -zxvf openvpn-2.5.3.tar.gz
 1007  cd openvpn-2.5.3/
 1008  ls -la
 1009  ./configure --prefix=/
 1017  yum install -y lz4*
 1018  ./configure --prefix=/
 1023  yum install -y pam-devel*
 1024  ./configure --prefix=/
 1025  make
 1026  make install
 1027  cd distro/systemd  #(看一下,你會想起來的)

```