# Week 2 - Dynamic Arrays

## Team

>Members:
>
>- Margarita Konnari
>- Kiki Liu
>
> Date: 12/03/2023


## Activities
Make sure to have the activities signed off regularly to ensure progress is tracked.

Before you start, download the project from Blackboard and explore the code contained in it.

### Activity 1: Random access

Rewrite the code by replacing **all** expressions in which pointers are dereferenced with equivalent ones that use the *array index operator* ("[..]").

````c
#include <stdio.h>
#define COUNT (50)

void fill_fibonacci(unsigned long long * storage, int count) {
	*storage = 0;
	*(storage + 1) = 1;
	for (int i = 2; i < count; i++) {
		*(storage + i) = *(storage + i - 1) + *(storage + i - 2);
	}
}

int main(void) {
	unsigned long long array[COUNT];
	fill_fibonacci(array, COUNT);
	for (int i = 1; i < COUNT; i++) {
		printf("f(%d) = %llu\n", i, array[i]);
	}
}
````

Answer:
````c
#include <stdio.h>
#define COUNT (50)

void fill_fibonacci(unsigned long long * storage, int count) {
    storage [] = 0;
    storage [1] = 1;
    for (int i = 2; i < count; i++) {
        storage[i] = storage[i-1] + storage[i-2];
    }
}

int main(void) {
    unsigned long long array[COUNT];
    fill_fibonacci(array, COUNT);
    for (int i = 1; i < COUNT; i++) {
        printf("f(%d) = %llu\n", i, array[i]);
    }
}
````
### Activity 2: Array definition

Explain what each of the three fields of the `array_t` structure listed below is used for.

Answer:
Capacity stores the amount of elements that can be stored in the array. Count stores how many elements are actually saved in the array. Data is the memory address of the elements in the array. 

Find out, for your system, what the maximum number of elements is that can be stored in the array.

Answer:
(2^64)-1, and that's because I use a 64bit system.
??

```C
typedef struct array {
    size_t capacity;
    size_t count;
    float *data;
} array_t;
```


### Activity 3: Correct initialization

Record your answer here.

```C
array_t *array_init(array_t *pArray, size_t capacity) {

}
```


### Activity 4: Cleaning up

Record your answer here.

```c
int main(void) {
    
}
```

### Activity 5: Resizing an array

Record your function definition here.

```c
void array_reserve(array *p_array, size_t min_capacity) {
    size_t capacity = p_array->capacity;
    while (capacity < min_capacity) {
        capacity = (capacity + 1) * ...
    }
	
	if (capacity != p_array->capacity) {
		/* reallocate memory, update capacity of array, etc. */
	}
}
```

### Activity 6: Appending values

Record your function definition here.

```c
void array_append(array * arr, float value);
```

Make sure to test your function using the `test_array_append` function.
Your code is correct if all the `assert` statements in the test function pass.


### Activity 7: Inserting values

Record your function definition here.

```c
void array_insert(array * arr, size_t index, float value);
```

Make sure to test your function using the `test_array_insert` function.
Your code is correct if all the `assert` statements in the test function pass.

### Activity 8: Removing by index

Record your function definition here.

```c
void array_remove(array * arr, size_t index);
```

Make sure to test your function using the `test_array_remove` function.
Your code is correct if all the `assert` statements in the test function pass.

### Activity 9: Constant time complexity

Record your answer here

### Activity 10: Worst-case time complexity

| Operation       | Worst-case time complexity |
| --------------- | -------------------------- |
| Insert          |                            |
| Remove          |                            |
| Lookup / access |                            |

Record your answer here

### Activity 11: Complexity of *append*

Record your answer here

### Activity 12: Storing grades in a dynamically growing array

```c
Include your program's code here.
```


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





> Written with [StackEdit](https://stackedit.io/).
