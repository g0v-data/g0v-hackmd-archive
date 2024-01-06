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
| -1              |      +1         |        +2      |
|  0              |      +2         |        +3      |
| +1              |      +2         |        +3      |

Code written to create and rotate the trees:

```cpp
    bintree_node nodeA{1}, nodeE{6}, nodeF{3};
    bintree_node nodeC{4, &nodeF, nullptr};
    bintree_node nodeD{5, &nodeC, &nodeE};
    bintree_node nodeB{2, &nodeA, &nodeD};
    std::cout<<nodeC.balance_factor()<<' ';
    nodeD.rotate_right();
    std::cout<<nodeC.balance_factor()<<' ';
    nodeB.rotate_left();
    std::cout<<nodeC.balance_factor()<<std::endl;

    bintree_node nodeA{1}, nodeE{6}, nodeC{3};
    bintree_node nodeD{5, &nodeC, &nodeE};
    bintree_node nodeB{2, &nodeA, &nodeD};
    std::cout<<nodeC.balance_factor()<<' ';
    nodeD.rotate_right();
    std::cout<<nodeC.balance_factor()<<' ';
    nodeB.rotate_left();
    std::cout<<nodeC.balance_factor()<<std::endl;

    bintree_node nodeA{1}, nodeE{6}, nodeF{3};
    bintree_node nodeC{4, nullptr, &nodeF};
    bintree_node nodeD{5, &nodeC, &nodeE};
    bintree_node nodeB{2, &nodeA, &nodeD};
    std::cout<<nodeC.balance_factor()<<' ';
    nodeD.rotate_right();
    std::cout<<nodeC.balance_factor()<<' ';
    nodeB.rotate_left();
    std::cout<<nodeC.balance_factor()<<std::endl;
```

### Activity 7: Rebalancing the tree

```cpp
bintree_node *bintree_node::rebalance() {
    update_height();    // Update the height of the current node
    // TODO:
    //  Check if the tree rooted at root is unbalanced, and if so, rebalance it.
    //  Return the node that is the new root of the tree after rebalancing, or the current root if no rebalancing
    //  took place.
    if(this->balance_factor() > 1){ //right-heavy
        bintree_node *child_root = this->m_right;
        if(child_root->balance_factor() < 0){ //right subtree of child_root is left-heavy so double rotation
            this->m_right = child_root->rotate_right(); //first right-rotate the right child
        }
        return this->rotate_left();//then left-rotate the full tree
    }
    else if(this->balance_factor() < -1){ //left-heavy
        bintree_node *child_root = this->m_left;
        if(child_root->balance_factor() > 0){ //left subtree of child_root is right-heavy so double rotation
            this->m_left = child_root->rotate_left(); //first left-rotate the left child
        }
        return this->rotate_right();//then right-rotate the full tree
    }
    return this; //already balanced
}
```

### Activity 8: Recursive tree traversal

```cpp
void print_tree(const bintree_node* node) {
    if (node == nullptr) {
        std::cout << '-';
        return;
    }
    std::cout << node->value();
    print_tree(node->left());
    std::cout << node->value();
}

//code to construct the tree
    bintree_node node1{1}
    bintree_node node42{42};
    bintree_node node2{2, &node1, nullptr};
    bintree_node node3{3, &node2, nullptr};
    bintree_node node4{4, &node3, &node42};
    print_tree(&node4);
    std::cout << std::endl;
```

### Activity 9: Insertion and removal

```cpp
bintree_node *balanced_insert(bintree_node *root, int value) {
    if (root == nullptr) { //create a new one
        m_count++;
        return new bintree_node{value};
    }
    if(value > root->m_value)
        root->m_right = balanced_insert(root->m_right,value);
    else if(value < root->m_value)
        root->m_left = balanced_insert(root->m_left,value);
    else
        return root;
    return root->rebalance();
}

bintree_node *balanced_remove(bintree_node *root, int value) {
    if (value == root->m_value) {
        if (root->is_full()) {
            // remove the node holding the minimum value in the right subtree of root,
            // and replace the value of root with the minimum value found
            root->m_right = balanced_remove_minimum(root->m_right, root->m_value);
        } else {
            bintree_node *temp_node = root;
            if (root->has_left_child()) {
                root = root->m_left;
            }
            else if (root->has_right_child()) {
                root = root->m_right;
            }
            else root = nullptr;
            delete temp_node;
            m_count--;
        }
    }
    else if (value < root->m_value && root->has_left_child()) {
        root->m_left = balanced_remove(root->m_left, value);
    }
    else if (value > root->m_value && root->has_right_child()) {
        root->m_right = balanced_remove(root->m_right, value);
    }
    else
        return root;   // value not found, no need to rebalance

    if (root != nullptr) {
        return root->rebalance();
    }
    else {
        return nullptr;
    }
}
```

### Activity 10: Balanced tree

```cpp
    bintree tree{};
    for (int i = 1; i < 16; i++) {
        tree.insert(i);
        bintree_writer::write_dot(std::string("tree" + std::to_string(i) + ".dot").c_str(), tree);
    }
    for (int i = 1; i < 16; i++) {
        tree.remove(i);
        bintree_writer::write_dot(std::string("tree_remove" + std::to_string(i) + ".dot").c_str(), tree);
    }
```

### Activity 11: Time complexity

Formula for height of the tree: log2(n + 1)

|      Operation      | Time complexity |
| ------------------- | --------------- |
| Value insertion     | O(log n)        |
| Value removal       | O(log n)        |
| Membership testing  | O(log n)        |
In a balanced binary search tree, the height is log with respect to the number of nodes.