# Week 8 - Hashing

## Team

>Members:
>
>- Member one
>- Member two
>
> Date: *day* *month* 2023

## Activities

Make sure to have the activities signed off regularly to ensure progress is tracked.

Download the provided project and open it in CLion.

### Activity 1: The costs of maintaining order

19 record_pair_ts


### Activity 2: Calculate the moduli

| id         | 8609 | 6348 | 4992 | 5839 | 1622 | 5450 | 7198 | 4827 |
| ---------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| **mod 8**  | 1    |   4  |   0  |   7  |      |      |      |      |
| **mod 16** | 1    |  12  |   0  |   15 |      |      |      |      |
| **mod 17** | 7    |   7  |  11  |      |      |      |      |      |

### Activity 3: Hash functions

Record your answer here

### Activity 4: Implement FNV-1a

```c
size_t fnv1a_hash(const char *str) {
    const size_t FNV_PRIME = 0x00000100000001b3;
    const size_t FNV_OFFSET_BASIS = 0xcbf29ce484222325;
    (void) str;
    // TODO: implement the FNV-1a hash function
}
```

### Activity 5: Case-insensitive string equality

```c
bool str_equals(const char *s1, const char *s2) {
    return false;
}
```

### Activity 6: Implement lookup

```c
```

### Activity 7: Adding and removing keys and values

```c
bool hashmap_add(hashmap_t *map, const void *key, size_t value) {
	(void) map;
	(void) key;
	(void) value;
	// TODO: implement (Activity 7)
    //  - use the hash function to find the slot
    //  - use the equals function to find the pair in the slot
    //  - update the pair's value if it was found,
	//  - prepend the pair to the list if it was not found
	//  - return true if the key was not already in the map, false it was updated
    return true;
}

void hashmap_remove(hashmap_t *map, const void *key) {
    (void) map;
    (void) key;
    // TODO: implement (Activity 7)
    //  - use the hash function to find the slot
    //  - use the equals function to find the pair in the slot
    //  - remove the pair from the slot (use list_remove)
}
```

### Activity 8: Word counting

#### Top 10 words in "alice0.txt"

| word        | frequency |
| ----------- | --------- |
| Dog         |           |
| Caterpillar |           |
| Cat         |           |
| Rabbit      |           |

#### Frequencies of the following words

| word    | frequency |
| ------- | --------- |
|         |           |
|         |           |
|         |           |
|         |           |

#### Words in slot

How many words are stored in the slot with index 10?

#### Empty slots

How many slots are empty?

#### Length of longest chain

What is the length of the longest of the 31 linked lists?

### Activity 9: Tracking load statistics

| Capacity                     | 4201 | 6101 | 15149 |
| ---------------------------- | ---- | ---- | ----- |
| Items                        | 3352 |      |       |
| Load factor                  | 0.80 |      |       |
| Fraction of free slots       | 0.46 |      |       |
| Slots with more than 0 items | 2288 |      |       |
| Slots with more than 1 item  |  796 |      |       |
| Slots with more than 2 items |      |      |       |
| Slots with more than 3 items |      |      |       |
| Slots with more than 4 items |      |      |       |
| Length of longest chain      |      |      |       |

Capacity smaller than 200000 for which no slot has more than one word stored after processing "alice0.txt":

### Activity 10: Time complexity

| Operation | Time complexity |
| --------- | --------------- |
| Lookup    | O(...)          |
| Insert    | O(...)          |
| Remove    | O(...)          |

### Activity 11: Implement rehashing

```c
void hashmap_rehash(hashmap_t *map, size_t new_capacity) {
    // TODO: implement (Activity 10)
    //  1. Allocate memory for the new slots
    //  2. Initialize the new slots to empty lists
    //  3. Rehash the items from the old slots into the new slots
    //  4. Free the old slots

    // allocate memory for the new slots
}
```

