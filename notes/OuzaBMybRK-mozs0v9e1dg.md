# Week 6 - Sets

## Team

>Members:
>- Margarita Konnari, 527941
>- Jiangshan Liu, 539663
>
> Date: *day* *month* 2023                                                   |      |

## Activities

Make sure to have the activities signed off regularly to ensure progress is tracked.

Download the provided project and open it in CLion.

### Activity 1: Comparing floating point numbers

```c
bool equals_dbl(double a, double b){
    if(fabs(a-b) <= 0.00000001)
        return true;
    return false;
}
```

### Activity 2: Function pointers

```c
int sum(int a, int b){
    return a + b;
}

int product(int a, int b) {
    return a * b;
}

void fun_with_ints(int (*funptr)(int, int)) {
    (void) funptr;
    for (int r = 1; r <= 15; ++r) {
        for (int c = 1; c <= 15; ++c) {
            // TODO (Activity 2)
            //  call the function, the address of which is sotred in funptr,
            //  and pass in r and c as arguments. Store the result in `result`,
            //  so that the function's result gets printed
            int result = funptr(r, c);
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
    if (!ensure_capacity(set)) return;
    if (!set_contains(set,value)){
        set->count++;
        set->data[set->count] = value;
    }

}

/// Removes a value from a set, if it is present
/// \param set The set to remove the value from
/// \param value The value to remove from the set
void set_remove(set_t * set, double value) {
    size_t index = 0;
    for(size_t i = 0; i < set->count; i++) {
        if(set->data[i] == value)
            index = i;
    }
    for(size_t i = index; i < set->count - 1; i++) {
        set->data[i] = set->data[i+1];
    }
    set->count--;
}

/// Checks if a value is in the set
/// \param set The set to search
/// \param value The value to search for in the set
/// \return true if the value is present, false if it is not
bool set_contains(const set_t * set, double value) {
    for(size_t i = 0; i < set->count; i++) {
        if(set->eq_fun(set->data[i], value))
            return true;
    }
    return false;
}
```

### Activity 4: Time complexity of unsorted set operations

| Operation |     Time complexity   |
|-----------| --------------------- |
| Contains  |        O(n)           |
| Add       |        O(n)           |
| Remove    |        O(n^2)         |

Contains:
The time complexity is O(n) while it goes through all the elements of the set using a for loop. 

Add:
The time complexity is the same as the Contains (O(n)) because it first calls that function and then just add the value at the end. 

Remove:
The time complexity is O(n^2) while it first goes trough the set until it finds the index and then it moves the values (after that index) one place back.

### Activity 5: Binary search

Value to find: 46:

| Binary search step | lo  | hi  | mid |
|--------------------|-----|-----|-----|
| 1                  | 0   | 16  | 8   |
| 2                  | 9   | 16  | 12  |
| 3                  | 13  | 16  | 14  |
| 4                  | 13  | 14  | 13  |
| 5                  |     |     |     |

Value to find: 4:

| Binary search step | lo  | hi  | mid |
|--------------------|-----|-----|-----|
| 1                  | 0   | 16  | 8   |
| 2                  | 0   | 8   | 4   |
| 3                  | 0   | 4   | 2   |
| 4                  | 0   | 2   | 1   |
| 5                  | 0   | 1   |  -  |

### Activity 6: Ordering doubles

```c
int cmp_dbl(double d1, double d2){
    if(fabs(d2-d1)<=0.0000000001)
        return 0;
    else if(d1 > d2)
        return 1;
    return -1;
}
```

### Activity 7: Implementing binary search

```c
size_t set_index_of(const set_t * set, double value) {
    int lo = 0;
    int hi = set->count;
    int mid = lo + ((hi-lo) /2);
    double v;
    if(set-> count > 0){
        v = set->data[mid];
        if (set->cmp_fun(v, value) == -1)
            lo = mid + 1;
        else if(set->cmp_fun(v, value) == 1)
            hi = mid - 1;
        else
            return mid;
        
        mid = lo + (hi - lo) / 2;
    }
}
```


### Activity 8: Binary search - Time complexity

| Array size | Lookups |
|------------|---------|
| 16         | 5       |
| 32         | 6       |
| 64         | 7       |
| 128        | 8       |
| 256        | 9       |
| 1000       |         |
| 4000       |         |
| 10000      |         |
| 1048576    |         |

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
