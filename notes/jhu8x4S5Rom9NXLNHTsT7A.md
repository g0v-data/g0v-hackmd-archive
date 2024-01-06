﻿# Week 3 - Linked Lists

## Team

>Members:
>
>- Member one
>- Member two
>
> Date: *day* *month* 2023

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

list_destroy(&list);	// deallocate all memory
```
### Activity 4: Appending to a singly linked list

Implement the `list_append` function.
Use the `test_list_append` function to test your implementation.

```c
void list_append(list_t * list, int value);
```

### Activity 5: Time complexity of prepend and append

Record your answer here

### Activity 6: Access by index

Implement the `list_at` function.
Use the `test_list_at` function to test your implementation.

```c
node_t *list_at(list_t *list, int index);
```

### Activity 7: A bad for-loop

Record your answer here

### Activity 8: Removal in a singly-linked list

Implement the `list_remove_last` function.
Use the `test_list_remove_last` function to test your implementation.

```c
void list_remove_last(list_t * list);
```

### Activity 9: Appending to a doubly linked list

Implement the `list_append` function for the doubly linked list.
Make sure to select the proper "run configuration" in CLion.
Use the `test_list_append` function to test your implementation.

```c
void list_append(list_t * list);
```

### Activity 10: Removal from a doubly linked list

Provide the correct implementation for the `list_remove` function.
Use the `test_list_remove` function to test your implementation.

```c
// updates the list by removing the node referred to by node from the list
void list_remove(list_t *list, node_t *node) {
	node->prev->next = node->next;
	node->next->prev = node->prev;
	free(pnode);
}
```

### Activity 11: Insertion in a doubly linked list

Implement the `list_insert` function for the doubly linked list.
Use the `test_list_insert` function to test your implementation.

```c
// updates the list by inserting value before the node referred to by before
void list_insert(list *list, node_t *before, int value);
```

### Activity 12: Time complexities

Fill in the table with the correct big-O expressions.

| Operation       | Array                      | Linked List |
| --------------- | -------------------------- | ----------- |
| Access          | O(?)                       | O(?)        |
| Append          | O(?)                       | O(?)        |
| Insert          | O(?)                       | O(?)        |
| Remove          | O(?)                       | O(?)        |

## Looking back

### What we've learnt

Formulate at least one lesson learned.

### What were the surprises

Fill in...

### What problems we've encountered

Fill in...

### What was or still is unclear

Fill in...

### How did the group perform?

How was the collaboration? What were the reasons for hick-ups? What worked well? What can be improved next time?


