# Perfect Partition
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e06c345c31cdda59338d5c2c7f9bb673.png)
## 解題:
```c=
#include <stdio.h>
#include <stdlib.h>
#include<stdbool.h>

#define SUCCESS     0
#define ERR_BASE    0
#define ERR_CANT_PARTITION  ERR_BASE-1
#define ERR_INPUT_ERR       ERR_BASE-2
#define ERR_MALLOC_FAIL     ERR_BASE-3
#define ERR_NULL_PTR        ERR_BASE-4

#define BEGIN_INDEX 0

int count=0;

int main(int argc,char* argv[])
{
    if(argc>3||argc<2)
    {
        printf("Input error\n");
        return ERR_INPUT_ERR;
    }
    int maxM;
    int input=atoi(argv[1]);
    if(argc==3)  maxM=atoi(argv[2]);
    else  maxM=input;
    
    if(maxM>input)
    {
        printf("Error can't partition\n");
        return ERR_CANT_PARTITION;
    }

    int *arr = (int *)malloc(sizeof(int) * input);
    if(!arr)
    {
        printf("Malloc failed");
        return ERR_MALLOC_FAIL;
    }

    for (int i = 0; i < input; i++) //creat 1.2.3...n
    {
        arr[i] = i + 1;
    }

    int **ans = (int **)malloc(sizeof(int *) * input);//creat subset
    if(!ans)
    {
        printf("Malloc failed");
        return ERR_MALLOC_FAIL;
    }

    for (int i = 0; i < input; i++) 
    {
        ans[i] = (int *)malloc(sizeof(int) * input);
        if(!ans[i])
        {
            printf("Malloc failed");
            return ERR_MALLOC_FAIL;
        }
    }
    Partition(arr, BEGIN_INDEX, input, ans, BEGIN_INDEX,maxM);
    printf("%s%d\n","Result Count: ",count);
    
    return SUCCESS;
}
```
### partition()
```c=
int Partition(int *arr, int index, int input, int **ans, int ansIndex,int maxM)
{
    if(!arr||!ans)
    {
        printf("Null ptr pass to Partition()");
        return ERR_NULL_PTR;
    }
    if(ansIndex<=maxM)//check subset number
    {
        if (index == input) //end of input
        {
            printPartition(ans, ansIndex, input);
            return SUCCESS;
        }

        for (int i = 0; i < ansIndex; i++) //from row 0 to ansindex-1 
        { 
            ans[i][index] = arr[index]; //each row put current input
            Partition(arr, index + 1, input, ans, ansIndex,maxM);//go partition to the rest of input
            ans[i][index] = 0;//
        }
        //for chosing set
        if(ansIndex<maxM)
        {
            ans[ansIndex][index] = arr[index];//move down row
            Partition(arr, index + 1, input, ans, ansIndex + 1,maxM);//walk rest input 
            ans[ansIndex][index] = 0;
        }
        
    }
    return SUCCESS;
}
```
### printPartiton()
```c=
int printPartition(int **ans, int rows, int cols)
{
    if(!ans)
    {
        printf("Null ptr pass to Partition()");
        return ERR_NULL_PTR;
    }

    for (int i = 0; i < rows; i++) {
        printf("{");
        for (int j = 0; j < cols; j++)
        {
            if(ans[i][j]!=0) 
            {
                printf("%d", ans[i][j]);
                if(checkBack(ans,cols,i,j+1)) printf(",");
            }
        }
        printf("}");
        if(i!=rows-1) printf(",");
    }
    printf("\n");
    count+=1;
    return SUCCESS;
}
```
### checkBack()
```c=
bool checkBack(int **ans,int input,int rowsId,int closId)
{
     if(!ans)
    {
        printf("Null ptr pass to Partition()");
        return ERR_NULL_PTR;
    }
    for(int j=closId;j<input;j++)
    {
        if(ans[rowsId][j]!=0) return true;
    }
    return false;
}
```
## 學習重點:
