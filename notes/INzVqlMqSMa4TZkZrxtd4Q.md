# Week 5 - Sorting

## Team

>Members:
>
>- Margarita Konnari, 527941
>- Jiangshan Liu, 539663
>
> Date: *day* *month* 2023                                                   |      |

## Activities

Make sure to have the activities signed off regularly to ensure progress is tracked.

Download the provided project and open it in CLion.

### Activity 1: Benefits of sorted data

 Answer 1:
 It is much simpler to look through a sorted array (time complexity: O(log n)) than an unsorted (time complexity: O(n)) due to the fact that you can constantly compare two values until you find the 42.
 
Answer 2:
binary search

### Activity 2: Find the smallest element

```c
int *find_min(int *values, size_t count) {
    if(count != 0) {
        int *min = values;
        for(int *ptr = values + 1; ptr < values + count; ptr++) {
            if(*ptr < *min) {
                min = ptr;
            }
        }
        return min;
    }
    else
     return NULL;
}
```
### Activity 3: Implement selection sort

```c
void array_sort(array_t *array) {
    if(array->count != 0) {
        for (size_t i = 0; i < array->count; i++) {
            int *a = &array->data[i];
            int *b = find_min(array->data + i, array->count - i);
            int temp;
            temp = *a;
            *a = *b;
            *b = temp;
        }
    }
}
```

### Activity 4: Selection sort: comparisons

| Array size | Comparisons |
|------------|-------------|
| 5          | 10          |
| 10         | 45          |
| 15         | 105         |
| 20         | 190         |
| 30         | 435         |
| 60         | 1770        |
| 90         | 4021        |
| 150        | 11191       |
| 300        | 44866       |
| 1000       | 499516      |
| 10000      | 49995016    |

### Activity 5: Merge sort - step by step

13 lists: [9], [0], [31], [5], [2], [8], [15], [13], [6], [4], [7], [11], [19]
7 lists: [0, 9], [5, 31], [2, 8], [13, 15], [4, 6], [7, 11], [19]
4 lists: [0, 5, 9, 31], [2, 8, 13, 15], [4, 6, 7, 11], [19]
2 lists: [0, 2, 5, 8, 9, 13, 15, 31], [4, 6, 7, 11, 19]
1 list: [0, 2, 4, 5, 6, 7, 8, 9, 11, 13, 15, 19, 31]

### Activity 6: Splitting a linked list in two halves

```c
node_t * split(node_t * phead) {
    node_t * fast = phead->next;
    while (fast != NULL && fast->next != NULL) {
        fast = fast->next;
        fast = fast->next;
        phead = phead->next;
    }

    node_t* node = phead->next;
    phead->next = NULL;
    return node;
}
```

### Activity 7: Merging two linked lists
```c
node_t *merge(node_t *a, node_t *b) {
    node_t temp = {.next = NULL};
    node_t *result = &temp;
    while (a != NULL && b != NULL) {
        if (a->value < b->value) {
            result->next = a;
            a = a->next;
        } else {
            result->next = b;
            b = b->next;
        }
        result = result->next;
    }
    if( a != NULL) {
        result->next = a;
    }
    else {
        result->next = b;
    }
    return temp.next;
}
```

### Activity 8: Implement merge sort

```c
// merge-sorts the list starting in first, and returns the first element
// of the resulting list
node_t * merge_sort(node_t * first) {
    if (first == NULL || first->next == NULL) {
        return first; // only a single node, so already sorted
    }
    else {
        node_t * next = split(first);

        // sort first
        node_t * left = merge_sort(first);

        // sort next
        node_t * right = merge_sort(next);

        // merge the two sorted halves
        first = merge(left, right);
        return first;
    }
}
```

### Activity 9: Merge sort: impact of order

The reason why more comparisons are made when sorting {1, 2, 3, 4, 5} compared to {5, 4, 3, 2, 1} is because the latter is already sorted in reverse order. When merging the two halves of the list in the merge-sort algorithm, fewer comparisons are needed to correctly place the elements in the correct order because they are already in reverse order. In contrast, when the elements are in increasing order, more comparisons are needed to correctly place the elements in the correct order.

### Activity 10: Merge sort: determining efficiency

| List length  | Comparions  |
|--------------|-------------|
| 5            | 5 - 7       |
| 10           | 15 - 19     |
| 15           | 24          |
| 20           | 35          |
| 30           | 64          |
| 60           | 259         |
| 90           | 584         |
| 150          | 1399        |
| 300          | 3629        |
| 1000         | 14979       |
| 10000        | 149979      |

### Activity 11: Compare merge sort and selection sort

| Algorithm        | Time complexity |
| ---------------- | --------------- |
| Merge sort       |   O(n log n)    |
| Selection sort   |     O(n^2)      |



