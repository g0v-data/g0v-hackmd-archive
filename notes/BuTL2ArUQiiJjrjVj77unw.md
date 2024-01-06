# Week 6 - Sets

## Team

>Members:
>
>- Margarita
>- Kiki
>
> Date:

## Activities

Make sure to have the activities signed off regularly to ensure progress is tracked.

Download the provided project and open it in CLion.

### Activity 1: Comparing floating point numbers

```c
bool equals_dbl(double a, double b) {
    if(fabs(a-b) <= 0.0000000000001) return true;
    return false;
}
```

### Activity 2: Function pointers

```c
int sum(int a, int b) {
    return a + b;
}

int mul(int a, int b) {
    return a * b;
}

void fun_with_ints(int (*funptr)(int, int)) {
    (void) funptr;
    for (int r = 1; r <= 15; ++r) {
        for (int c = 1; c <= 15; ++c) {
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
    if(!set_contains(set,value)){
        set->data[set->count] = value;
        set->count++;
    }
}

/// Removes a value from a set, if it is present
/// \param set The set to remove the value from
/// \param value The value to remove from the set
void set_remove(set_t * set, double value) {
    for(size_t i = 0; i < set->count; i++)
        if(set->eq_fun(set->data[i],value)) {
            for(size_t j = i; j < set->count - 1; j++)
                set->data[j] = set->data[j + 1];
            set->count--;
            break;
        }
}

/// Checks if a value is in the set
/// \param set The set to search
/// \param value The value to search for in the set
/// \return true if the value is present, false if it is not
bool set_contains(const set_t * set, double value) {
    for(size_t i = 0; i < set->count; i++)
        if(set->eq_fun(set->data[i],value))return true;
    return false;
}
```

### Activity 4: Time complexity of unsorted set operations

| Operation |     Time complexity   |
|-----------| --------------------- |
| Contains  |        O(n)           |
| Add       |        O(n)           |
| Remove    |        O(n^2)         |

Contains is O(n) because it goes trough all of the set using a for.
Add is O(n) because it just adds a value at the end, after calling contain which is O(n).
Remove is O(n^2) because it goes trough the set basically one time, it iterates until it finds the index, and then resumes moving all the carachters.

Record your answer here

### Activity 5: Binary search

Value to find: 46:

| Binary search step | lo  | hi  | mid |
|--------------------|-----|-----|-----|
| 1                  | 0   | 15  | 7   |
| 2                  | 7   | 15  | 11  |
| 3                  | 11  | 15  | 13  |
| 4                  |     |     |     |
| 5                  |     |     |     |

Value to find: 4:

| Binary search step | lo  | hi  | mid |
|--------------------|-----|-----|-----|
| 1                  | 0   | 15  | 7   |
| 2                  | 0   | 7   | 3   |
| 3                  | 0   | 3   | 1   |
| 4                  |     |     |     |
| 5                  |     |     |     |


### Activity 6: Ordering doubles

```c
int cmp_dbl(double d1, double d2) {
    if(fabs(d1-d2) <= 0.0000000000001)return 0;
    else if(d1-d2 > 0.0000000000001)return 1;
    else return -1;
}
```

### Activity 7: Implementing binary search

```c
size_t set_index_of(const set_t * set, double value) {
    int lo = 0, hi = set->count - 1, mid = lo + (hi - lo) / 2;
    if(set->count > 0) {
        double v = set->data[mid];
        while (lo <= hi) {

            if (set->cmp_fun(v, value) == -1) lo = mid + 1;
            else if (set->cmp_fun(v, value) == 1) hi = mid - 1;
            else return mid;

            mid = lo + (hi - lo) / 2;
            v = set->data[mid];
        }
    }
    return mid;
}
```

Record your answer here

### Activity 8: Binary search - Time complexity

| Array size | Lookups |
|------------|---------|
| 16         | 5       |
| 32         | 6       |
| 64         | 7       |
| 128        | 8       |
| 256        | 9       |
| 1000       | 10      |
| 4000       | 12      |
| 10000      | 14      |
| 1048576    | 20      |

Record your answer here


### Activity 9: Finalizing the sorted array

```c
/// Adds a value to a set, if it is not already present
/// \param set The set to add the value to
/// \param value The value to add to the set
void set_add(set_t * set, double value) {
    if (!ensure_capacity(set)) return;
    if(!set_contains(set,value)) {
        size_t index = set_index_of(set, value);
        set->count++;
        if(set->count != 1) {
            for (size_t i = set->count - 1; i > index; i--)
                set->data[i] = set->data[i - 1];
        }
        set->data[index] = value;
    }
}

/// Removes a value from a set, if it is present
/// \param set The set to remove the value from
/// \param value The value to remove from the set
void set_remove(set_t * set, double value) {
    if(set_contains(set,value)) {
        size_t index = set_index_of(set, value);
        for (size_t i = index; i < set->count - 1; i++)
            set->data[i] = set->data[i + 1];
        set->count--;
    }
}

/// Checks if a value is in the set
/// \param set The set to search
/// \param value The value to search for in the set
/// \return true if the value is present, false if it is not
bool set_contains(const set_t * set, double value) {
    if(set->cmp_fun(set->data[set_index_of(set,value)],value) == 0)return true;
    return false;
}
```

Record your answer here

### Activity 10: Time complexity of the sorted set

| Operation | Time complexity |
|-----------| --------------- |
| Add       |  O(n)           |
| Remove    |  O(n)           |
| Contains  |  O(log n)       |

set_add and set_remove are O(n) because, in the worst case, they have to shift all elements when they add/remove.
Contains is O(log n) because the function uses binary search to find the index of the value in the sorted array, and binary search has a worst-case time complexity of O(log n).


