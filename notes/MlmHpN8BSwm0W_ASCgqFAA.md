# Week 10 - Balanced Binary Search Trees

## Team

>Members:
>
>- Margarita Konnari, 527941
>- Jiangshan Liu, 539663
>
> Date: *day* *month* 2023

## Activities

Make sure to have the activities signed off regularly to ensure progress is tracked.

Download the provided project and open it in CLion. **NOTE**: in this week you will have to reuse the code of last week. Follow the instructions given in the `main.cpp` file.

### Activity 1: Remembering tree heights

```cpp
void bintree_node::update_height() {
    if((this->has_right_child()) && (this->has_left_child()){
        if(this->m_right->m_height > this->m_left->m_height) //height of the right child is greater than the left
            m_height = this->m_right->m_height + 1;
        else
            m_height = this->m_left->m_height + 1;
    }
    else if(this->has_left_child())
        m_height = this->m_left->m_height + 1;
    else if(this->has_right_child())
        m_height = this->m_right->m_height + 1;
    else
        m_height = 1;
}
```

### Activity 2: Do it yourself: Balance factors

Left tree (Figure 3a):
| Node | Height | Balance factor |
|------|:------:|:--------------:|
| A    |    4   |        1       |
| B    |    2   |        -1      |
| C    |    1   |        0       |
| D    |    3   |       -1       |
| E    |    2   |        0       |
| F    |    1   |        0       |
| G    |    1   |        0       |
| H    |    1   |        0       |

Right tree (Figure 3b):
| Node | Height | Balance factor |
|------|:------:|:--------------:|
| K    |    4   |       -2       |
| L    |    3   |        1       |
| M    |    1   |        0       |
| N    |    2   |        0       |
| P    |    1   |        0       |
| Q    |    1   |        0       |
| R    |    1   |        0       |


### Activity 3: Computing the balance factor

```cpp
int bintree_node::balance_factor() const {
    if(this->has_right_child() && this->has_left_child()) 
        return (this->m_right->m_height - this->m_left->m_height);
        
    else if(this->has_left_child()) 
        return -this->m_left->m_height;
        
    else if(this->has_right_child())
        return this->m_right->m_height;
        
    else 
        return 0;
}
```

### Activity 4: Implement rotation

```cpp
bintree_node *bintree_node::rotate_left() {
    if (m_right == nullptr) 
        throw std::invalid_argument("rotate_left: right child is null");
    // TODO:
    //  Rotate the tree rooted at this node to the left, i.e. make the right child the new root
    //  Return the new root of the subtree
    bintree_node *new_root = this->m_right;
    this->m_right = new_root->m_left;
    new_root->m_left = this;
    this->update_height();
    new_root->update_height();
    return new_root;
}

bintree_node *bintree_node::rotate_right() {
    if (m_left == nullptr)
        throw std::invalid_argument("rotate_right: left child is null");
    // TODO:
    //  Rotate the tree rooted at this node to the right, i.e. make the left child the new root.
    //  Update the heights of those nodes for which the children have changed, in the right order.
    //  Return the new root of the subtree
    bintree_node *new_root = this->m_left;
    this->m_left = new_root->m_right;
    new_root->m_right = this;
    this->update_height();
    new_root->update_height();
    return new_root;
}
```

### Activity 5: Left rotations and balance

| B (Balance) | D (Balance) | A Height | C Height | E Height | Balance after rot | 
|-------------|:-----------:|:--------:|----------|----------|-------------------|
| +2          |      -1     |    H     |  H + 1   |    H     |       -2  H-(H+2) |
| +2          |      0      |    H     |  H + 1   |  H + 1   |       -1          |
| +2          |      +1     |    H     |    H     |  H + 1   |      0 (H+1)-(H+1)|
| +2          |      +2     |    H     |  H - 1   |  H + 1   |      0 (H+1)-(H+1)|

### Activity 6: Double rotations and balance

| Before rotation | After right-rot | After left-rot |
|-----------------|:---------------:|:--------------:|
| -1              |      -1         |       H        |
|  0              |      0          |                |
| +1              |      +1         |                |

Code written to create and rotate the trees:

```cpp
```

### Activity 7: Rebalancing the tree

```cpp
void bintree_node::rebalance() {  
}  
```

### Activity 8: Recursive tree traversal

```cpp
void print_tree(const bintree_node* node) {
}
```

### Activity 9: Insertion and removal

```cpp
bintree_node *balanced_insert(bintree_node *root, int value) {  
}

bintree_node *balanced_remove(bintree_node *root, int value) {
}
```

### Activity 10: Balanced tree

Record your answer here (include an image of the final tree)

Code used:

```cpp
```

### Activity 11: Time complexity

Formula for height of the tree: ....

|      Operation      | Time complexity |
| ------------------- | --------------- |
| Value insertion     | O(log n)        |
| Value removal       | O(log n)        |
| Membership testing  | O(log n)        |
