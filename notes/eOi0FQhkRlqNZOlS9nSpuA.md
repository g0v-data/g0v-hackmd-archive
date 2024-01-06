# Week 7 - Dictionaries

## Team

>Members:
>- Margarita Konnari, 527941
>- Jiangshan Liu, 539663
>
> Date: *day* *month* 2023                                                   |      |

## Activities

Make sure to have the activities signed off regularly to ensure progress is tracked.

Download the provided project and open it in CLion.

### Activity 1: The ctype header file

isalpha(int c) function returns a non-zero value if the character passed as argument is an alphabetic character, otherwise it returns 0.

islower(int c) function returns a non-zero value if the character passed as argument is a lowercase alphabetic character, otherwise it returns 0.

isupper(int c) function returns a non-zero value if the character passed as argument is an uppercase alphabetic character, otherwise it returns 0.

tolower(int c) function returns the lowercase equivalent of the character passed as argument, if the argument is an uppercase alphabetic character. Otherwise it returns the same character.

toupper(int c) function returns the uppercase equivalent of the character passed as argument, if the argument is a lowercase alphabetic character. Otherwise it returns the same character.

### Activity 2: Count letters in a string

```c
unsigned long countLetters(unsigned long counts[static 26], const char* str) {
    // TODO (Activity 2): implement counting letters
    //  count characters in str, keep counts in the counts array
    //  return the total number of characters in str
    unsigned long count = 0;
    for(int i = 0; str[i] != '\0'; i++){
        char letter = tolower(str[i]);
        if(letter >= 'a' && letter <= 'z') {
            counts[letter - 'a']++;
            count++;
        }
    }
    return count;
}

int main(void){
	unsigned long counts[26] = {0};
	const char* text = "The Quick Brown Fox Jumps Over The Lazy Dog.";
	unsigned long total = countLetters(&counts[0], text);
	assert(35 == total);
	printCounts(&counts[0], false, true);
}
```

### Activity 3: Recognizing languages

```c
const char* makeSignature(unsigned long counts[static 26]) {
    // TODO (Activity 3 - part 1): create a language signature
    //  Return a string with the six most frequently occurring characters,
    //  in descending order of frequency.
    static char buffer[7];
    std::pair<unsigned long, char> letterCounts[26]; // pair array

    for (int i = 0; i < 26; i++) {
        letterCounts[i] = std::make_pair(counts[i], static_cast<char>(i + 'a'));
    }// create pairs

    // sort based on letter counts
    std::sort(letterCounts, letterCounts + 26, std::greater<std::pair<unsigned long, char>>());

    for (int i = 0; i < 6; i++) {
        buffer[i] = letterCounts[i].second;// second value of the pair
    }
    buffer[6] = '\0';  // to make it a valid string

    return buffer;
}

int main(void) {
    unsigned long counts1[26] = {15,3,4,5,16,6,7,8,9,7,6,3,2,11,14,1,2,12,13};
	unsigned long counts2[26] = {16,4,7,5,20,7,4,3,14,5,9,1,2,18,6,12,9,13,9,15};
	assert(strcmp("eaosrn", makeSignature(counts1)) == 0);
	assert(strcmp("enatir", makeSignature(counts2)) == 0);
}
```

| File       | Signature | Language |
| ---------- | --------- | -------- |
| alice0.txt |  etaoin   |   en     |
| alice1.txt |  iantes   |   fi     |
| alice2.txt |  eaionr   |   it     |
| alice3.txt |  enisra   |   de     |

### Activity 4: Find out: dictionaries in other languages

Python:
Dictionary type: dict
1. Insert a key-value pair: my_dict[key] = value
2. Delete a key: del my_dict[key]
3. Check if a key exists: if (key in my_dict){..}
4. Retrieve the value associated with a key: my_dict[key]

C#:
Dictionary type: Dictionary<TKey, TValue>
1. Insert a key-value pair: myDictionary.Add(key, value)
2. Delete a key: myDictionary.Remove(key)
3. Check if a key exists: myDictionary.ContainsKey(key)
4. Retrieve the value associated with a key: myDictionary[key]

JavaScript:
Dictionary type: Object

Java:
Dictionary type: HashMap<KeyType, ValueType>

PHP:
Dictionary Type: array (associative array)


### Activity 5: Generic sorting in C

```c
int compare_strings(const void *a, const void *b){
    const char **str_a = (const char **)a;
    const char **str_b = (const char **)b;

    return strcmp(*str_a, *str_b);
}

int main(void) {
    const char * strings[] = {"Spam", "Cheese", "Knights", "Holy Grail", "Lumberjack", "Ministry", "Swallow",
                              "Silly", "Black Knight", "Camelot", "Coconut", "Parrot", "Shrubbery", "Taunt", "Argument"};

    qsort(strings, (sizeof(strings) / sizeof(strings[0])), sizeof(strings[0]), compare_strings);
    print_string_array(strings, sizeof(strings) / sizeof(strings[0]));
    
    return 0;
}

### Activity 6: Generic searching in C

```c
int main(void) {
    const char * strings[] = {"Spam", "Cheese", "Knights", "Holy Grail", "Lumberjack", "Ministry", "Swallow",
                              "Silly", "Black Knight", "Camelot", "Coconut", "Parrot", "Shrubbery", "Taunt", "Argument"};
                              
     const char* search_strings[] = {"Holy Grail", "Parrot", "Rabbit"};

    for(size_t i = 0; i < sizeof(search_strings)/sizeof(search_strings[0]); i++) {
        const void* needle = search_strings[i];
        const void* haystack = strings;
        size_t item_count = sizeof(strings) / sizeof(strings[0]);
        size_t item_size = sizeof(strings[0]);
        
        bsearch_result_t result = binary_search(needle, haystack, item_count, item_size, compare_strings);
            if(result.found) {
                printf("'%s' found at index %zu\n", search_strings[i], result.index);
            }
            else {
                printf("'%s' not found!\n", search_strings[i]);
            }
        }
    return 0;
}                          
```

### Activity 7: Counter - function implementations

```c
counter_t *counter_init(counter_t *counter, size_t capacity) {
    if(counter != NULL) {
        counter->capacity = capacity;
        counter->data = malloc(sizeof(pair_t) * capacity);
        counter->item_size = sizeof(pair_t);
        counter->cmp_fun = compare_strings;
        counter->count = 0;
    }
    return NULL;
}

const pair_t *counter_get_pair_at(const counter_t *counter, size_t index) {
    return &((pair_t *) counter->data)[index];
}


size_t counter_get_count(const counter_t *counter, const char *string) {
    if(counter != NULL && string != NULL) {
        pair_t *pairs = (pair_t *) counter->data;
        for (size_t i = 0; i < counter->count; ++i) {
            if (counter->cmp_fun(&pairs[i].key, &string) == 0) {
                return pairs[i].value;
            }
        }
    }
    return 0;
}

void counter_increment(counter_t *counter, const char *string) {
    if (counter == NULL || string == NULL) {
        return;
    }
    pair_t *pairs = counter->data;
    for (size_t i = 0; i < counter->count; ++i) {
        if (counter->cmp_fun(&pairs[i].key, &string) == 0) {
            pairs[i].value++;
            return;
        }
    }
    pair_t name = make_pair(string);

    set_add(counter,&name);
}

void counter_destroy(counter_t *counter) {
    internal_pair_t * pairs = (internal_pair_t*) counter->data;
    (void) pairs;
    for(size_t i =0; i < counter->count; i++){
        free(pairs[i].key);
    }

    set_destroy(counter);
}
```

### Activity 8: Find out: function `strtok`

The strtok function is used for tokenizing a string into smaller tokens based on specified separator characters.

```c
void process_line(counter_t* counter, char* line) {
    // separator characters
    //initialize the character pointer with a string of separator characters
    const char* sep = "\t (),.;:?!\"\r\n'_-*"; 
    char* token = strtok(line, sep);
    // as long as token is not NULL
    while (token) {
        //it checks if the length of the token is greater than 0
        if (strlen(token) > 0) process_word(counter, token);//update the word count in the counter structure for the given word
        token = strtok(NULL, sep);
    }
}
```

### Activity 9: How many words?

Alice: 401 times
the: 1691 times
rabbit: 5 times

### Activity 10: Most frequent words

```c
int just_compare(const void* a, const void* b) {
    const pair_t *pairA = (const pair_t*)a;
    const pair_t *pairB = (const pair_t*)b;

    if(pairA->value < pairB->value)
        return -1;
    else if (pairA->value > pairB->value)
        return 1;
    else return 0;
}

void main(void) {
    pair_t *pair = (pair_t *) malloc(counter.count * sizeof(pair_t));
    memcpy(pair, counter.data, counter.count* sizeof(pair_t));
    qsort(pair, counter.count, sizeof(pair_t), just_compare);
    for(size_t i = 0; i < 10; i++){
        printf("Word %s appears %zu times\n", pair[counter.count - i - 1].key, pair[counter.count - i - 1].value);
    }
    counter_destroy(&counter);
    free(pair);
    return 0;
}
```