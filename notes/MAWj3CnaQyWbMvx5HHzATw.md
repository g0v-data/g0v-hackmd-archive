# Week 3 - Linked Lists

## Team

>Members:
>
>- Margarita Konnari, 527941
>- Jiangshan Liu, 539663
>
> Date: 30/03/23

## Provided code

The `zip` file on Blackboard contains the C code for this week.
The project contains two *targets*: `singly_linked_lists` and `doubly_linked_lists`.
The first eight activities apply to the singly linked lists project, activities nine, ten, and eleven apply to the doubly linked lists project.

Make sure to test your code!
There are several `test_list_` functions provided in the `test_list.c` source and `test_list.h` header files.
These functions perform tests of your implementations by using the `assert` macro.
In case an assertion fails, your program will stop, and the failed assertion will be indicated in the console.

If you're on Windows, then run your code on WSL.
This allows you to use the *address sanitizer*, which will help you to locate bugs related to memory management.
To enable it, add the `-DUSE_ASAN=True` option to your CMake profile (Settings > Build, Execution, Deployment > CMake > CMake options).

## Activities

Make sure to have the activities signed off regularly to ensure progress is tracked.

### Activity 1: Chaining pointers

Use the following code in your `main` function.
Replace all pointer dereferences (e.g., `*pointer`) with the arrow operator.

```c
node_t first = { .value = 1,
    .next = &(node_t) { .value = 2,
        .next = &(node_t) { .value = 3,
            .next = &(node_t) { .value = 4,
                .next = NULL}}}};

printf("first: %d\n", first.value);
printf("second: %d\n", first.next->value);
printf("third: %d\n", first.next->next->value);
printf("fourth: %d\n", first.next->next->next->value);
```

### Activity 2: Traversal

Implement the function `print_nodes`, so that the two calls from the `main` function give the expected results.


```c
void print_nodes(const node_t *first) {
    for(const node_t* i = first; i != NULL; i = i->next) {
        printf("%d ", i->value);
    }
}

int main(void) {
    node_t first = { .value = 1,
	    .next = &(node_t) { .value = 2,
    		.next = &(node_t) { .value = 3,
	    		.next = &(node_t) { .value = 4,
		    		.next = NULL}}}};
	
	// expected output: 1, 2, 3, 4
	print_nodes(&first);
	
	// expected output: 3, 4
	print_nodes(first.next->next);
}
```

?
### Activity 3: Linked list deallocation

Implement the `list_destroy` function, such that the code does not contain a memory leak.
Use the address sanitizer to check if your code runs without memory problems.

```c
void list_destroy(list_t *plist) {
    if(plist != NULL) {
        node_t *currentNode = plist->head;
        node_t *nextNode;
        while(currentNode !=  NULL) {
            nextNode = currentNode->next;
            free(currentNode);
            currentNode = nextNode;
        }
    }
}

list_t list;
list.head = node_create(2);		// pointer to first node
list.head->next = node_create(3);	// create and add second node
list.head->next->next = node_create(7);	// create and add third node
list.head->next->next->next = node_create(42);	// add a final node	

list_destroy(&list);	// deallocate memory
```
### Activity 4: Appending to a singly linked list

```c
void list_append(list_t *plist, int value) {
    node_t *node = node_create(value);
    if(node != NULL) {
        if(plist->head == NULL) {
            plist->head = node;
        }
        else {
            node_t *currentNode = plist->head;
            while(currentNode->next != NULL) {
                currentNode = currentNode->next;
            }
            currentNode->next = node;
        }
    }
}
```

### Activity 5: Time complexity of prepend and append

Answer 1: 
The time complexity is O(n) because it will start from the head and go through all the n elements, until the tail to find the last node.
Answer 2: 
If we would keep track of the tail using a pointer the time complexity will be O(1), because we point to the 'old' end and the 'old' end points to the new element thet we appent. 

### Activity 6: Access by index

Implement the `list_at` function.
Use the `test_list_at` function to test your implementation.

```c
node_t *list_at(list_t *list, int index){
    node_t *current = list->head;
    int i = 0;
    while (current != NULL && i != index) {
        current = current->next;
        i++;
    }
    return current;
}
```

### Activity 7: A bad for-loop

Answer 1 
: The time complexity is O(n^2) because we go through 2 nested for loops.

### Activity 8: Removal in a singly-linked list
```c
void list_remove_last(list_t *plist) {
    node_t *current_node = plist->head;
    node_t *new_node = NULL;
    while(current_node->next != NULL) {
        new_node = current_node;
        current_node = current_node->next;
    }
    if(new_node != NULL) { //new_node is the pre last one
        new_node->next = NULL;
    }
    free(current_node);//finally we can free the last one 
}
```

### Activity 9: Appending to a doubly linked list

Implement the `list_append` function for the doubly linked list.
Make sure to select the proper "run configuration" in CLion.
Use the `test_list_append` function to test your implementation.

```c
void list_append(list_t *plist, int value) {
    if(plist != NULL) {
        if(plist->head != NULL) {
            node_t *new = plist->tail;
            new->next = node_create(value);
            plist->tail = new->next;    
            plist->tail->prev = new;
        }
        else {
            plist->head = node_create(value);
            plist->tail = plist->head;
        }
    }
}
```

### Activity 10: Removal from a doubly linked list

```c
void list_remove(list_t *plist, node_t *pnode) {
    if(plist != NULL) {
        if(pnode != plist->head && pnode != plist->tail) {
            node_t *temp_prev = pnode->prev;
            node_t *temp_next = pnode->next;
            temp_prev->next = temp_next;
            temp_next->prev = temp_prev;
            free(pnode);
        }
        else if (pnode == plist->head && pnode == plist->tail) {
            free(pnode);
            plist->head = NULL;
            plist->tail = NULL;
        }
        else if(pnode == plist->head){
            if(plist->head->next != NULL){
                plist->head = plist->head->next;
                free(plist->head->prev);
                plist->head->prev = NULL;
            }
        }
        else
        if(plist->tail->prev != NULL){
            plist->tail = plist->tail->prev;
            free(plist->tail->next);
            plist->tail->next = NULL;
        }
    }
}
```

### Activity 11: Insertion in a doubly linked list

```c
void list_insert_before(list_t *plist, node_t *pnode, int value) {
    if(plist != NULL){
        if(pnode != plist->head) {
            node_t *new_node = node_create(value);
            node_t *node_before = pnode->prev;
            pnode->prev = new_node;
            node_before->next = new_node;
            new_node->next = pnode;
            new_node->prev = node_before;
        }
        else {
            node_t *new_node = node_create(value);
            new_node->next = plist->head;
            plist->head = new_node;
            new_node->next->prev = plist->head;
        }
    }
}
```

### Activity 12: Time complexities


| Operation       | Array                      | Linked List |
| --------------- | -------------------------- | ----------- |
| Access          | O(1)                       | O(n)        |
| Append          | O(1)                       | O(n)        |
| Insert          | O(n)                       | O(n)        |
| Remove          | O(n)                       | O(n)        |

