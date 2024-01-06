# Week 1 - Memory

## Team

Date:

Members:
- Margarita Konnari, 527941
- Jiangshan Liu, 539663

## Activities

Make sure to have the activities signed off regularly to ensure progress is tracked.

Set up a project in CLion to write the small programs needed in some of the activities.

### Before you start

In your projects, make sure that the `CMakeLists.txt` file contains the following line, so that potential problems appear in the "Messages" tab:

> ```text
> target_compile_options(${PROJECT_NAME} PRIVATE -Wall -Wextra -pedantic -Werror)
> ```

Make sure to check the messages after building.

### Activity 1: Printing memory addresses - I

Give the memory address ranges of the two arrays, `integers` and `doubles`, in the code listed below.
Explain why these ranges do or do not overlap.

1:
For the first memory it ranges from 0000007c931fec70 to 0000007c931ffc70
For the second memory it ranges from 0000007c931fdc70 to 0000007c931ffc70

2:
Yes, we can observe that the last memory address are the same for both arrays.

3:
No, after the function returns something it is being emptieed right after it so when the second function it's being runned, the addresses are "empty".

4:
First function needs 4096 (int:4bytes 1024*4)and the second needs 8192(double: 8 bytes 1024*8), so in total 12,288.


This is how you include code listings in your markdown document:
```C
#include <stdio.h>

int sum_ints(void) {
	int integers[1024] = {1};
	for (int i = 1; i < 1024; ++i) integers[i] = integers[i - 1] + 1;
    printf("The size of the array is %zu, and it's memory ranges from %p to %p \n", sizeof(integers), &integers[0], &integers[1023]);
	return integers[1023];
}

double mul_doubles(int init) {
	double doubles[1024] = {init};
	for (int i = 1; i < 1024; ++i) doubles[i] = doubles[i - 1] * 0.999;
    printf("The size of the array is %zu, and it's memory ranges from %p to %p \n" ,sizeof(doubles), &doubles[0], &doubles[1023]);
	return doubles[1023];
}

int main(void) {
	double result = mul_doubles(sum_ints());
	printf("Result = %lf\n", result);
}
```

### Activity 2: Printing memory addresses - II

Record the answer to the activity's questions here.

1:
For the first memory it ranges from 0000005af65fca80 to 0000005af65fda7c
For the second memory it ranges from 0000005af65fdad0 to 0000005af65ffac8

2:
No. They don't have common address range.

3:
Yes, because the first function it's being called in the second one, so both functions run at the same time.

4:
First function needs 4096 and the second needs 8192, so in total 12,288.

```C
#include <stdio.h>

int sum_ints(void) {
    int integers[1024] = {1};
    for (int i = 1; i < 1024; ++i) integers[i] = integers[i - 1] + 1;
    printf("The size of the array is %zu, and it's memory ranges from %p to %p \n", sizeof(integers), &integers[0], &integers[1023]);
    return integers[1023];
}

double mul_doubles(void) {
    double doubles[1024] = {sum_ints()};
    for (int i = 1; i < 1024; ++i) doubles[i] = doubles[i - 1] * 0.999;
    printf("The size of the array is %zu, and it's memory ranges from %p to %p \n" ,sizeof(doubles), &doubles[0], &doubles[1023]);
    return doubles[1023];
}

int main(void) {
    double result = mul_doubles();
    printf("Result = %lf\n", result);
}
```


### Activity 3: Using data that is no longer alive

Record the answer to the activity's questions here.

1:
error: function returns address of local variable [-Werror=return-local-addr]

2:
The function returns a pointer that points to a memory adress which no longer exist.

3:
No, because the array is not created in the main but in the create_array function which after will be gone.

```c
#include <stdio.h>

int * create_array(void) {
	int array[10];
	return array;
}

void print_array(int values[], size_t size) {
	printf("[%d", values[0]);
	for (size_t i = 1; i < size; ++i) printf(", %d", values[i]);
	printf("]\n");
}

int main(void) {
	int * values = create_array();
	for (int i = 0; i < 10; ++i) values[i] = i + 1;
	print_array(values, 10);
}
```

### Activity 4: Using malloc

Record the answer to the activity's questions here.
```c
#include <stdio.h>
#include <stdlib.h>

int* allocate_memory(int count){
    int* location = (int*) malloc(count*sizeof(int[count]));
    return location;
}

int main(void){
    unsigned long* number;
    float* numbers;
    number1 = (unsigned long*) malloc(1*sizeof(unsigned long));  //sizeof(unsigned long[1])
    number2 = (float*) malloc(256 * sizeof(float));     //sizeof(float[256)

    printf("%p \n %p \n", &number1[0], &number2[0]);

    int* location = allocate_memory(16); //16 for testing
    printf("The allocated memory for COUNT ints is: %p", &location);
    return 0;
}
```
### Activity 5: Allocating zero bytes

Record the answer to the activity's questions here.
1:
Returns a pointer whitch points to a block of memory.
2:
If the memory size is 0 then it might return a null pointer.
3:
You can't even have a negative memory size.1

### Activity 6: Using allocated memory as an array

Record the answer to the activity's questions here.

```c
int * create_array(size_t capacity) {
	int *ptr = (int*) malloc(capacity);
	return ptr;
}

int main( void ) {
	const size_t capacity = 24;
	int * array = create_array(capacity);
	for (size_t i = 1; i <= capacity; i++) array[i] = 42;
	for (size_t i = 1; i <= capacity; i++) {
		printf("array[%zu] = %d\n", i, array[i]);
	}
}
```
1: 
std::cout << sizeof(int);  // 24/4=6
2:
You are accesing memory that has not been allocated.
3:
The programm was using malloc(capacity) and it was allocating memory for 'capacity' bytes, but we were needed to use malloc(capacity * sizeof(int)) so the program could allocate memory for the entire array.

```c
#include <stdio.h>
#include <stdlib.h>

int * create_array(size_t capacity) {
    int *ptr = (int*) malloc(capacity * sizeof(int));
    return ptr;
    }

 int main( void ) {
    const size_t capacity = 24;
    int * array = create_array(capacity);

     for (size_t i = 1; i <= capacity; i++) array[i] = 42;

     for (size_t i = 1; i <= capacity; i++) {
        printf("array[%zu] = %d\n", i, array[i]);
    }
     return 0;
}
```

### Activity 7: Fixing a memory leak

```c
#include <stdio.h>
#include <stdlib.h>

int main(void) {
	const int size = 1024 * 1024;
	for (int i = 0; i < size; ++i) {
		int * ptr = (int*) malloc(sizeof(int[size]));
		if (ptr != NULL) ptr[0] = 0;
	}
	puts("All done!");
}
```
Answer:
We used the free to de-allocate the dynamic memory.
```c
#include <stdio.h>
#include <stdlib.h>

int main(void) {
    const int size = 1024 * 1024;
    for (int i = 0; i < size; ++i) {
        int * ptr = (int*) malloc(sizeof(int[size]));
        if (ptr != NULL) ptr[0] = 0;
        free(ptr);
    }
    puts("All done!");
    return 0;
}
```
### Activity 8: Dangerous `free`s

```c
#include <stdio.h>
#include <stdlib.h>

int main(void) {
    int stack_variable = 42;
    int* ptr = &stack_variable;
    free(ptr); 

    int* null_ptr = NULL;
    free(null_ptr); 
    return 0;
}
```
1:
We got a warning that says "'free' called on unallocated object".
2:
No eerors!The function first checks whether the pointer is null.


### Activity 9: Using realloc

```c
int main( void ) {
	float *grades = NULL;
	size_t capacity = 1024;
	for (int count = 0; count < 10000; capacity += 1024, ++count) {
		float *new_grades = (float*)realloc(grades, sizeof(float[capacity]));
		if (new_grades != NULL){
			grades = new_grades;
		}
	}
}
```

Answer:
The memory reallocated 9764 times.
```c
#include <stdlib.h>
#include<stdio.h>

int main(void){
    int longer = 0; 
    int reallocated=0;
    float *grades = NULL;
    size_t capacity = 1024;
    for (int count = 0; count < 10000; capacity += 1024, ++count) {
        
        size_t old_begining = (size_t)&grades[0];
        size_t old_end = (size_t)&grades[capacity - 1024];
        
        float *new_grades = (float*)realloc(grades, sizeof(float[capacity]));
        if (new_grades != NULL){
            grades = new_grades;
        }
        size_t new_begining = (size_t)&grades[0];
        size_t new_end = (size_t)&grades[capacity];
        
        if(old_begining == new_begining && old_end != new_end)
            longer++;
        if(old_begining != new_begining && old_end != new_end)
            reallocated++;
    }
}
    return 0;
}
```
### Activity 10: Using a dynamically sized buffer
```c

#include <stdio.h>      // for printf, fopen, fgetc
#include <stdlib.h>     // for realloc & free
#include <assert.h>     // for assert

/*
 * Reads the file "E.coli.txt" into a dynamically allocated array
 */
int main( void ) {
    char *ptr = NULL; // the memory address of the array
    size_t capacity = 20; // the capacity of the array
    size_t count = 0; // the number of actual values stored in the array

    ptr = realloc(ptr, sizeof(char[capacity])); // allocate memory
    if (ptr == NULL){ // check if allocation worked
        fprintf(stderr, "Memory allocation failed\n");
        return 1;
    }

    // open the file "E.coli.txt" for reading in text mode
    FILE *file = fopen("E.coli.txt", "r");

    if (file == NULL) { // check if file was opened
        fprintf(stderr, "Error opening file\n");
        return 1;
    }

    int c = fgetc(file); // read next character from file
    while (c != EOF) {
        if(count == capacity){
            capacity *= 1.1;
            char * ptr_ = realloc(ptr, sizeof(char[capacity]));
            
            if(ptr_ == NULL){
                free(ptr);
                printf("Pointer is NULL");
                return 1;
            }
            else{
                ptr = ptr_;
            }
        }
        /* TODO: re-allocate memory pointed to by ptr if count == capacity
        *  TODO: check if the pointer returned by realloc is not NULL
        */

        ptr[count++] = (char) c; // store current character, then increase count
        c = fgetc(file); // read next character from file
    }

    // count how many 'a's are in the file
    int freq = 0;
    for (size_t i = 0; i < count; ++i) if (ptr[i] == 'a') freq++;

    printf("Character 'a' appears %d times in the array - this should be 1142069\n", freq);

    // let the program crash if the frequency is not correct
    assert(freq == 1142069);

    free(ptr); // release the memory
}

```

