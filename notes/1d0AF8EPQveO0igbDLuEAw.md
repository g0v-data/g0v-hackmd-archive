# Please finish sorted double-linked list (ascending) functions.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_766de1d6784f0ea5923b818aea6a34a9.png)

## 解題:
```c=
#include <stdio.h>
#include <stdlib.h>
#include<stdbool.h>

#define SUCCESS                 0
#define ERR_BASE                0
#define ERR_DUPLICATE       ERR_BASE-1
#define ERR_NOT_FOUND       ERR_BASE-2
#define ERR_OUT_OF_MEM      ERR_BASE-3
#define ERR_OPEN_FAIL       ERR_BASE-4
#define ERR_LOAD_FAIL       ERR_BASE-5
#define ERR_SAVE_FAIL       ERR_BASE-6
#define ERR_WRONG_DIR       ERR_BASE-7
#define ERR_EMPTY_LINKLIST  ERR_BASE-8
#define ERR_MELLOC_FAIL     ERR_BASE-9

#define TYPE_FROM_HEAD  1
#define TYPE_FROM_TAIL  2

int main()
{
    struct doubleLinkList *list=(struct doubleLinkList*)malloc(sizeof(struct doubleLinkList));
    if(!list)
    {
        printf("Error list malloc fail\n");
        return ERR_MELLOC_FAIL;
    }
    add(list,3);
    add(list,5);
    add(list,1);
    add(list,4);
    add(list,2);
    del(list,5);
    del(list,1);
    del(list,3);
    del(list,1);
    dump(list,TYPE_FROM_HEAD);
    dump(list,TYPE_FROM_TAIL);
    if(save("test.txt",list)!=SUCCESS)
    {
        return ERR_SAVE_FAIL;
    }
    clear(list);
    if(load("test.txt",list)!=SUCCESS)
    {
        return ERR_LOAD_FAIL;
    }
    dump(list,TYPE_FROM_TAIL);

    return SUCCESS;
}

```
### add()
```c=
int add(struct doubleLinkList *list,int element)
{
    if(!list)
    {
        printf("ERROR  dblinklist is NULL.\n");
        return  ERR_MELLOC_FAIL;
    }
    
    struct listnode *tmp=(struct listnode*) malloc(sizeof(struct listnode)); //creat a new node
    if(initNode(tmp,element)!=SUCCESS) //initial node and check
    {
        return ERR_MELLOC_FAIL;
    } 

    if(!list->head&&!list->tail) //empty linklist
    {
        initDL(list,tmp);
    }
    else //not empty
    {
        if(list->tail->val<tmp->val)   //tail check
        {
            list->tail->next=tmp;
            tmp->pre=list->tail;
            tmp->next=NULL;
            list->tail=tmp;
        }
        else    //element in the range of current linklist
        {
            struct listnode*ptr=list->head;
            while(ptr)
            {
                if(ptr->val>tmp->val)
                {
                    if(!ptr->pre)
                    {
                        ptr->pre=tmp;
                        tmp->next=ptr;
                        tmp->pre=NULL;
                        list->head=tmp;
                    }
                    else
                    {
                        ptr->pre->next=tmp;
                        tmp->pre=ptr->pre;
                        tmp->next=ptr;
                        ptr->pre=tmp;
                    }
                    break;
                }
                else if(ptr->val==tmp->val)
                {
                    printf("%s","add() Error! element already in list \n");
                    free(tmp);
                    return ERR_DUPLICATE;
                }
                ptr=ptr->next;     
            }
        }
    }

    return SUCCESS; 
}
```
### del()
```c=
int del(struct doubleLinkList *list,int element)
{
    if(!list)
    {
        printf("del() list is null.\n");
        return ERR_MELLOC_FAIL;
    }
    if(!list->head&&!list->tail)
    {
        printf("del() Error linklist is empty\n");
        return  ERR_EMPTY_LINKLIST;
    }
    else
    {
        if(list->tail->val==element)   //bound check
        {
            struct listnode *tmp=list->tail;
            list->tail->pre->next=NULL;
            list->tail=list->tail->pre;
            tmp->pre=NULL;
            free(tmp);
        }
        else    //element in the range of current linklist
        {
            bool find=false;
            struct listnode*ptr=list->head;
            while(ptr)
            {
                if(ptr->val==element)
                {
                    find=true;
                    if(!ptr->pre)// if is head
                    {
                        ptr->next->pre=NULL;
                        list->head=ptr->next;
                        ptr->next=NULL;
                    }
                    else
                    {
                        ptr->pre->next=ptr->next;
                        ptr->next->pre=ptr->pre;
                        ptr->next=NULL;
                        ptr->pre=NULL;
                    }
                    break;
                }
                ptr=ptr->next;
            }
            if(!find)
            {
                printf("%s","del() Error! element not in list can't delete \n");
                return ERR_NOT_FOUND;
            }
            else free(ptr);
        }
    }
    return SUCCESS;
}
```
### dump()
```c=
int dump(struct doubleLinkList *list,int dir)
{
    if(!list)
    {
        printf("dump() list is null.\n");
        return ERR_MELLOC_FAIL;
    }
    if(!list->head&&!list->tail)    //check if linklist is empty
    {
        printf("%s\n","dump() Error linklist is empty\n");
        return  ERR_EMPTY_LINKLIST;
    }
   
    if(dir==TYPE_FROM_HEAD) //print from head
    {
        struct listnode *ptr=list->head;
        while(ptr)
        {
            printf("%d",ptr->val);
            if(ptr!=list->tail)
            {
                printf("%c",',');
            }
            ptr=ptr->next;
        }
        printf("%s","\n");
    }
    else if(dir==TYPE_FROM_TAIL)    //print from tail
    {
        struct listnode *ptr=list->tail;
        while(ptr)
        {
            printf("%d",ptr->val);
            if(ptr!=list->head)
            {
                printf("%c",',');
            }
            ptr=ptr->pre;
        }
        printf("%s","\n");
    }
    else    //input wrong dirction
    {
        printf("%s","Dirction setting wrong.\n");
        return ERR_WRONG_DIR;
    }

    return SUCCESS; 
}
```
### save()
```c=
int save(char* filename,struct doubleLinkList *list)
{
    if(!list)
    {
        printf("save() list is null.\n");
        return ERR_MELLOC_FAIL;
    }

    FILE *fp = fopen(filename, "w");
    if (fp == NULL)
    {
        printf("Error opening the file %s", filename);
        return ERR_OPEN_FAIL;
    }
    struct listnode *ptr=list->head;
    while(ptr)
    {
        fprintf(fp,"%d\n",ptr->val);   
        ptr=ptr->next;
    }

    fclose(fp);
    return SUCCESS;
}
```
### load()
```c=
int load(char* filename,struct doubleLinkList *list)
{
    if(!list)
    {
        printf("load() list is null.\n");
        return ERR_MELLOC_FAIL;
    }

    clear(list);
    FILE *fp  = fopen(filename, "r"); 
    if(fp==NULL)
    {
        printf("Error opening the file %s", filename);
        return ERR_OPEN_FAIL;
    }
    int tmp;
    while (fscanf(fp,"%d\n",&tmp)!=EOF)
    {  
        add(list,tmp);
        //printf ("%d\n", tmp);    
    }
    fclose (fp);   
    return SUCCESS;  
}
```
### clear()
```c=
int clear(struct doubleLinkList *list)
{
    if(!list)
    {
        printf("clear() list is null.\n");
        return ERR_MELLOC_FAIL;
    }
    struct listnode *ptr=list->head;
    while(ptr)
    {
        struct listnode *tmp=ptr->next;
        free(ptr);
        ptr=tmp;
        
    }
    list->head=NULL;
    list->tail=NULL;
    return SUCCESS;
}    
```
## 學習重點:
1. 所有malloc後都要去檢查是否成功
2. 須 #define SUCCESS 以及 ERROR_BASE以利之後大型專案追蹤
3. function比較少會有void，通常會是int方便回傳ERROR Message或SUCCESS
4. 程式盡量去除相似功能的動作
5. 不要有magic number
6. 專案內容須吻合，若有需要甚麼變動須先詢問
7. 確定好需求再開始寫**


