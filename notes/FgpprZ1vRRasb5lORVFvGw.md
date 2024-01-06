### A~Z

```c=
#define _CRT_SECURE_NO_WARNINGS
#include<stdio.h>
#include<stdlib.h>
#include<math.h>
#include <time.h>
void main(){
    srand( time(NULL) );
    int row, col;
    int no_space = 0;
    int next_pos = 0;
char stop_letter;
char m[11][11];

for(int i = 0; i < 10; i++){
for(int j = 0; j < 10; j++){
            m[i][j] = '.';
}
}

    //initial the position
row = rand() % 10;
col = rand() % 10;
m[row][col] = 'A';

    // 0:up 1:down 2:left 3:right
    for( char i = 'B'; i <= 'Z'; i++){

int move = rand() % 4;

if(move == 0){
    if(row - 1 >= 0 && m[row - 1][col] == '.'){
            m[row - 1][col] = i;
    row--;
            }
            else{
next_pos++;
    no_space++;
            }

        if(row + 1 <= 9 && m[row + 1][col] == '.' && next_pos == 1){
        m[row + 1][col] = i;
            row++;
            }
            else{
               next_pos++;
               no_space++;
            }

            if(col - 1 >= 0 && m[row][col - 1] == '.' && next_pos == 2){
               m[row][col - 1] = i;
               col--;
            }
            else{
               next_pos++;
               no_space++;
            }

            if(col + 1 <= 9 && m[row][col + 1] == '.' && next_pos == 3){
               m[row][col + 1] = i;
               col++;
            }
            else{
               next_pos++;
               no_space++;
            }
      }

      if(move == 1){          
            if(row + 1 <= 9 && m[row + 1][col] == '.'){
               m[row + 1][col] = i;
               row++;
            }
            else{
               next_pos++;
               no_space++;
            }

            if(row - 1 >= 0 && m[row - 1][col] == '.' && next_pos == 1){
               m[row - 1][col] = i;
               row--;
            }
            else{
               next_pos++;
               no_space++;
            }

            if(col - 1 >= 0 && m[row][col - 1] == '.' && next_pos == 2){
               m[row][col - 1] = i;
               col--;
            }
            else{
               next_pos++;
               no_space++;
            }

            if(col + 1 <= 9 && m[row][col + 1] == '.' && next_pos == 3){
               m[row][col + 1] = i;
               col++;
            }
            else{
               next_pos++;
               no_space++;
            }
      }

      if(move == 2){            
            if(col - 1 >= 0 && m[row][col - 1] == '.' ){
               m[row][col - 1] = i;
               col--;
            }
            else{
               next_pos++;
               no_space++;
            }

            if(col + 1 <= 9 && m[row][col + 1] == '.' && next_pos == 1){
               m[row][col + 1] = i;
               col++;
            }
            else{
               next_pos++;
               no_space++;
            }

            if(row - 1 >= 0 && m[row - 1][col] == '.' && next_pos == 2){
               m[row - 1][col] = i;
               row--;
            }
            else{
               next_pos++;
               no_space++;
            }

            if(row + 1 <= 9 && m[row + 1][col] == '.' && next_pos == 3){
               m[row + 1][col] = i;
               row++;
            }
            else{
               next_pos++;
               no_space++;
            }
      }

    if(move == 3){            
            if(col + 1 <= 9 && m[row][col + 1] == '.' ){
            m[row][col + 1] = i;
            col++;
            }
            else{
            next_pos++;
            no_space++;
            }  

            if(col - 1 >= 0 && m[row][col - 1] == '.' && next_pos == 1){
            m[row][col - 1] = i;
            col--;
            }
            else{
            next_pos++;
            no_space++;
            }

            if(row - 1 >= 0 && m[row - 1][col] == '.' && next_pos == 2){
            m[row - 1][col] = i;
            row--;
            }
            else{
            next_pos++;
            no_space++;
            }

            if(row + 1 <= 9 && m[row + 1][col] == '.' && next_pos == 3){
            m[row + 1][col] = i;
            row++;
            }
            else{
            next_pos++;
            no_space++;
            }
    }

    if(no_space == 4){
        stop_letter = i;
            break;
    }
    next_pos = 0;
    no_space = 0;
}

for(int i = 0; i < 10; i++){
    for(int j = 0; j < 10; j++){
            printf("%c", m[i][j]);
}
printf("\n");
}
if(no_space == 4){
    printf("No space for %c\n", stop_letter);
}
else
printf("Completed all letters\n");
}
```