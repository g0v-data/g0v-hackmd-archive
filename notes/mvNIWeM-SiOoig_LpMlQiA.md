# Data structure
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

*null=0=something went wrong do not proceed
------
### reallocating spaces
use two elements, "list" and "node"
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_24f2532a0841f1cbbaf2e842b830510a.png)
insert "tmp" to expand the list
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8573648ed504c0e1d107cb354ddb3138.png)
_______
## Linked list
* nodes (節點)
雙向連結
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8421224acd8a8414b8515c798a01fc9d.png)
(prev=previous)
使用struct(結構)綑綁,連接不同數據體(這邊指針與data) 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_20e9227a142aa70c577538c800634d6f.png)
