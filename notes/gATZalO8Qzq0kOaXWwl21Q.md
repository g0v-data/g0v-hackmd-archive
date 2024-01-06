# Week 8 - Hashing

## Team

>Members:
>
>- Margarita Konnari, 527941
>- Jiangshan Liu, 539663
>
> Date: *day* *month* 2023

## Activities

Make sure to have the activities signed off regularly to ensure progress is tracked.

Download the provided project and open it in CLion.

### Activity 1: The costs of maintaining order

19 record_pair_t

### Activity 2: Calculate the moduli

| id         | 8609 | 6348 | 4992 | 5839 | 1622 | 5450 | 7198 | 4827 |
| ---------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| **mod 8**  | 1    |  4   |   0  |  7   |   6  |  2   |  6   |  3   |
| **mod 16** | 1    |  12  |   0  |  15  |   6  |  10  |  14  |  11  |
| **mod 17** | 7    |  7   |   11 |  8   |   7  |  10  |  7   |  16  |

There are some modulus that have the same result. This can cost wrong mapping while multiple IDs will have the same index.


### Activity 3: Hash functions

A hash functions are function that take an input (often a string) and returns a fixed-size string of characters, which is typically a hash code or hash value. The purpose of a hash function is to map data of arbitrary size to a fixed-size value, which is typically a numerical index or key in a data structure like an array or hash table.

Properties of a good hash function include:

Deterministic: The same input should always produce the same hash value. This property is essential for consistency.

Uniformity: A good hash function should distribute the hash values uniformly across the entire range of possible hash values. This property helps minimize collisions (two different inputs producing the same hash value), which can degrade the performance of data structures relying on hash functions.

Efficiency: The hash function should be computationally efficient to calculate the hash value for any given input. The time complexity of the hash function should be as low as possible.

Avalanche effect: A small change in the input should produce a significantly different hash value. This property ensures that even similar inputs have distinct hash values, reducing the likelihood of collisions.

Pre-image resistance: Given a hash value, it should be computationally infeasible to determine the original input. This property adds a layer of security and is desirable in cryptographic hash functions.

Examples of hash functions:

MD5 (Message Digest Algorithm 5): MD5 is a widely used hash function that produces a 128-bit hash value. However, MD5 is considered weak for cryptographic purposes due to vulnerabilities.

SHA-1 (Secure Hash Algorithm 1): SHA-1 produces a 160-bit hash value. It was widely used but is now considered insecure for cryptographic applications due to vulnerabilities.

SHA-256 (Secure Hash Algorithm 256-bit): SHA-256 is part of the SHA-2 family and produces a 256-bit hash value. It is widely used and is considered secure for various cryptographic applications.

CRC32 (Cyclic Redundancy Check): CRC32 is a hash function commonly used for error-checking purposes, such as verifying data integrity in network protocols or file checksums. It produces a 32-bit hash value.

A good hash function minimizes collisions, has a low probability of generating the same hash value for different inputs, and efficiently distributes values across the hash space. A bad hash function may produce many collisions, have a high probability of generating the same hash value for different inputs, or exhibit poor distribution of hash values.


### Activity 4: Implement FNV-1a

```c
size_t fnv1a_hash(const char *str) {
    const size_t FNV_PRIME = 0x00000100000001b3;
    const size_t FNV_OFFSET_BASIS = 0xcbf29ce484222325;
    size_t hash = FNV_OFFSET_BASIS; // initialize hash value
    while(*str != '\0') {
        hash ^= (size_t)(*str);
        hash *= FNV_PRIME;
        str++; //next character
    }
    return hash;
}
```

### Activity 5: Case-insensitive string equality

```c
size_t fnv1a_hash(const char *str) {
    const size_t FNV_PRIME = 0x00000100000001b3;
    const size_t FNV_OFFSET_BASIS = 0xcbf29ce484222325;
    size_t hash = FNV_OFFSET_BASIS; // initialize hash value
    while(*str != '\0') {
        char c = tolower(*str);
        hash ^= (size_t)c;
        hash *= FNV_PRIME;
        str++; //next character
    }
    return hash;
}
        
bool str_equals(const char *s1, const char *s2) {
    while ((*s1 != '\0') && (*s2 != '\0')) {
        if (tolower(*s1) != tolower(*s2)) {
            return false;
        }
        s1++;
        s2++;
    }
    return (*s1 == '\0' && *s2 == '\0'); //encure strings end at same position
}
```

### Activity 6: Implement lookup

```c
pair_t * hashmap_lookup(const hashmap_t *map, const void *key) {
    // TODO (Activity 6): find the pair with the given key
    //  - use the hash function to find the slot
    //  - use the equals function to find the pair in the slot
    if(map != NULL){
        size_t hash = map->hash_fun(key) % map->capacity;
        list_t *slot = &map->slots[hash];
        
        node_t *node = slot->head;
        while(node != NULL) {
            pair_t *pair = (pair_t*)node->data;
            if(map->equals_fun(pair->key, key)){
                return pair;
            }
            node = node->next;
        }
    }
    return NULL;
}
```

### Activity 7: Adding and removing keys and values

```c
bool hashmap_add(hashmap_t *map, const void *key, size_t value) {
    // TODO: implement (Activity 7)
    //  - use the hash function to find the slot
    //  - use the equals function to find the pair in the slot
    //  - update the pair's value if it was found,
    //  - prepend the pair to the list if it was not found
    //  - return true if the key was not already in the map, false it was updated
    if(map != NULL){
        size_t hash = map->hash_fun(key) % map->capacity;
        list_t *slot = &map->slots[hash];

        pair_t *pair = hashmap_lookup(map, key);
        if(pair == NULL) { //add
            pair_t *new_pair = (pair_t*)malloc(sizeof(pair_t));//ensures enough memory is allocated
            new_pair->key = key;
            new_pair->value = value;
            list_prepend(slot, new_pair);
            map->count++;
            return true;
        }
        else {//update
            node_t *node = slot->head;
            while(node != NULL){
                pair_t *pair2 = (pair_t*)node->data;
                if(map->equals_fun(pair2->key, key)) { //compare the key of the current pair with the given key
                    pair2->value = value;//updates value with new value
                    return false;
                }
                node = node->next;
            }
        }
    }
    return false;
}

void hashmap_remove(hashmap_t *map, const void *key) {
    // TODO: implement (Activity 7)
    //  - use the hash function to find the slot
    //  - use the equals function to find the pair in the slot
    //  - remove the pair from the slot (use list_remove)
    if(map != NULL){
        size_t hash = map->hash_fun(key) % map->capacity;
        list_t *slot = &map->slots[hash];

        node_t *node = slot->head;
        while(node != NULL) {
            pair_t *pair = (pair_t*)node->data;
            if(map->equals_fun(pair->key, key)){
                list_remove(slot, node);
                free(pair);
                map->count--;
                break;
            }
            node = node->next;
        }
    }
}
```

### Activity 8: Word counting

#### Top 10 words in "alice0.txt"

| word        | frequency |
| ----------- | --------- |
| Dog         |      3    |
| Caterpillar |      29   |
| Cat         |      37   |
| Rabbit      |      53   |


#### Words in slot

How many words are stored in the slot with index 10? 334

#### Empty slots

How many slots are empty? 3

#### Length of longest chain

What is the length of the longest of the 31 linked lists? 490

### Activity 9: Tracking load statistics

| Capacity                     | 4201 | 6101 | 15149 |
| ---------------------------- | ---- | ---- | ----- |
| Items                        | 3352 | 3352 |3352   |
| Load factor                  | 0.80 | 0.55 |0.22   |
| Fraction of free slots       | 0.46 |0.58  |0.80   |
| Slots with more than 0 items | 2288 |2590  |2988   |
| Slots with more than 1 item  |  796 |644   |344    |
| Slots with more than 2 items |  203 |106   |18     |
| Slots with more than 3 items |  39  |11    |11     |
| Slots with more than 4 items |   6  |1     |1      |
| Length of longest chain      |   5  |5     |5      |


### Activity 10: Time complexity

| Operation | Time complexity |
| --------- | --------------- |
| Lookup    | O(1)            |
| Insert    | O(1)            |
| Remove    | O(1)            |

All O(1) because the index in known. 
(hash function determine the index where the key is) 

### Activity 11: Implement rehashing

```c
 void hashmap_rehash(hashmap_t *map, size_t new_capacity) {
    list_t *new_slots = calloc(new_capacity, sizeof(list_t));
    for (size_t i = 0; i < new_capacity; i++) {
        list_init(&new_slots[i]);
    }
    for (size_t i = 0; i < map->capacity; i++) {
        list_t *slotList = &(map->slots[i]);
        node_t *current = slotList->head;
        while (current != NULL) {
            pair_t *pair = (pair_t *) current->data;
            hashmap_add(map, pair->key, pair->value);
            current = current->next;
        }
    }
    for (size_t i = 0; i < map->capacity; i++) {
        list_destroy(&(map->slots[i]));
    }
    free(map->slots);
    map->slots = new_slots;
    map->capacity = new_capacity;
}
```

