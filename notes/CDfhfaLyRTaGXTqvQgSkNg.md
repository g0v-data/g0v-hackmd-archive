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

Record your answer here

### Activity 2: Count letters in a string

```c
unsigned long countLetters(unsigned long counts[static 26], const char* str) {
    ...
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
    ...
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
| alice0.txt |           |          |
| alice1.txt |           |          |
| alice2.txt |           |          |
| alice3.txt |           |          |

### Activity 4: Find out: dictionaries in other languages

Record your answer here

### Activity 5: Generic sorting in C

```c
int main(void) {
    const char * strings[] = {"Spam", "Cheese", "Knights", "Holy Grail", "Lumberjack", "Ministry", "Swallow",
                              "Silly", "Black Knight", "Camelot", "Coconut", "Parrot", "Shrubbery", "Taunt", "Argument"};
	return 0;
}
```
### Activity 6: Generic searching in C

```c
int main(void) {
    const char * strings[] = {"Spam", "Cheese", "Knights", "Holy Grail", "Lumberjack", "Ministry", "Swallow",
                              "Silly", "Black Knight", "Camelot", "Coconut", "Parrot", "Shrubbery", "Taunt", "Argument"};
	return 0;
}
```

Record your answer here

### Activity 7: Counter - function implementations

```c
counter_t *counter_init(counter_t *counter, size_t capacity) {
}

const pair_t *counter_get_pair_at(const counter_t *counter, size_t index) {
}

size_t counter_get_count(const counter_t *counter, const char *string) {
}

void counter_increment(counter_t *counter, const char *string) {
}

void counter_destroy(counter_t *counter) {
}
```

### Activity 8: Find out: function `strtok`

Record your answer here

### Activity 9: How many words?

Record your answer here

### Activity 10: Most frequent words

```c
int main(void) {

}
```

