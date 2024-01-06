# Leetcode 203. Remove Linked List Elements
## Solution

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ef27222ea5bd0f8d31fc727eaef9fdf3.png)

```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */

struct ListNode *getIntersectionNode(struct ListNode *headA, struct ListNode *headB) {
    struct ListNode *intersectVal;
    int state = 0; //1:reach short end, 2: both reach end and start to cpr, 3: no match

    static struct ListNode *ptrA;
    ptrA = headA;
    static struct ListNode *ptrB;
    ptrB = headB;

    while(state < 2)
    {
        if ((ptrA->next != NULL) && (ptrB->next != NULL))
        {
            ptrA = ptrA->next;
            ptrB = ptrB->next;
        }
        else if (ptrA->next == NULL)
        {
            ptrA = headB;
            state++;
            if (ptrB->next == NULL)
            {
                ptrB = headA;
                state++;
            }
            else
                ptrB = ptrB->next;
        }
            
        else if (ptrB->next == NULL)
        {
            ptrB = headA;
            state++;
            if (ptrA->next == NULL)
            {
                ptrA = headB;
                state++;
            }
            else
                ptrA = ptrA->next;
        }
            
        
    } 

    while(state == 2)
    {
        if ((ptrA->val == ptrB->val) && (ptrA == ptrB))
        {
            intersectVal = ptrA;
            return intersectVal;
        }
        else if((ptrA->next != NULL) && (ptrB->next != NULL))
        {
            ptrA = ptrA->next;
            ptrB = ptrB->next; 
        }
        else
            state = 3;
    }


    return NULL;
}

```
