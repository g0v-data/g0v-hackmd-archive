# Week 6 - Sets

## Team

>Members:
>
>- Member one
>- Member two
>
> Date: *day* *month* 2023                                                   |      |

## Activities

Make sure to have the activities signed off regularly to ensure progress is tracked.

Download the provided project and open it in CLion.

### Activity 1: Comparing floating point numbers

```c
bool equals_dbl(double a, double b) {
    if(fabs(a-b) <= 0.0000000000001)
     return true;
     else
     return false;
}
```

### Activity 2: Function pointers

```c
void fun_with_ints(int (*funptr)(int, int)) {
    (void) funptr;
    for (int r = 1; r <= 15; ++r) {
        for (int c = 1; c <= 15; ++c) {
            // TODO (Activity 2)
            //  call the function, the address of which is sotred in funptr,
            //  and pass in r and c as arguments. Store the result in `result`,
            //  so that the function's result gets printed
            int result = 0;
            printf(" %5d", result);
        }
        printf("\n");
    }
    printf("\n\n");
}
```


### Activity 3: Function implementations

```c
/// Adds a value to a set, if it is not already present
/// \param set The set to add the value to
/// \param value The value to add to the set
void set_add(set_t * set, double value) {

}

/// Removes a value from a set, if it is present
/// \param set The set to remove the value from
/// \param value The value to remove from the set
void set_remove(set_t * set, double value) {

}

/// Checks if a value is in the set
/// \param set The set to search
/// \param value The value to search for in the set
/// \return true if the value is present, false if it is not
bool set_contains(const set_t * set, double value) {

}
```

### Activity 4: Time complexity of unsorted set operations

| Operation | Time complexity |
|-----------| --------------- |
| Contains  |                |
| Add       |                 |
| Remove    |                 |

Record your answer here

### Activity 5: Binary search

Value to find: 46:

| Binary search step | lo  | hi  | mid |
|--------------------|-----|-----|-----|
| 1                  | 0   | 16  | 8  |
| 2                  |     |     |     |
| 3                  |     |     |     |
| 4                  |     |     |     |
| 5                  |     |     |     |

Value to find: 4:

| Binary search step | lo  | hi  | mid |
|--------------------|-----|-----|-----|
| 1                  | 0   | 16  | 8  |
| 2                  |     |     |     |
| 3                  |     |     |     |
| 4                  |     |     |     |
| 5                  |     |     |     |

### Activity 6: Ordering doubles

```c
int cmp_dbl(double d1, double d2) {

}
```

### Activity 7: Implementing binary search

```c
size_t set_index_of(const set_t * set, double value) {
}
```

Record your answer here

### Activity 8: Binary search - Time complexity

| Array size | Lookups |
|------------|---------|
| 16         | 5       |
| 32         |         |
| 64         |         |
| 128        |         |
| 256        |         |
| 1000       |         |
| 4000       |         |
| 10000      |         |
| 1048576    |         |

Record your answer here


### Activity 9: Finalizing the sorted array

```c
/// Adds a value to a set, if it is not already present
/// \param set The set to add the value to
/// \param value The value to add to the set
void set_add(set_t * set, double value) {

}

/// Removes a value from a set, if it is present
/// \param set The set to remove the value from
/// \param value The value to remove from the set
void set_remove(set_t * set, double value) {

}

/// Checks if a value is in the set
/// \param set The set to search
/// \param value The value to search for in the set
/// \return true if the value is present, false if it is not
bool set_contains(const set_t * set, double value) {

}
```

Record your answer here

### Activity 10: Time complexity of the sorted set

| Operation | Time complexity |
|-----------| --------------- |
| Add       |                 |
| Remove    |                 |
| Contains  |                 |

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

