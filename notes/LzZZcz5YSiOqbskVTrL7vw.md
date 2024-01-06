# System Programming - Slide6
# chapter8 (part2)

### Temporarily Elevate Privileges
* Why changes effective user id in the middle of a program execution?
    * Least-privilege model: a program should use the least privilege necessary to accomplish any task.
    * Reduce window of security vulnerability
    * Example
        * A process gains a privilege to access a privileged file and then gives up the privilege when no more accesses are required.

Unix都是能不變就不變：
1. child process 和 parent process同個effective id
2. user buffer在有需要用到的時候才會allocate
3. delay write
4. exec如果有set-s/g-id會改變effective id

### A process can have more than one ID(Ch.4)
* Real user/group ID: who you really are
* Effective user/group ID: determine file access permission
* Supplementary group IDs
* Saved set-user/group-ID = owner of the program with set-user/group-id bit set
    * Why do you need saved set-user-id?
        * Cannot give up privilege temporarily and get it back
    * 偶爾想借owner的id有時候想用我自己的real id



### Func: setuid(), setgid()
呼叫這隻system call的人不一樣效果就不一樣
```
#include <sys/types.h>
#include <unistd.h>
int setuid(uid_t uid);
```
* The process == superuser
-> set **real/effective/saved-suid = uid**
(不會check uid是誰 )
* Otherwise,
-> if uid == **ruid** or uid == **saved-suid**, then **euid=uid**
->把effective id變成real-uid或saved-set-uid
* Or errno=EPERM (_POSIX_SAVED_IDS)
* 成功return 0，否則-1
```
int setgid(gid_t gid);
```
* The same as setuid

### User/Group ID’s
* Only superuser process can change real uid
    * Normally done by the **login program**
`-r-sr-xr-x 1 root wheel 21040 ... /usr/bin/login*`
跟root借權限以查看/etc/passwd
* The euid is set by exec only if the setuid bit is set for the program file. 
**euid can only be set as its saved-suid or ruid.**
* exec **copies the euid to the saved-suid** (after the setting of euid if setuid bit is on).看下面圖表

### Ways to Change User ID’s
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_10c3d13e36c021eb79b09efca1d96a5d.png)
* process A exec program B, 如果program B的set-user-ID bit 是on的, process B的effective id就會變成programB的user id(owner id)
* We have `getuid() & geteuid()`
* Some systems provide a way to obtain the current value of the saved set-user-ID like **Linux** (`getresuid, getresgid`)

#### User B runs User A’s program in B’s shell
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2ea81e5137f1607e20ceeb17b93e05ee.png)


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4a25ccc4bbd53d74c738130fb911f729.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2a56d9af505c57ecc111d66882fa18d7.png)

#### 注意
right process的effective id是Ｂ因為exec會讓saved-set-user-id複製effective id
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_00e2edb0fbb55da385d680b452468a55.png)

### Utility of saved set-user-ID
* Example tip (BSD) or cu (SV)
    * 這裡不是要介紹tip & UUCP，是要假設有這兩個program 
    * tip & UUCP programs want to use the same modem(數據機) at the same time
    * UUCP: Unix To Unix Copy Program
    * A lock file is required for the exclusive use of the modem. The lock file is owned by uucp.
    * The **setuid bit is on** for **tip (owner=uucp).**
        * For file locking
        * 要借用uucp的權限才能access lock(因為lock的owner是uucp)
    * Tip calls setuid(ruid) for file access & later creating of shells/processes
        * Correct uid
    * Switch the euid back to uucp

### Example of Using setuid()
1. 要access和release lock之前都要把effective id設成uucp
2. step 2後用geteuid()得到uucpid，因為沒有直接得到saved-set-user-id的system call
3. 做完step2就不需要uucp的權限，在step3因為我要做我想做的事，所以應該用自己的權限，`setuid(getuid)`
4. 做完step4要release lock，所以需要uucp權限->`setuid(uucpuid)`，`uucpuid`是當初step1，effective id還是uucp的時候，用`geteuid`存起來的

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e7e374057b622cfb5c61843e69bac87e.png)

### Discussion
* What happens if tip spawns a shell while it is running in Step 3?
* What happens if tip is set-user-ID to root?
* Remark: Not good for files with setuid = root!

### Func: setreuid(), setregid()
```
#include <sys/types.h>
#include <unistd.h>
int setreuid(uid_t ruid, uid_t euid);
int setregid(uid_t rgid, uid_t egid);
```
* If the **effective user ID** of the calling process is **the superuser**, you can **set the real user ID and the effective user ID to any legal value**.
*  can Swapping of real and effective uids.
* **Non-superusers** can set **euid = [ruid or saved setuid ]**(after saved setuid is introduced)
* BSD only or BSD-compatibility library

### Func: seteuid(), setegid()
```
#include <sys/types.h>
#include <unistd.h>
int seteuid(uid_t uid);
int setegid(uid_t gid);
```
* Non-superusers can only set **euid=(ruid or saved-setuid)**.
* A privileged user only sets euid = uid.
* It is different from `setuid(uid)`

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_592f37810006ec037674ef9344839165.png)

### Process Times
```
#include <sys/times.h>
//想知道一個process run多久就會用到這個參數，呼叫兩次算差值
clock_t times(struct tms *buf);
struct tms {
    clock_t tms_utime; /* user CPU time */
    clock_t tms_stime; /* system CPU time */
    clock_t tms_cutime; /* user CPU time, terminated **child** */
    clock_t tms_cstime; /* system CPU time terminated child */
}
```
* Return elapsed wall clock time in clock ticks
* The returned value from some arbitrary point in the past. 
* In clock ticks (divided by CLK_TCK -> secs)
* type clock_t

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_512f756bb2a1d9ffb53291fed8fe7f9f.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e51370d69fefa93b2de0e9ecf03621e7.png)

### Calendar Time vs. Process Time
* Calendar time
    * In seconds since the Epoch (00:00:00 January 1, 1970, Coordinated Universal Time,i.e., UTC)
    * type time_t
    * Keeping time in UTC
    * **Automatic handling** of conversions such as**daylight saving time**
    * Keeping of time and date as a single quantity(Ch6.10)

### Time and Date Routines
可以換成年月日等等等 日光節約時間
```
#include <time.h>
time_t time(time_t *calptr);
```
* As a func in BSD, call gettimeofday
* Time initialization: settimeofday (BSD)
stime (SVR4)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_13dd3931b016ecc46ab925f19da2bb1c.png)

### Interpreter file
* 名詞定義：一個interpreter file裡面有interpreter(!#開頭的指令)

#### Example1
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_864bc92c66e3e08e6aefe797adade7f2.png)
```
execl("home/sar/bin/testinterp", "testinterp", "myarg1", "MY ARG2", (char*) 0 < 0)
```
* testinterp是一個interpreter file
* `#!/home/sar/bin/echoarg`是interpreter
* argv的排列: 先interpreter的argv，再exec的argv

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_33bab69c74f5a733fcdea559178d1006.png)

#### Example2
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3457389544889fcd0947a8356030d3ad.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0b089d992fcd6aff7c67af58c470353c.png)
上圖發生的事如下：
1. `cp /home/sar/bin/echoarg /bin/awk`：
`awk.c`被設成`echoarg.c`(裡面的argv是小寫)
2. terminal 看不懂什麼是`awkexample`所以fork 再exec`awkexample`，（預設是exec系列裡有p的function，所以pathname不用輸入完整路徑名，他會自己去環境變量找）
3. 此時就找到`/usr/local/bin/awkexample`，它是一個interpreter file，exec傳入的參數是`/usr/local/bin/awkexample`,`file1`,`FILENAME2`,`f3`
4. `awkexample`的內容是`/bin/awk -f`
5. 所以對shell來說，它看到的是
`/bin/awk -f /usr/local/bin/awkexample file1 FILE2 f3`
> 如果remove `-f` 最後就跑不了了
> 

還有...