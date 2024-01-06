# Week 11 - Heaps

## Team

>Members:
>
>- Margarita Konnari, 527941
>- Jiangshan Liu, 539663
>
> Date: *day* *month* 2023                                                 |      |

## Activities

Make sure to have the activities signed off regularly to ensure progress is tracked.

### Activity 1: Comparing different data structures

| Data structure     | Find-max | Delete-Max |  Insert  |
|--------------------|:--------:|:----------:|:--------:|
| Sorted array       |   O(1)   |    O(1)    |  O(n)    |
| Sorted linked list |   O(1)   |    O(1)    |  O(n)    |
| Balanced BST       | O(log n) |  O(log n)  | O(log n) |

For finding/removing the maximum element: The sorted array and the sorted linked list have a worst-case time complexity of O(n), while the balanced BST has a worst-case time complexity of O(log n).
This is because for these two data
structures we would know exactly where the maximum value would be stored, and we could remove it
in constant time, assuming that the array would be sorted from low to high.

For inserting a new element: The balanced BST has a worst-case time complexity of O(log n), while both the sorted array and the sorted linked list have a worst-case time complexity of O(n).

### Activity 2: Identify valid heaps

The 1st and the 3rd trees are heaps. Both trees are min-heaps while their minimum element is stored in the tree’s root node.
The 2nd is not a heap while 29<37, 29<31, 37<43, 37<41.

### Activity 3: Do it yourself

Two swaps will be needed. 1st swap 12 with 3 and 2nd swap 12 with 11.

### Activity 4: Worst-case time complexities

| Data structure  | Find-max | Delete-Max |  Insert  |   Find   |
|-----------------|:--------:|:----------:|:--------:|:--------:|
| Balanced BST    | O(log n) |  O(log n)  | O(log n) | O(log n) |
| Binary max-heap |   O(1)   |  O(log n)  | O(log n) | O(log n) |

### Activity 5: Index computations

```cpp
size_t maxheap::parent_index(size_t index) {
    // TODO (Activity 5)
    //  return the index of the parent of the node at the given index, or npos if it does not exist
    size_t parent = (index - 1) / 2;
    if(parent < m_values.size()) {
        return parent;
    }
    return npos;
}

size_t maxheap::left_child_index(size_t index) {
    // TODO (Activity 5)
    //  return the index of the left child of the node at the given index, or npos if it does not exist
    size_t LeftChild = (index * 2) + 1;
    if(LeftChild < m_values.size()){
        return LeftChild;
    }
    return npos;
}

size_t maxheap::right_child_index(size_t index) {
    // TODO (Activity 5)
    //  return the index of the right child of the node at the given index, or npos if it does not exist
    size_t RightChild = (index * 2) + 2;
    if(RightChild < m_values.size()){
        return RightChild;
    }
    return npos;
}
```

### Activity 6: Implement the find-max operation

```cpp
const task &maxheap::maximum() const {
    // TODO (Activity 6)
    //  return the maximum value in the heap
    return m_values[0];
}
```

### Activity 7: Bubbling up

```cpp
size_t maxheap::bubble_up(size_t index) {
    // TODO (Activity 7)
    //  while the value at the given index is smaller than its parent value,
    //  bubble it up
    //  use the functions swap_at_index and parent_index
    size_t swaps = 0;
    size_t child = index;
    size_t parent = parent_index(child);
    while (m_values[child] > m_values[parent]) {
        swap_at_index(parent, child);
        swaps++;
        child = parent;
        parent = parent_index(child);
    }
    return swaps;
}
```

### Activity 8: Bubbling down

```cpp
size_t maxheap::bubble_down(size_t index) {
    // TODO (Activity 8)
    //  While the value at the given index is greater than any of its two child values,
    //  bubble it down
    size_t swaps = 0;
    size_t parent = index;
    while (true) {
        size_t LeftChild = left_child_index(parent);
        size_t RightChild = right_child_index(parent);
        size_t max_value = npos;

        if ((LeftChild == npos) && (RightChild == npos)) {
            break;
        }
        if ((LeftChild != npos) && (m_values[LeftChild] > m_values[parent])) {
            max_value = LeftChild;
        }
        if ((RightChild != npos) && (m_values[RightChild] > m_values[parent])) {
            if (m_values[RightChild] > m_values[LeftChild]) {
                max_value = RightChild;
            }
        }
        if (max_value != npos) {
            swap_at_index(parent, max_value);
            swaps++;
            parent = max_value;
        }
    }
    return swaps;
}
```

### Activity 9: Implement heapify

```cpp
size_t maxheap::heapify() {
    // TODO (Activity 9)
    //  fix heap violations by bubbling values down, starting with leaf nodes
    size_t swaps = 0;
    for (int i = m_values.size(); i >= 0; i--) {
        swaps += bubble_down(i);
    }
    return swaps;
}
```

### Activity 10: Heapify - time complexity

| Number of values | Number of swaps  |
|------------------|:----------------:|
| 5                |         3        |
| 10               |         8        |
| 20               |         17       |
| 50               |         47       |
| 100              |         96       |
| 200              |         195      |
| 300              |         295      |
| 400              |         394      |
| 500              |         493      |
| 1000             |         992      |

The worst-case time complexity of the heapify operation is O(n).

### Activity 11: Bubbling down vector elements

```cpp
void bubble_down(std::vector<int> &values, size_t index, size_t count) {
    size_t npos = - 1;
    size_t parent = index;
    while (true) {
        size_t LeftChild = (parent * 2) + 1;
        size_t RightChild = (parent * 2) + 2;
        size_t max_value = npos;

        if(LeftChild > (count - 1))
            LeftChild = npos;
        if(RightChild > (count - 1))
            RightChild = npos;

        if (LeftChild == npos && RightChild == npos) {
            break;
        }

        if ((LeftChild != npos) && (values[LeftChild] > values[parent])) {
            max_value = LeftChild;
        }
        if ((RightChild != npos) && (values[RightChild] > values[parent])) {
            if (values[RightChild] > values[LeftChild]) {
                max_value = RightChild;
            }
        }

        if (max_value != npos) {
            std::swap(values[parent], values[max_value]);
            parent = max_value;
        }
        else break;//it means the heap property is restored, so the loop breaks
    }
}
void heapify(std::vector<int> &values) {
    for(int i = values.size() ; i >= 0; i--) {
        bubble_down(values, i, values.size());
    }
}
```

### Activity 12: In-place heap sort

```cpp
void heap_sort(std::vector<int> &values) {
    heapify(values); //converts the vector into a max heap
    for(size_t i = values.size() - 1; i > 0; i--) {
        std::swap(values[0], values[i]);
        bubble_down(values,0,i);//restore the heap on the remaining elements
    }
}
```

### Activity 13: General heap sort

Include your generic implementations of `heap_sort`, `heapify` and `bubble_down`.

```cpp=
template<typename T>
void bubble_down(std::vector<T> &values, size_t index, size_t count) {
    size_t npos = - 1;
    size_t parent = index;
    while (true) {
        size_t LeftChild = (parent * 2) + 1;
        size_t RightChild = (parent * 2) + 2;
        size_t max_value = npos;

        if(LeftChild > (count - 1))
            LeftChild = npos;
        if(RightChild > (count - 1))
            RightChild = npos;

        if (LeftChild == npos && RightChild == npos) {
            break;
        }

        if ((LeftChild != npos) && (values[LeftChild] > values[parent])) {
            max_value = LeftChild;
        }
        if ((RightChild != npos) && (values[RightChild] > values[parent])) {
            if (values[RightChild] > values[LeftChild]) {
                max_value = RightChild;
            }
        }

        if (max_value != npos) {
            std::swap(values[parent], values[max_value]);
            parent = max_value;
        }
        else break;//it means the heap property is restored, so the loop breaks
    }
}

template<typename T>
void heapify(std::vector<T> &values) {
    for(int i = values.size() ; i >= 0; i--) {
        bubble_down(values,i,values.size());
    }
}
template<typename T>
void heap_sort(std::vector<T> &values) {
    heapify(values); //converts the vector into a max heap
    for(size_t i = values.size() - 1; i > 0; i--) {
        std::swap(values[0], values[i]);
        bubble_down(values,0,i);//restore the heap on the remaining elements
    }
}
```

