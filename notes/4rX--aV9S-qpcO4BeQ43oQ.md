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

```C
typedef struct array {
    size_t capacity;
    size_t count;
    float *data;
} array_t;
```


### Activity 3: Correct initialization

Answer 1:
The correct is the second one. 

Answer 2:
The first one is not correct because the data array will no longer exists after the function returns.As a conclusion p_array->data will point to a wrong memory address.

Answer 3:
```c
array_t* array_init(array_t *p_array, size_t capacity) {
    if (p_array != NULL){
        p_array->data = malloc(sizeof(float[capacity]));
        p_array->count = 0;
        p_array->capacity = p_array->data != NULL ? capacity : 0;
    }
    return p_array;
}
```

### Activity 4: Cleaning up
Answer:
The correct is the second one. The memory is allocated dinamically and when the free() function is called the memory is dealocated correctly.
The memory of the first one is not allocated dinamically. 

```c
int main(void) {
	array_t *array = (array_t *) malloc(sizeof(array_t));
    array_init(array, 10);
    // .... do some work ...
    // finally, clean up
    array_destroy(array);
    free(array);
}
```



### Activity 5: Resizing an array

```c
void array_reserve(array_t *p_array, size_t min_capacity) {
    size_t capacity = p_array->capacity;
    while (capacity < min_capacity) {
        capacity = (capacity + 1) * 1.5 /* insert your factor here */;
    }
    if (capacity != p_array->capacity) {
        p_array->capacity = capacity;
        p_array->data = (float *) realloc(p_array->data, sizeof(size_t[capacity]));
    }
}
```
### Activity 6: Appending values

```c
void array_append(array_t *arr, float value){
    arr->size += 1;
    if(arr->size > arr->capacity){
        array_reserve(arr, arr->size);
    }
    value = arr->data[arr->size];
}
```

### Activity 7: Inserting values

```c
void array_insert(array_t *arr, size_t index, float value){
    arr->size += 1;
    if(arr->size > arr->capacity){
        array_reserve(arr, arr->size);
    }
    for(size_t i = arr->size-1; i > index; i--){
        arr->data[i] = arr->data[i-1];
    }
    arr->data[index] = value;
}
```

Make sure to test your function using the `test_array_insert` function.
Your code is correct if all the `assert` statements in the test function pass.

### Activity 8: Removing by index

```c
void array_remove(array_t *arr, size_t index){
    for(size_t i = index; i < arr->size; i++){
        arr->data[i] = arr->data[i + 1];
    }
    arr->size --;
}
```

### Activity 9: Constant time complexity

Answer 1:
Time complexity is constant if the running time isn't dependent on the input size.

Answer 2:
O(1)

### Activity 10: Worst-case time complexity

| Operation       | Worst-case time complexity |
| --------------- | -------------------------- |
| Insert          | O(n)                       |
| Remove          | O(n)                       |
| Lookup / access | O(n)                       |

Insert:vthe function needs to shift all the elements in the array by one position to the right to create space for the new element to be inserted at the specified index, using a for.

Remove: The function needs to shift all the elements in the array by one position to the left to fill the gap left by the removed element, using one for.

Lookup/access: The function needs to go trough all the elements in the array, one by one, using one for.

### Activity 11: Complexity of *append*

A1- O(1)

A2- The average case is O(1) and the worst case is O(n), it differs so much because in the worst case when we append a value, the whole array has to be reallocated.

### Activity 12: Storing grades in a dynamically growing array

```c
Include your program's code here.
```


> Written with [StackEdit](https://stackedit.io/).
