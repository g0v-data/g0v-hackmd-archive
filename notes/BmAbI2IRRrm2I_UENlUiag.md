# Week 1 - Memory

## Team

Date:

Members:
- Margarita Konnari,527941
- Jiangshan Liu,539663
- Sergiu Ciliuta,541213

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

This is how you include code listings in your markdown document:

*What are the memory address ranges of both arrays?
The integer's memory address range is from 0x7ffda7f1be40 until 0x7ffda7f1ce3c and the double's memory address range is from 0x7ffda7f1ae40 until 0x7ffda7f1ce38.
*Do these memory address ranges overlap?
This ranges do ovelap because the begenning of the integer's memory adress is at some point common as the double's.
*Does the lifetime of the two arrays overlap? Why (not)?
No, it does not, because they are called in different fuctions and the first array is destroyed after the first function ended which is before the start of the second function.
*How much memory does the program need to store the two arrays?
The program needs 8192(1024*8) bytes to store the two arrays.
```C
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
```

### Activity 2: Printing memory addresses - II

The integer's memory address range is from 0x7ffda7f1be40 until 0x7ffda7f1ce3c and the double's memory address range is from 0x7ffda7f1ae40 until 0x7ffda7f1ce38.

```C
#include <stdio.h>

int sum_ints(void) {
	int integers[1024] = {1};
	for (int i = 1; i < 1024; ++i) integers[i] = integers[i - 1] + 1;
	return integers[1023];
}

double mul_doubles(void) {
	double doubles[1024] = {sum_ints()};
	for (int i = 1; i < 1024; ++i) doubles[i] = doubles[i - 1] * 0.999;
	return doubles[1023];
}

int main(void) {
	double result = mul_doubles();
	printf("Result = %lf\n", result);
}
```


### Activity 3: Using data that is no longer alive

Record the answer to the activity's questions here.

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

### Activity 5: Allocating zero bytes

Record the answer to the activity's questions here.

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

### Activity 7: Fixing a memory leak

Record the answer to the activity's questions here.

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

### Activity 8: Dangerous `free`s

Record the answer to the activity's questions here.

### Activity 9: Using realloc

Record the answer to the activity's questions here.

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


