# Week 9 - Binary Trees

## Team

>Members:
>
>- Margarita Konnari, 527941
>- Jiangshan Liu, 539663
>
> Date: *day* *month* 2023                                            |      |

## Activities

Make sure to have the activities signed off regularly to ensure progress is tracked.

Download the provided project and open it in CLion.

### Activity 1: Maintaining order in arrays and linked lists - reprise

Record your answer here
|                    | Array  | Linked List |
| ------------------ | ------ | ----------- |
| value insertion    | O(n)   |   O(n)      |
| value removal      | O(n)   |   O(n)      |
| membership testing | O(n)   |   O(n)      |

### Activity 2: Recognizing BSTs

C is a binary search tree.
A: 72 is not less/equal  that 71 (A ≤ G ≤ F)
B: 84 is not greater than 85

### Activity 3: Searching for values

```cpp
bool bintree::contains(int value) const {
    // TODO (Activity 3) - find out if the tree contains the value
    //  return true if the value is in the tree, false otherwise
    if (m_root == nullptr){
        return false;// empty tree
    }
    bintree_node *value1 = m_root;
    while (value1 != nullptr) {
        if ((value1->value()) == value) {
            return true;  //found
        } 
        else if (value < (value1->value())) {
            value1 = value1->m_left;
        } 
        else {
            value1 = value1->m_right;
        }
    }
    return false;// not found
}
```

### Activity 4: Inserting values

```cpp
bool bintree::insert(int value) {
    if (m_root == nullptr) {
        // Let the sentinel node point to the root
        m_sentinel.m_left = m_root = new bintree_node{value};
        m_count = 1;
        return true;
    } else {
        // TODO (Activity 4) - insert the value into the tree
        // the tree already contains some nodes
        bintree_node *value1 = m_root;
        bintree_node *parent = nullptr;
        
        while (value1 != nullptr) {
            if ((value1->value()) == value) { //If the value is already in the tree, return false
                return false;
            } 
            else if ((value1->value()) > value) {
                parent = value1;
                value1 = value1->m_left;
            } else {
                parent = value1;
                value1 = value1->m_right;
            }
        }
        //otherwise insert a new bintree_node
        bintree_node *neww = new bintree_node{value};
        
        if ((parent->m_value) > value) {
            parent->m_left = neww;
        } 
        else {
            parent->m_right = neww;
        }

        //at the right place, increment the count, and return true
        m_count++;
        return true;
    }
}
```

### Activity 5: Removing leafs

```cpp
void bintree::remove_leaf(bintree_node *node, bintree_node *parent) {
    if (!parent->is_child(node)){
        throw std::invalid_argument("parent is not the parent of the node");
    }
    // TODO (Activity 5) - remove the leaf node from the tree
    //  - The bintree_node::replace_child function may be useful here
    //  - Make sure to deal correctly with the case of removing the root node
    if(node == m_root) { //empty tree
        m_root = nullptr;
        m_count = 0;
    }
    else { //remove a leaf node
        parent->replace_child(node, nullptr);
        m_count--;
    }
    delete node;
}

void bintree::remove_half_node(bintree_node *node, bintree_node *parent) {
    if (!parent->is_child(node)){
        throw std::invalid_argument("parent is not the parent of the node");
    }
    // TODO (Activity 5) - remove the node from the tree, and make sure that the tree remains a binary search tree
    //  - The bintree_node::replace_child function may be useful here
    //  - Make sure to deal correctly with the case of removing the root node
    if(node == m_root){
        if(node->has_right_child()) {
            m_root = node->m_right;
            m_sentinel.m_right = node->m_right;
        }
        else {
            m_root = node->m_left;
            m_sentinel.m_left = node->m_left;
        }
    }
    else{
        if(node->has_right_child()) {
            parent->replace_child(node, node->m_right);
        }
        else {
            parent->replace_child(node, node->m_left);
        }
    }
    m_count--;
    delete node;
}
```

### Activity 6: Moving values around

Left Tree: B or E, root>=B or root<=E
Right Tree: C or G, root>=C, or root<=G

### Activity 7: Finding the smallest and greatest values

```cpp
int value1(const bintree_node * root) {
    while (root->has_left_node()) root = root->left();
    return root->value();
}

int value1(const bintree_node * root) {
    while (root->has_left_node()) root = root->left();
    return root->value();
}

int value3(const bintree_node * root) {
    while (root->has_right_node()) root = root->right();
    while (root->has_left_node()) root = root->left();
    return root->value();
}

int value4(const bintree_node * root) {
    while (root->has_right_node()) root = root->right();
    return root->value();
}
```
Value1 successfully finds the smallest value and Value3 successfully finds the largest value.

### Activity 8: Removing full nodes

```cpp=
void bintree::remove_full_node(bintree_node *node) {
    // TODO (Activity 8) - remove the node from the tree, and make sure that the tree remains a binary search tree
    //  Replace the value of the node to be removed with an appropriate value from one of its descendant nodes,
    //  and then remove that descendant node from the tree.
    //  Note that node is guaranteed to have two children.
    bintree_node* parent;
    auto child = node;
    if(node->has_right_child()) {
        parent = child;
        child = child->m_right;
        while (child->has_left_child()) {
            parent = child;
            child = child->m_left;
        }
        node->m_value = child->value();
        if(child->has_right_child()){
            remove_half_node(child,parent);
        }
        else{
            remove_leaf(child,parent);
        }
    }
    else if(node->has_left_child()){
        parent = child;
        child = child->m_left;
        while (child->has_right_child()) {
            parent = child;
            child = child->m_right;
        }
        node->m_value = child->value();
        if(child->has_left_child()){
            remove_half_node(child,parent);
        }
        else{
            remove_leaf(child,parent);
        }
    }
    m_count--;
}
```

### Activity 9: Cleaning up

```cpp

bool bintree::remove(int value) {
    bintree_node * parent = &m_sentinel;
    auto node = m_root;
    return false;
}
void bintree::destruct_subtree(bintree_node *root) {
    if(root == nullptr) return;
    destruct_subtree(root->m_left);
    destruct_subtree(root->m_right);
    delete root;
    m_count--;
}
```

### Activity 10: (Un)balanced trees

Record your answer here

### Activity 11: Time complexity

| Operation | Time complexity (if balanced)   | Time complexity (if unbalanced) |
| --------- | ------------------------------- | ------------------------------- |
| Lookup    | O(n)                            | O(log n)                        |
| Insert    | O(n)                            | O(log n)                        |
| Remove    | O(n)                            | O(log n)                        |

Insert:from the root to the  (nnum of nodes)

- Membership testing involves traversing the tree from the root to the leaf. The time complexity is O(n), as we may need to visit every node in the tree to determine membership.
- Similar to insertion, removal in an unbalanced tree requires traversing the tree to find the node to remove. The time complexity is O(n), as we may need to visit every node in the tree to find the node to remove.

- Each insertion operation requires traversing the tree from the root to a leaf, resulting in a time complexity of O(log n), where n is the number of nodes in the tree. This is because the tree's height remains logarithmic in the number of nodes.
- In a balanced tree, membership testing involves traversing the tree from the root to a leaf.The time complexity is O(log n), as we only need to visit a fraction of the nodes to determine membership.
- Similar to insertion and membership testing, removal in a balanced tree requires traversing the tree to find the node to remove. The time complexity is O(log n), as we only need to visit a fraction of the nodes to find the node to remove.

Balanced:
Lookup: O(log n) 
Insert: O(log n) 
Remove: O(log n) 

Unbalanced: 
Lookup: O(n) 
Insert: O(n) 
Remove: O(n) 