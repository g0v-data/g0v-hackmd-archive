# System Programming - Slide4
# chapter 4

# Files and Directories
### Three major functions:
```
#include <sys/types.h>
#include <sys/stat.h>
int stat(const char *pathname, struct stat *buf);
int fstat(int filedes, struct stat *buf);
int lstat(const char *pathname, struct stat *buf);
```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b9cf62562d3073b10a416888b8b8d372.png)

在這三個函式中，都用到了stat 結構體， 這裡就介紹一下stat結構體。

```
struct stat{

    mode_t   st_mode;      //檔案訪問許可權，型別

    ino_t        st_ino;          //索引節點號

    dev_t       st_dev;         //檔案所在裝置的裝置號

    dev_t       st_rdev;       //檔案inode所代表的裝置的裝置號。

    nlink_t     st_nlink;      //硬連結數

    uid_t        st_uid;         //檔案所有者 使用者ID

    gid_t        st_gid;         //檔案所在組 組ID

    off_t         st_size;        //普通檔案，檔案大小， Bytes

    time_t      st_atime;     //檔案被最後訪問（access）的時間

    time_t      st_mtime;    //檔案內容最後被修改（modify）的時間
    
    time_t      st_ctime;     //檔案狀態最後被修改的時間（ status change）

    blksize_t st_blksize;     //檔案所在磁碟的磁碟塊大小

    blkcnt_t   st_blocks;      //檔案佔用塊數量

};
```
#### 函式返回值：

成功執行返回為0,  如果失敗則返回-1, 並且置errno。

#### stat， fstat， 和lstat 之間的區別是什麼呢？

對於stat，它可以僅僅通過檔案地址，獲取檔案屬性，而不一定要開啟檔案； 而fstat 需要將檔案開啟，獲取fd，然後通過fd來獲取檔案的stat。

對於連結檔案， stat獲取的檔案屬性是被連結檔案的檔案屬性，而lstat獲取的則是連結檔案本身的檔案屬性(info regarding the symbolic link)。

### File Types
* Regular Files: text, binary, etc.
* Directory Files: only kernel can update these files – { (filename, pointer) }.
* Character Special Files, e.g., tty, audio, etc.
* Block Special Files, e.g., disks, etc.
* **FIFO – named pipes**
* Sockets – not POSIX.1 or SVR4
* SVR4 uses library of socket functions, instead.
4.3+BSD has a file type of socket.
* Symbolic Links – not POSIX.1 or SVR4

### File Type Macros <sys/stat.h>
The argument to each of these macros is the st_mode member from the stat structure 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_358808544105a0429036f60c9650a979.png)
* `mystat.st_mode (mystat.st_mode & S_IFMT)` means to consider only the bits involved to determine the file type (regular file, socket, block or char device, etc.)
* Use `S_ISREG(buf.st_mode)` to check its type.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_922e7fbc2ef6aac3c8f9742f756a9c6a.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ee775b72391626e31041c351a077f480.png)


### Access Permissions & UID/GID
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9f778a9669d6c7d15049109ad587838b.png)

### Operations vs Permissions
* Directory
    * X – pass through the dir (**search bit**)
    * R – list of files under the dir.
    * W – update the dir, e.g., delete or create a file.
        * To create a new file, must have **write+execute** permission for the directory（因為要確定檔名沒重複所以要有執行的權限）
        * To delete a file, need write+execute on directory, file doesn’t
matter
        * Everyone has the write permission for /tmp. Does it mean
that you can delete any file in /tmp?
* File
    * X – execute a file (which must be a regular file), exec()
    * R – O_RDONLY or O_RDWR
    * W – O_WRONLY, O_RDWR, or **O_TRUNC**


### Set-User-ID/Set-Group-ID
* st_uid/st_gid: user/group ID of the owner.
* How can a user change his/her password without having the write permission to /etc/passwd and /etc/shadow?
Ans:
使用`passwd`指令，他會呼叫一個root擁有的執行檔，而這個執行檔裡面有做set-user-id，在執行時會把這個process的effective id設成此執行檔(/etc/password)的owner id(root=0)
* A **process** could have **more than one ID**.
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_07e33b276efb7568bd15a6a3d9db6da8.png)
* A創造了一個執行檔和一個目標檔案，目標檔案的權限是“rwx------”，執行檔的process會去開啟這個目標檔案，將這個執行檔交給B，並讓B擁有執行檔的x權限：
    * 如果沒有做set-user-id，則B無法開啟目標檔案，因為目標檔案的owner是A，而
        Ｂ開啟的執行檔的process:
        * real id: B's id
        * effective id: B's id
        * owner id: A's id
    * 有了set-user-id，B就可以開啟目標檔案，因為Ｂ開啟的執行檔的process會變成:
        * real id: B's id
        * effective id: A's id
        * owner id: A's id
    

 
### Access Permissions & UID/GID
* Real User/Group ID
    * from /etc/passwd
* Effective User/Group ID, Supplementary GID’s
    * check for file access permissions
* Saved Set-User/Group-ID
    * saved by **exec()**
    * saved IDs are optional in older versions of POSIX.
    * _POSIX_SAVED_IDS at compile time or callsysconf(_SC_SAVED_IDS) at runtime
* Set-User-ID
    * when a **file is executed**, set the **effective** user ID of its process to be the owner of the file
    * **S_ISUID** on st_mode **記錄有沒有做Set-User-ID這件事**
* Set-Group-ID
    * when a **file is executed**, set the **effective** group ID of its process to be the group owner of the file
    * **S_ISGID** on st_mode **記錄有沒有做Set-Group-ID這件事**


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a5ada922245a0bfa3edfedbb0015acae.png)
* s的value是倒數第四個bit

To locate the setuid, **look for an ‘s’ instead of an ‘x’** in the executable bit of the file permissions.

An example of an executable with setuid permission is passwd, as can be seen in the following output.

```
ls -l /etc/passwd
```

This returns the following output:
```
-rwsr-xr-x root root 2447 Aug 29  2018 /etc/passwd
```
As we can observe, the ‘x’ is replaced by an ‘s’ in the user section of the file permissions.

To set the setuid bit, use the following command.
```
chmod u+s 
```
To remove the setuid bit, use the following command.
```
chmod u-s 
```
### Comparison of real/effective UID
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6ccd5ea8fde64109444feec31c07def0.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_163dfe68e41d0c1495901cf65529e532.png)


### Discussion: Think About …
* How can a user just allow his friend to copy his files?
    * Give appropriate permissions to the files(How?)
    Ans: 給朋友這個檔案的名字和wx權限
    * Write a set-user-id program and protect the files himself (How?)
    * Any other methods? (open problem)
    
### Access Permissions & UID/GID
* File Access Test – each time a process **creates/opens/deletes a file**
    * If the effective UID == 0 -> superuser!
    * If the effective UID == UID of the file/dir
        * Check appropriate access permissions!
    * If the effective GID or any of its supplementary group*ID == GID of the file/dir
        * Check appropriate access permissions!
    * Check appropriate access permissions for others!

Related Commands: `chmod` & `umask`

### Ownership of a New File
* UID and GID of a new file by calling open() or creat()
* Rules
    * UID of a file (st_uid) = the **effective** UID of **the creating process**
    * GID of a file (st_gid) – options under POSIX
    要注意！
        1. GID of the file = the **effective GID of the process**
        2. GID of the file = the **GID of directory** in which it is being created
            * 4.3BSD and FIPS 151-1 always do it.
            * SVR4 needs to set the set-group-ID bit of the residing dir (mkdir)!
            * Ex: **/var/spool/mail** directory on Linux
            * 可能會出問題，process沒資格把directory的權限借給file

### Function – access
```
#include <unistd.h>
int access(const char *pathname, int mode)
```
* 傳回值:  0 : 檔案存在, 且符合指定條件, -1 無符合指定條件的檔案存在
* **Check the real UID/GID!**
* 使用時機: A process with set-user-ID to root wants to verify that the real user can access a given file
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ffe3584bbd6f6212b12b0bea0dd81f4d.png)
* Example:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3f79e0df12a849b28e33c25f36c710fd.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_70e1513dfd52435374cf7c59f4475697.png)

經過指令
```
chown root a.out
chmod u+s a.out
```
後，User A以root身份去執行a.out，則該process:
* real id: A's id
* effective id: A's id -> root
* owner id: A's id -> root

access函式檢查A對/etc/shadow的r權限，沒過
但因為effective id已經變成root所以可以open.


### Function – umask
```
#include <sys/types.h>
#include <sys/stat.h>
mode_t umask(mode_t cmask)
```
* **Turn OFF** the file mode
    * cmask = **bitwise-OR** S_I[RWX]USR, etc.
    * e.g. `umask(S_IWUSR | S_IXUSR | S_IWOTH)`
* The mask goes with the process only
    * Inheritance from the parent
    * No affection for the mask of its parent
* **Return: the previous value of the mask**
* 一般umask預設為022或002，一般檔案預設為666，一般資料夾預設為777(但像編譯過後的執行檔會具備x權限)
    所以在umask影響下檔案權限為644，資料夾預設為755
* Why is umask a **built-in** command in a shell? 
    1.在fork後可能出錯
    2.If umask were a separate program, then typing umask wouldn't change the umask value for the shell's process! See Appendix C if you are unsure why this scenario is so. A umask ( ) system call for programs that wish to further change their umask also exists.


#### Example
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_769841d0dcfa50edcbe3835d3ab75a51.png)

###  Function – chmod & fchmod
```
#include <sys/types.h>
#include <sys/stat.h>
int chmod(const char *pathname, mode_t mode)
int fchmod(int filedes, mode_t mode)
```
* fchmod() is not in POSIX.1, but in SVR4/4.3+BSD
* Callers must be a **superuser** or **effective UID = file UID**.
* Mode = **bitwise-OR** S_I[RWX]USR, S_ISVTX (sticky bit), **S_IS[UG]ID**, etc.
* **chmod – updates on i-nodes(meta)**
* chmod() automatically clears two permission bits under the conditions:
    * If we try to set the **sticky bit (S_ISVTX)** on a regular file and do not have superuser privileges, the sticky bit is automatically **turned off**.
    * If the GID of a newly created file is **not equal to the effective GID of the calling process** (or one of the supplementary GID’s), or the process is not a superuser, **clear the set-group-ID bit**!
    * **Clear up set-user/group-ID bits** if a non-superuser process writes to a set-uid/gid file.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_078f4b0976189d8e317330567e61e434.png)

### Sticky Bit (S_ISVTX) – saved-text bit
* Not POSIX.1 – by SVR4 & 4.3+BSD
* S_ISVTX executable file
    * Used to save a copy of a S_ISVTX executable in the **swap area** to speed up the execution next time.
    * Not needed for a system with a virtual memory system and fast file system.
* If the bit is set for a directory, a file in the directory can be **removed or renamed** only if the user has **write permission** for the directory
**and** one of the following:
    * Owns the file
    * Owns the directory
    * Is the superuser
* S_ISVTX directory file, e.g., /tmp
    * Remove/rename its file only if ‘w’ permission of the dir is set, and the process is belonging to superusers/owner of the file/dir
* This is the sticky bit, usually **01000**.
  you must have both **write permission for the directory and own the file** you want to **delete**. The one exception is that **the owner of the directory can delete any file** in the directory, no matter who owns it (provided the owner has given himself write permission for the directory). This is commonly used for the **/tmp directory, where anyone may create files but not delete files created by other users**.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2dea84bcb7955f44c77c7f4bbf638e56.png)
跟set user/group id一樣是倒數第4個bit

### Function – chown, fchown, lchown
```
#include <sys/types.h>
#include <unistd.h>
int chown(const char *pathname, uid_t owner, gid_t, grp);
int fchown(int filedes, uid_t owner, gid_t, grp);
int lchown(const char *pathname, uid_t owner, gid_t, grp);
```
* `lchown()` is unique to SVR4. **Under non-SVR4 systems, if the pathname to `chown()` is a symbolic link, only the ownership of the symbolic link is changed**.
* **-1** for owner or group if **no change is wanted**
*  超級使用者程序可以修改檔案的屬主和屬組，
       普通程序必須**擁有該檔案**才可以修改其屬主和屬組。
       
#### _POSIX_CHOWN_RESTRICTED is in effect (check pathconf())
* Superuser -> the UID of the file can be changed!
* The GID of the file can be changed if
    * **The process owns the file(effective id of process = user id of file)**, and
    * Parameter owner = UID of the file & parameter grp = the process GID or is in supplementary GID’s
    * This means that when _POSIX_CHOWN_RESTRICTED
is in effect, **you can't change the user ID of other users' files.** You can change the group ID of files that you own,
but only to groups that you belong to.
* **set-user/group-ID bits would be cleared if chown is called by non- super users**.

### File Size
* File Sizes – st_size
    * Regular files – 0~max (off_t)
    * Directory files – multiples of 16/512
    * Symbolic links – pathname length
* File Holes
    * st_blocks vs st_size (st_blksize)
    邏輯大小和控制大小沒有一定哪個比較大
     ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_647f3e86d2bfb62d9e4af21d1afe3216.png)

### Functions – truncate & ftruncate
```
#include <sys/types.h>
#include <unistd.h>
int truncate(const char *pathname, off_t length)
int ftruncate(int filedes, off_t length)
```
Not POSIX.1
SVR4: creates holes if length > fsize.
4.3+BSD: only truncates files to make them smaller.
Solaris: fcntl with F_FREESP to free any part of a file.

函式說明：truncate()會將引數path指定的檔案大小改為引數length指定的大小。 如果原來的檔案大小比引數length大，則**超過的部分會被刪除**

　　返回值：執行成功則返回0， 失敗返回-1， 錯誤原因存於errno

　　錯誤程式碼：EACCESS 引數path所指定的檔案無法存取

　　EROFS 欲寫入的檔案存在於只讀檔案系統內

　　EFAULT 引數path指標超出可存取空間

　　EINVAL 引數path包含不合法字元

　　ENAMETOOLONG 引數path太長

　　ENOTDIR 引數path路徑並非一目錄

　　EISDIR 引數path指向一目錄

　　ETXTBUSY 引數path所指的檔案為共享程式，而且正被執行中

　　ELOOP 引數path有過多符號連線問題

　　EIO I/O存取錯誤
  
### UNIX File and Directory
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_70e0b13aab1fa407ee1c98f4cc99ce75.png)

### File Systems
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9e176bec7874e56a4bdce1f5d800e7d0.png)
每個同心圓都屬於同一個Cylinder Group
* cylinder>> track >> sector
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9469988d55fe005aab0ab84a7a0ec8fe.png)

### Partition v.s. Physical Devices
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d7c73c2acf47f0bba5007ec73eee39a4.png)

輸入指令`more /etc/mtab` 可以得知每個資料夾屬於哪個partition

### i-node and data blocks
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_19f57e3347df90848f60b2f94c7dc056.png)
* i-node (**fixed size**) :
    * Version 7: 64B, 4.3+BSD:128B, S5:64B, UFS:128B
    * 儲存File type, **access permission**(所以多個link會有一樣的permission), file size, data blocks, referenced count(被幾個pointer指到), etc.
    * **Predefined** number of files that can be created.
    * It can happen that there is enough size, but i-node table is full.
    * `ls –i filename` (show i-node number)
* Link count – **hard links!!!**
    * st_nlink in stat, LINK_MAX in POSIX.1
    * Unlink/link a file
    * 就是以下的referenced count

#### Structure within a partition
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_067e00579ff2a392f2204d0cce428864.png)
* 每個leaf directory的referenced count =2
* 每個intermediate directory的referenced count >=3
* root的directory block的“..”可能指向自己或某個地方，每個系統不同
#### Relations between Directories and inodes
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_38b4e0bf0b0bf0c824aec2a22ad2b72a.png)

### Moving files among directory
* When files are moved **in the same mounted file system**, no need to physically move the file.
    * **Only directory block is updated**.
* Other, the file has to be physically
moved.

### File System – 4.4BSD i-node
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6af0f1da230a914f0577e4f84414d37d.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a714211b3155aea5b463e832b82bbc5c.png)


### Hard Link v.s. Soft Link
* Hard Link
    * Cannot link to different mounted file system.
    * 沒辦法連結目錄
    * Is a different name for the same set of data blocks.
    * Only superuser can create a link to a directory.
* Soft Link (or Symbolic link)
    * Can be a directory or file
    * Is a pointer to a set of data blocks.
    * File type is **S_IFLINK**
    * File size = pathname
* What’s the difference on their i-nodes? 

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bcecf20f194034b80ed459aec510bbcd.png)

指令：
* hard link: `ln /usr/joe/foo /usr/sue/bar `
* soft link: `ln -s /usr/joe/foo /usr/sue/bar `

差別：
* referenced count
* 當殺掉/usr/joe/foo 
    * hard link: 檔案仍存在 referenced count-1
    * soft link: 發生錯誤，/usr/sue/bar指到的i-node類型是S_IFLINK，會連到/usr/joe/foo，可是檔案已經不存在


### Functions – link, unlink
每一个文件，都可以通过一个struct stat的结构体来获得文件信息，其中一个成员**st_nlink**代表文件的链接数

当通过shell的touch命令或者在程序中open一个带有O_CREAT的不存在的文件时，文件的链接数为1。

`int link(const char *existingpath, const char*newpath)`
* Creation of the new dir entry and increment of the link count must be an **atomic operation**

`int unlink( const char *pathname)`
* (hardlink) 从文件系统中删除一个名称。如果名称是文件的最后一个连接，并且没有其它进程将文件打开，名称对应的文件会实际被删除。
* 成功执行时，返回0。失败返回-1，errno被设
* Sticky bits set for a residing dir, we must have the write permission for the directory and either owner of the file, the dir, or super users.
* **If pathname is a symbolic link, unlink references the symbolic link** (i.e.,it doesn’t follow symbolic link).
* Checking if any process has the file open
* close() might trigger the removal of file content

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0a8c8bfbc9ce282ebe23ccfe964e997c.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_06de8ebf553c9414c78c57734df78e65.png)
* unlink 之後打ls已經看不到tempfile
* 但因為程式沒有結束，tempfile仍佔用usage (18%)
* 直到process結束，tempfile才真正關閉(Use:15%)
* 這是一個很讚的做法，在程式有多個結束點的時候，很有可能忘記刪除暫存檔，讓它永遠佔著記憶體空間，所以open接著unlink的做法可以讓我們在process裡依舊可以對暫存檔做事
### Functions – rename, remove
```
int remove(const char *pathname)
int rename(const char *oldname, const char *newname)
```
* remove =
**unlink** if pathname is a **file**.
rmdir if pathname is a dir. (ANSI C)
* Rename – ANSI C
    * If oldname refers to a file:
        * if newname exists and it is not a directory, it’s removed and oldname is renamed newname
        * if newname exists and it is a directory, an error results
        * must **have w+x permissions for the directories** containing oldname and newname
    * If oldname refers to a directory:
        * if newname exists and is an empty directory (contains only . and ..), it is removed; oldname is renamed newname
        * if newname exists and is a file, an error results
        * **if oldname is a prefix of newname, an error results**
        * must **have w+x permission**
    * oldname & newname 必須同時是file或directory

### Symbolic Links
* Goal
    * Get around the limitations of hard links: 
(a) file system boundary (b) link to a dir.
    * Initially introduced by 4.2BSD

```
#include <unistd.h>
int symlink(const char *actualpath, const char *sympath)
int readlink(const char *pathname, char *buf, int bufsize)
```
* actualpath does not need to exist!
    * They do not need to be in the same file system.
* readlink is an action consisting of open, read, and close – not null terminated.
* readlink會得到這個link的path

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ea9f4e41f0142d97c31b3f6ea49eda60.png)


### File Times
* Three Time Fields:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_33e47790ab4eb34012f6fe024292e974.png)
* Changing the **access permissions, user ID, link count**, etc,
**only affects the i-node**!
* ctime is modified automatically! (stat & access are for reading)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_03e8ac174a6ef2dc7fd34b812b751f94.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9d1442d1cdb31d577cd69ff3d7e9c5f8.png)
write 可能會使file size變大，所以有c（動到i-node）

```
#include <sys/types.h>
#include <utime.h>
int utime(const char *pathname, const struct utimbuf *times)
```
```
struct utimbuf {
    time_t actime;
    time_t modtime;
}
```
函数说明：utime()用来修改参数filename 文件所属的inode 存取时间(a,m)
* time values are in seconds since the Epoch
* times = **null** -> set as the **current time**
    * Effective UID = file UID or W right to the file
* times != null -> set as requested
    * Effective UID = ( file UID or superuser ) **and W right** to the file.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0dd4d724e8cf0d997c643640d9966060.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f2a20ef9556d4b4aacf635b60c99448f.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_286f3bea64e3c432fef9bcbb1ed2debe.png)

### Functions – mkdir and rmdir
```
#include <sys/types.h>
#include <sys/stat.h>
int mkdir(const char *pathname, mode_t mode)
```

* umask, UID/GID setup (the same with file)
* . and .. are automatically created
```
#include <unistd.h>
int rmdir(const char *pathname)
```
An empty dir is deleted.
Link count reaches zero, and no one still opens the dir

### Functions – opendir, readdir, rewinddir, closedir
```
#include <sys/types.h>
#include <dirent.h>

DIR *opendir(const char *pathname)

struct dirent *readdir(DIR *dp)

void rewinddir(DIR *dp)

int closedir(DIR *dp)
```
* `DIR *` 是一種類似cursor的結構，會以某種不知道的方式遍歷這個directory的內容的set
* Only the kernel can write to a dir!!!
* WX for creating/deleting a file!
* Implementation-dependent!
* dirent struct is very implementation dependent, e.g.,
```
struct dirent {
ino_t d_ino; /* not in POSIX.1 */
char d_name[NAME_MAX+1];
} /* fpathconf() */
```
* ftw/nftw
recursively **traversing** the file system
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0ad3db1b8cba5a0f01a9bef952c6de94.png)

### Functions – chdir, fchdir, getcwd
```
#include <unistd.h>
int chdir(const char *pathname)
int fchdir(int filedes)
```
* chdir 就是cd 指令的c函式版
它必須是build-in函式這樣後續的程式才能在正確的位置作用
當process結束後會回到原本的位置（如下例）
* fchdir – not POSIX.1
    * chdir must be built into shells!
    * The kernel only maintains the i-node number and dev ID for the current working directory!
    * Per-process attribute – working dir!
* **cd is a built-in command**

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e38d78a87677c93263b6aa33611b96c7.png)

```
#include <unistd.h>
char *getcwd(char *buf, size_t size);
// get current working directory
```
* The buffer must be large enough, or an error returns!
* **chdir follows symbolic links, and getcwd has not idea of symbolic links**!
* 像下圖 因為/usr/spool是一個symbolic link指向 /var/spool 
所以getcwd直接顯示轉向後的位置

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_64ab70cff0aa941442627211688eb4ee.png)
* spool是一個symbolic link

### st_ino (I-node number)
* Each file has a unique i-node number(index number).
* The i-node number can be used to look up a file’s information (i-node) in a system table (the i-list).
* A file’s i-node contains:
    * user and group ids of its owner
    * permission bits
    * etc.


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6fbe805820a8bc2d689db5d18cc0af25.png)

