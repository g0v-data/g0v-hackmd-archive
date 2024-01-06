# Week 1 - Memory

## Team

Date: 15.02.2023

Members:
- Margarita Konnari
- Jiangshan Liu
- Sergiu Ciliuta

## Activities

Make sure to have the activities signed off regularly to ensure progress is tracked.

Set up a project in CLion to write the small programs needed in some of the activities.

### Before you start

In your projects, make sure that the `CMakeLists.txt` file contains the following line, so that potential problems appear in the "Messages" tab:

> text
> target_compile_options(${PROJECT_NAME} PRIVATE -Wall -Wextra -pedantic -Werror)
> 

Make sure to check the messages after building.

### Activity 1: Printing memory addresses - I

Give the memory address ranges of the two arrays, `integers` and `doubles`, in the code listed below.
Explain why these ranges do or do not overlap.

• What are the memory address ranges of both arrays?
These 2 are the memory adress ranges of both arrays:
0x7fffca14ae40 -> 0x7fffca14be3c
0x7fffca149e40 -> 0x7fffca14be38
• Do these memory address ranges overlap?
Yes they do overlap, because after the first function is executed and the first array takes a certain part of memory, a part of that memory gets reallocated to the second array in the second function.
• Does the lifetime of the two arrays overlap? Why (not)?
No, it does not, because they are called in different fuctions and the first array is destroyed after the first function ended which is before the start of the second function.
• How much memory does the program need to store the two arrays?
The program needs 8192 bytes to store the two arrays.

This is how you include code listings in your markdown document:
C
#include <stdio.h>

int sum_ints(void) {
	int integers[1024] = {1};
	for (int i = 1; i < 1024; ++i) integers[i] = integers[i - 1] + 1;
	return integers[1023];
}

double mul_doubles(int init) {
	double doubles[1024] = {init};
	for (int i = 1; i < 1024; ++i) doubles[i] = doubles[i - 1] * 0.999;
	return doubles[1023];
}

int main(void) {
	double result = mul_doubles(sum_ints());
	printf("Result = %lf\n", result);
}

### Activity 2: Printing memory addresses - II


• What are the memory address ranges of both arrays?
0x7fffeb7aa230 -> 0x7fffeb7ab22c
0x7fffeb7a81f0 -> 0x7fffeb7a91ec
0x7fffeb7a9230 -> 0x7fffeb7ab228
• Do these memory address ranges overlap?

• Does the lifetime of the two arrays overlap? Why (not)?
Yes, because the first function is called within the second function.
• How much memory does the program need to store the two arrays?
The program needs 4096 bytes for the first array + 8192 bytes for the second array = 12288 bytes.

C
#include <stdio.h>

int sum_ints(void) {
	int integers[1024] = {1};
	for (int i = 1; i < 1024; ++i) integers[i] = integers[i - 1] + 1;
	return integers[1023];
}

double mul_doubles(int init) {
	double doubles[1024] = {sum_ints()};
	for (int i = 1; i < 1024; ++i) doubles[i] = doubles[i - 1] * 0.999;
	return doubles[1023];
}

int main(void) {
	double result = mul_doubles(sum_ints());
	printf("Result = %lf\n", result);
}


### Activity 3: Using data that is no longer alive

Record the answer to the activity's questions here.
• Which warnings and / or errors does the compiler give when compiling this program?
The error the compiler gives is : error: function returns address of local variable [-Werror=return-local-addr]
• What do these warnings and / or errors mean?
The function create_array returns the address of a local variable (array), which is allocated on the stack and the memory will be depleted when the function returns, this means that pointer values points to values which no longer exist and that causes the program to crash.
• Does this approach to create an array at runtime work? Why (not)?
No, the approach to create an array at runtime does not work correctly because the function creates an array on the stack that will no longer exist after the function has ended.
c
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


### Activity 4: Using malloc

c
#include <stdio.h>
#include <stdlib.h>

int* allocate_memory(int count)
{
    int *arrayOfIntegers = malloc(sizeof(int[count]));
    return arrayOfIntegers;
}


int main(void) {
    int count=10;
    unsigned long *number_pointer = malloc(sizeof(unsigned long) * 1);
    float *floatArray_pointer = malloc(sizeof(float[256]));
    allocate_memory(count);
}

### Activity 5: Allocating zero bytes

• What does the call to malloc return?
The call to malloc returns a valid pointer which is stored in size0, however that pointer points to a block of memory of 0 bytes.
• What happens if you try to store data in the block of memory obtained by malloc (by storing a value at the address that was returned), and why does that happen?
If size is zero, the behavior of malloc is implementation-defined. For example, a null pointer may be returned. Alternatively, a non-null pointer may be returned; but such a pointer should not be dereferenced, and should be passed to free to avoid memory leaks.
• Is it possible to allocate a block of memory that has a negative size?
No, it is not possible to allocate a block of memory that has a negative size. The malloc function takes an argument of type size_t, which is an unsigned integer type. This means that the argument cannot be negative.

c
#include <stdio.h>
#include <stdlib.h>

int main(void) {
    int *size0 = malloc(0);
    *size0 = 100;
}    

### Activity 6: Using allocated memory as an array

• How many int elements can be stored in the block of memory allocated by the
create_array function?
20 elements.
• What happens when you perform an out-of-bounds access to an array that is stored in dynamically allocated memory?
All the elements that are after the bound will be 0.
• What are the problems in the program listed below, and how can they be fixed (Include the fixed program into your logbook)?
1.The create_array() function allocates memory for the array, but it only allocates enough memory to hold capacity bytes, not capacity integers. That means, it hold only 20 bytes instead of 20*4 = 80 bytes.
2.The other problem is that the program starts to acces from 1->20 not from 0->19, like the array is indexed in C.

c
//replaced code
int * create_array(unsigned int capacity) {
    int *ptr =malloc(capacity * sizeof(int));
	return ptr;
}

int main( void ) {
	const int capacity = 20;
	int * array = create_array(capacity);
	for (int i = 0; i < capacity; i++) {
		printf("array[%d] = %d\n", i, array[i]);
	}
}

```c
//old code 
int * create_array(unsigned int capacity) {
	int *ptr = (int*) malloc(capacity);
	return ptr;
}

int main( void ) {
	const int capacity = 20;
	int * array = create_array(capacity);
	for (int i = 1; i <= capacity; i++) {
		printf("array[%zu] = %d\n", i, array[i]);
	}
}


### Activity 7: Fixing a memory leak
c
//new code
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
}


c
//old code
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


### Activity 8: Dangerous `free`s

c
#include <stdio.h>
#include <stdlib.h>

int main(void) {
 int stack_variable = 42;
    int* ptr = &stack_variable;
    free(ptr); // 1. free a variable that has automatic lifetime
    // this behavior can lead to a crash or a memory leak. 
    // the program terminates with an error message

    int* null_ptr = NULL;
    free(null_ptr); // 2. calling free on a pointer that is NULL
    // safe but it does not release any memory
    // because there is no memory allocated for a NULL pointer.   
}


### Activity 9: Using realloc

Record the answer to the activity's questions here.

c
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


### Activity 10: Using a dynamically sized buffer

Download the project for this activity from Blackboard.

Include your code & notes here.

## Looking back

### What we've learnt

Formulate at least one lesson learned.

### What were the surprises

Fill in...

### What problems we've encountered

Fill in...

### What was or still is unclear

Fill in...