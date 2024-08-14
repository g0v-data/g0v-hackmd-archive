# Data structure
(a demonstration of how data doesn't need to be contiguous)
* queue 序列
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2e74d170fdd2d84a1bf5c318e5020f9c.png)

___
## malloc(memory allocation)
in the code
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_013121a92d07d0bff9e8d1eec8b360f6.png)
we focus on the line 
<pre> int *list = malloc(3 * sizeof(int));
</pre>
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9202aa7346db9f9cbf7977e5f79e609a.jpg)


| **Element**                | **Description (描述)**                                                                                      |
|----------------------------|-----------------------------------------------------------------------------------------------------------|
| `int *list`                | 声明一个名为 `list` 的指针，可以指向一个整数或整数数组的第一个元素。                                    |
| `malloc(3 * sizeof(int))`  | 使用 `malloc` 函数动态分配 3 个整数的内存。                                                                |
| `sizeof(int)`              | 返回一个整数的字节大小。通常在大多数系统上为 4 个字节。                                                   |
| `3 * sizeof(int)`          | 计算存储 3 个整数所需的总字节数（通常为 12 个字节）。                                                      |
| `list = malloc(...)`       | 将分配的内存地址分配给指针 `list`，该指针将指向数组的第一个元素。                                        |
| `free(list);` (not shown)  | 释放已分配的内存，以防止内存泄漏（在使用完已分配的内存后，最好释放）。                                   |
| `list == NULL` (optional)  | 通过验证 `list` 是否为 `NULL`，检查 `malloc` 是否成功。                                                    |

* null=0=something went wrong do not proceed
------
## reallocating spaces
use two elements, "list" and "node"
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_24f2532a0841f1cbbaf2e842b830510a.png)
insert "tmp" to expand the list
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8573648ed504c0e1d107cb354ddb3138.png)
_______
## Linked list
a dynamic data structure that can grow or sheink
* nodes (節點)
## 雙向連結(先製造箭頭!)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8421224acd8a8414b8515c798a01fc9d.png)

(prev=previous)
使用struct(結構)綑綁,連接不同數據體(這邊指針與data) 

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_20e9227a142aa70c577538c800634d6f.png)
----
### making array
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_90cb22a648b0f0d7afa5c517d09cc3d5.png)

<pre>node *list = NULL;
</pre>
indicate the list is initially empty.
___
### 将一个新的节点 n 插入到一个已经排序的链表中。它通过遍历链表找到合适的位置，然后插入新节点
*ptr= pointer
<pre>//implements a list of numbers using a linked list

#include <cs50.h>
#include <stdio.h>
#include <stdlib.h>

typedef struct node
{
    int number
    struct node *next;
}
node;

int main(int argc, char *argv[])
{
    //memory for numbers
    node *list = NULL;

    //for each command-line argument
    for (int i = 1; i < argc; i++)
    {
        //convert argument to int
        int number = atoi(argv[i]);

        //allocate node for number
        node *n = malloc(sizeof(node));
        if (n == NULL)
        {
            return 1;
        }
        n->number = number;
        n->next = NULL;

        //if list is empty
        if (list == NULL)
        {
            //this node is thewhole list
            list = n;
        }
        //if list has numbers already
        else
        {
            //iterate over nodes in list
            for (node *ptr = list; ptr != NULL; ptr = ptr->next)
            {
                //if at end of list
                if (ptr->next == NULL)
                {
                    //append node
                    ptr->next = n:
                    break;
                }
            }
        }
    }

}
</pre>
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_aa40777673dacda529cf6c16480aa49e.png)

<pre>

// Iterate over nodes in list
for (node *ptr = list; ptr != NULL; ptr = ptr->next)
</pre>
same format as "for (int i = 0; i < 3; i++)"
* break: 因为已经插入了节点，所以跳出循环。
* if (n->number < ptr->next->number):新节点 n 的值小于下一个节点 ptr->next 的值，说明新节点应该插入到当前节点和下一个节点之间。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_291fd5f5c4ff1970238e37e478715335.png)
___
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2a80ec80ac6cad381b0b5b85e1a14e28.png)

| 大 O 表示法 | 中文解释 |
|---|---|
| O(1) | 常数时间复杂度，表示算法的执行时间不受输入数据量的影响，始终保持不变。 |
| O(log n) | 对数时间复杂度，通常发生在每次迭代都能将问题规模缩小一半的情况下，例如二分搜尋。 |
| O(n) | 线性时间复杂度，表示算法的执行时间与输入数据量成正比。 |
| O(n log n) | 线性对数时间复杂度，通常发生在分治法中，例如快速排序。 |
| O(n²) | 平方时间复杂度，通常发生在需要嵌套循环的情况下，例如气泡排序。 |
___
### hash function
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_94fda4d316eed91a5e6a8b3950004f6e.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4f966d75c29962453dc3b89aade5c225.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_59e220be440855e749c8f265379ed3b8.png)
> * char：表示一個字符。
>* 星星字符(*)：表示指標，指向一個記憶體位址。
綜合起來，char* 就代表一個指向字符的指標。 也就是說，這個變數存儲的不是字符本身，而是指向字符的記憶體地址。

<pre>
#include <ctype.h>

unsigned int hash(const char *word)
{
    return toupper(word[0]) - 'A';
}
 </pre>
 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_64aabc4d45c84a6196b750e67d98b9e4.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b5fcb9299b53215e87401f2132459fa7.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_31f6fed69edaaedb1fd21c2f32929bdb.png)
