# SP 2020 Assignment2 -B08902029陳咏誼
### 1. Directories and files. 
To reach `/home/user/alice.txt`, we access the directories: `root -> home -> user `first. 
Each directory corresponds to an i-node,inside which one direct pointer points to its directory block. 
Hence, we've accessed 3 i-nodes and 3 disk blocks so far.

And then we compute how many disk blocks an i-node can point to.
Each direct pointer points to 1 disk block.
Each singly-indirect pointer points to another block containing 1024 block pointers.
(1024 is obtained by sizeof(disk block)/sizeof( block pointer) = 4096/4 )
Each doubly-indirect pointer points to another block
containing 1024 singly-indirect pointers.
Each doubly-indirect pointer points to another block
containing 1024 doubly-indirect pointers.


Each i-node has:

| # of pointers |# of pointed disk blocks |
| -------- | -------- | 
| 12 direct pointers | 12     |
| 1 singly-indirect pointer     |  1 +  1024  |
|1 doubly-indirect pointer   |  1 + 1024 * (1+1024)    |
| 1 triply-indirect pointer     | 1 + 1024*(1 + 1024 * (1+1024))|
sizeof(`alice.txt`)/sizeof(disk block) = 5242880/4096 =1280.
So we have to access 1280 disk blocks to read the entire file itself.
To access 1280 disk blocks, we access one i-node since 1280 < 12+(1 +  1024 )+(1 + 1024 * (1+1024) )+(1 + 1024*(1 + 1024 * (1+1024))).

To access 1280 disk blocks, we access  12 direct pointers, 1024 direct pointers as branch of singly-indirect pointer and 1 singly-indirect pointer as branch of doubly-indirect pointer.
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fc1f246a251c656adb04618380c8ada6.png)


Consequently, if we want to read the entire
file of `/home/user/alice.txt`, we access 4 i-nodes and 1286 disk blocks.


### 2. Soft and hard links. 
( a ) Suppose there is a file *A* in Alice's Outbox and Alice creates a link *B* pointing to *A* and adds a file *C* by copying *A* in Bob's Inbox.
When the content of *A* is modified, the content of *B* simultaneously updates as well, while *C* remains its original content.
Hence, the advantage of creating a link in InBox over copying a file to InBox is that creating a link allows the contents in one person's Outbox and the other person's Inbox consistent.

( b )    Symbolic link is a better choice.
Since the intention of "Inbox & Outbox" is to share files for two users, if a file in Outbox is deleted by the owner, the link in Inbox should not able to access the file anymore.
Symbolic link satifies the property above while hard link doesn't, so symbolic link is better.

\( c \)    The access rights of Others should be:
* Directory InBox:`"-wx"`
* Directory OutBox (if hard links are adopted):`"---"`
* Directory OutBox (if symbolic links are adopted):`"--x"`

( d )    Bob can remove the file from his InBox directory in general case.
The fact that the file put in Bob's Inbox with permission `"r-- --- ---"` means only its owner Alice can read it. But the right to delete the file depends on the access rights for user of Bob's Inbox directory. In general case, the access rights of directory for user will be `"rwx"`, with write and execute authority, Bob can delete the file. However, if the access rights for user of Bob's Inbox lack write or execute authority, Bob can't delete the file.

