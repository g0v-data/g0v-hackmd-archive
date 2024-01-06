# virustotal command line tool

#### Source
https://github.com/VirusTotal/vt-cli

#### Installling the tool
```bash
$ git clone https://github.com/VirusTotal/vt-cli
$ cd vt-cli
$ make install
```
The executable file "vt" could be found under /vt-cli/build/. Edit ~/.zshrc(or ~/.bashrc) if you want to use "vt" directly in every shell.
```bash
#~/.zshrc file for zsh interactive shells.

export PATH="$HOME/Desktop/vt-cli/build:$PATH"
```

#### Basic VT commands
```bash
#insert your API key
$ vt init
 
#upload chin14.exe file to virustotal, an ID would be returned, you will need this ID for results query.
$ vt scan file virus/chin14.exe

#check the scanned results with the ID
$ vt analysis ID
```

#### Some optimization for convenience
save IDs in a file "vt_ID_list"![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_66df9b7209404176677e61956a301ab5.png)

record and check the results with the following commands
```bash
#upload file and save ID
#save_hash.sh should be build at current location first
$ vt scan file virus/chin15.exe | tail -1 | bash save_hash.sh  

#check the resultes
$ cat vt_ID_list | grep chin14-3.exe -A1 | tail -1 | vt analysis -
```



**file savehash.sh** :
```bash
#/bin/bash

read sentence
fileloc=/home/kali/vt_ID_list

IFS=" "
read -a stringarray <<< "$sentence"

echo ${stringarray[0]} >> $fileloc
echo ${stringarray[1]} >> $fileloc
                                     
```

