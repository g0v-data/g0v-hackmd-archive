# Week 4 - Stacks and Queues

## Team

>Members:
>
>- Member one
>- Member two
>
> Date: *day* *month* 2023

## Provided code

The `zip` file on Blackboard contains the C code for this week.
The project contains three *targets*: `stacks`, `queues` and `circular-buffer`.

Also, the project uses a static library that provides an array and a linked list.
If you're on Windows, then run your code on WSL.

## Activities

Make sure to have the activities signed off regularly to ensure progress is tracked.

### Activity 1: LIFO vs FIFO

LIFO (last in, first out) is the method where the last-most recent added element is the first one that will be processed.

FIFO (first in, first out) is the method where the first- added  element is the first one that will be processed. 


A stack is sometimes called a LIFO memory buffer because is a structure which stores the elements on the following way.When a new item is added to the stack, it becomes the new top element, and when an item is removed from the stack, the top element is removed first. This means that the last item to be added to the stack will be the first one to be removed, which is why it is called a LIFO data structure.


### Activity 2: Stacks and LIFO

SYEUQTSAONIE

### Activity 3: Pushes and pops

B is not possible because 0 is poped out before 1.

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

Record your answer here

### Activity 6: Arrays, linked lists, and queues

| Operation                          |      Array      |   Linked List  |
| ---------------------------------- | --------------- | -------------- |
| Insert / remove **first** element  |     O(...)      |      O(...)    |
| Insert / remove **last** element   |     O(...)      |      O(...)    |
| Peek first / last element          |     O(...)      |      O(...)    |

Record your answer here

### Activity 7: Time complexities, once again

| Operation                     | Time complexity |
| ----------------------------- | --------------- |
| Insert / remove first element |    O(...)       |
| Insert / remove last element  |    O(...)       |
| Peek first / last element     |    O(...)       |

Record your answer here

### Activity 8: Clock arithmetic

Record your answer here

### Activity 9: Writing into a circular buffer

Record your answer here

### Activity 10: Reading from a circular buffer

Record your answer here

### Activity 11: Testing the queue

Record your answer here

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
