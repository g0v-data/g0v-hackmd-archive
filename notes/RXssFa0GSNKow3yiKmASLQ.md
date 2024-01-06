# Week 4 - Stacks and Queues

## Team

>Members:
>
>- Margarita Konnari, 527941
>- Kiki Liu, 539663
>
> Date: 11/04/23

## Provided code

The `zip` file on Blackboard contains the C code for this week.
The project contains three *targets*: `stacks`, `queues` and `circular-buffer`.

Also, the project uses a static library that provides an array and a linked list.
If you're on Windows, then run your code on WSL.

## Activities

Make sure to have the activities signed off regularly to ensure progress is tracked.

### Activity 1: LIFO vs FIFO

In LIFO (last in, first out) data structure, the latest element added to the structure is the first one that will be removed. 

In FIFO (fist in, first out) data structure, the first element added to the scructure is the first one that will be removed. 

A stack is sometimes called a LIFO memory buffer because when a new item is added to the stack, it becomes the new top element, and when an item is removed from the stack, the top element is removed first. In other words the last item that is added will be the first one to be removed.


### Activity 2: Stacks and LIFO

SYEUQTSEONIE

### Activity 3: Pushes and pops

B, 0 cant be taken out before 1.

### Activity 4: Communication through a linked list

```c
bool try_read_deque(list_t *list, char *value) {
    if(list_try_remove(list, FRONT, value)) return true;
    else return false;
}

void  write_deque(list_t *list, char value) {
    list_add(list, FRONT, value);
}
```

### Activity 5: FIFO and queues

EASYQUASTION

### Activity 6: Arrays, linked lists, and queues

| Operation                          |      Array      |   Linked List  |
| ---------------------------------- | --------------- | -------------- |
| Insert / remove **first** element  |     O(n)        |      O(1)      |
| Insert / remove **last** element   |     O(1)        |      O(n)      |
| Peek first / last element          |     O(1)        |      O(1)      |


### Activity 7: Time complexities, once again

| Operation                     | Time complexity |
| ----------------------------- | --------------- |
| Insert / remove first element |    O(1)         |
| Insert / remove last element  |    O(1)         |
| Peek first / last element     |    O(1)         |

### Activity 8: Clock arithmetic

```c
size_t buffer_get_rear_idx(const buffer_t *buffer) {
     temp = (buffer->head + buffer->count) % buffer->capacity;
     return tmp;
}
```

### Activity 9: Writing into a circular buffer

```c
bool buffer_try_write(buffer_t *buffer, char character) {
    if(buffer->count != buffer->capacity) {
        buffer->data[buffer_get_rear_idx(buffer)] = character;
        buffer->count++;
        return true;
    }
    else return false;
}
```

### Activity 10: Reading from a circular buffer

```c
bool buffer_try_read(buffer_t *buffer, char *character) {
    if(buffer->count != 0){
        *character = buffer->data[buffer->head];
        buffer->head = (buffer->head + 1) % buffer->capacity;
        buffer->count--;
        return true;
    }
    else return false;
}
```

### Activity 11: Testing the queue

The program works by copying the input file into the output file, using the buffer.