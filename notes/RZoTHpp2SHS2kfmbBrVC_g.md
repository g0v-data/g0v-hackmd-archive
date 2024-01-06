# Week 9 - Binary Trees

## Team

>Members:
>
>- Member one
>- Member two
>
> Date: *day* *month* 2023                                            |      |

## Activities

Make sure to have the activities signed off regularly to ensure progress is tracked.

Download the provided project and open it in CLion.

### Activity 1: Maintaining order in arrays and linked lists - reprise

Record your answer here
|                    | Array  | Linked List |
| ------------------ | ------ | ----------- |
| value insertion    | O(...) | O(...)      |
| value removal      | O(...) | O(...)      |
| membership testing | O(...) | O(...)      |

### Activity 2: Recognizing BSTs

Record your answer here

### Activity 3: Searching for values

```c++
bool bintree::contains(int value) const {

}
```

### Activity 4: Inserting values

```c++
bool bintree::insert(int value) {

}
```

### Activity 5: Removing leafs

```c++
void bintree::remove_leaf(bintree_node *node, bintree_node *parent) {
    if (!parent->is_child(node)) throw std::invalid_argument("parent is not the parent of the node");
}
```

### Activity 6: Moving values around

Record your answer here

### Activity 7: Finding the smallest and greatest values

```c++
// snippets
```

### Activity 8: Removing full nodes

```c++
void bintree::remove_full_node(bintree_node *node) {
    (void) node;
}
```

### Activity 9: Cleaning up

```c++
void bintree::destruct_subtree(bintree_node *root) {
    if (root == nullptr) return;
    delete root;
}

bool bintree::remove(int value) {
    bintree_node * parent = &m_sentinel;
    auto node = m_root;
    return false;
}
```

### Activity 10: (Un)balanced trees

Record your answer here

### Activity 11: Time complexity

| Operation | Time complexity (if balanced)   | Time complexity (if unbalanced) |
| --------- | --------------- | --------------- |
| Lookup    | O(...)          | O(...)          |
| Insert    | O(...)          | O(...)          |
| Remove    | O(...)          | O(...)          |

