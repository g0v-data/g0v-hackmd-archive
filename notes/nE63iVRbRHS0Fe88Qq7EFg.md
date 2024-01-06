
``` c=

#define OCR0A //  have to know the addr of this reg // init as 0b00000000
#define OCR0B //  have to know the addr of this reg // init as 0b00000000
#define TCCR0A //  have to know the addr of this reg // init as 0b00000000
#define TCCR0B //  have to know the addr of this reg // init as 0b00000000

// dutyCyclePercentage: 1~99
// frequencyInHz: 1~16000000

void outputClockviaPWM(int dutyCyclePercentage, int frequencyInHz){
    
    if (dutyCyclePercentage == 0){return;}
    if (dutyCyclePercentage == 100){return;}
    if (frequencyInHz == 0){return;}
    
    int f_ratio = frequencyInHz/16000000;
    
    if (f_ratio/8 < 256) {
	    OCR0A |= f_ratio/8;
        OCR0B |= f_ratio/8 * dutyCyclePercentage / 100;
	    TRRR0B |= (0b00001000 | 0b00000010);
    } else if (f_ratio/64 < 256) {
	    OCR0A |= f_ratio/64;
        OCR0B |= (f_ratio/64 * dutyCyclePercentage / 100;
	    TRRR0B |= (0b00001000 | 0b00000011);
    } else if (f_ratio/256 < 256) {
	    OCR0A |= f_ratio/256;
        OCR0B |= f_ratio/256 * dutyCyclePercentage / 100;
	    TRRR0B |= (0b00001000 | 0b00000100);
    } else {
        OCR0A |= f_ratio/1024;
        OCR0B |= f_ratio/1024 * dutyCyclePercentage / 100;
	    TRRR0B |= (0b00001000 | 0b00000101);
    }
    
    
    TCCR0A |= 0b00100011;
    
    return;
}
```

