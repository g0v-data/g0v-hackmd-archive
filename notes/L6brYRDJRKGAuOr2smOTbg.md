**Ch-1 遞迴 Recursion**
將大問題變成小問題，本質仍不變，最後解決問題，優點是精簡且易懂，通常一開始為Base Case 

*Base Case*
最簡單的情況下，通常在寫遞迴時，首先起手式就是寫一個if的base case，接著才是else的其他條件

*找尋最大值*
二元搜尋 binary search(一分為二)
分為左右半邊，再分別找尋該區的最大值，最後在比較。
!非常花時間，效率低 <==> 可用迴圈更輕鬆

*費氏數列*
0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144
簡而言之就是下一項為前兩項的和

*在n個選k個的組合數*
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_95372db314cef57c9a9e5c89b8cadd82.png)
前三個為base case 
第四個:當有9大行星要選3個，我將問題簡化成【必選地球+必不選地球】則完成，加號代表或

*Tower 0f Hanoi*               最適合做遞迴
2個盤子=>2^2-1步驟
3個盤子=>2^3-1步驟
...

solveTowers(n,source,final,spare) //[定義]個數,起點,終點,輔助
solveTowers(n-1,source,spare,final) //[解決n-1個盤子的問題] n-1個盤子的終點是輔助柱
solveTowers(1,source,final,spare) //[最大的盤子丟到終點柱]
solveTowers(n-1,spare,final,source) //[n-1個盤子從輔助柱到終點柱]
但遞迴呼叫次數會比自己本身移動還多次

*單字*
alogoritnm 算法
pivot item 樞紐分析表欄位中的項目
factorial 階層

**Ch-2 資料抽象化 Data Abstraction**

**Ch-3 鏈結串列 Linked List**

*陣列 vs. 鏈結串列*
前者:需要移動資料,fixed size
後者:不需要移動資料,able to grow in size as needed,彈性增加資料

*指標 Pointer*
就像門牌一樣，為一種資料型態 
在此比喻:    記憶體=房子    成員=資料

*增加資料*
int *p;    //p為指標用在處存門牌(地址)
p = &x;   //p指向的門牌號碼(x)
*p = 6;    //x的成員(資料)
p = new int;    //增加一個房子
*p = 7;    /p指向房子的成員(new int的資料) 

*減少資料*
delete p;
p = NULL;
!不可對調    //先歸還房子,在遺忘門牌

*Pointer-Based Linked List*

struct Node{    //一節火車的架構
    int item;    //資料
    Node  *next;    //指標
};
//這裡第一個節點head賦值為5,第二個node2賦值為128
int main(int argc, char* argv[])
{
	// create first node "head"
	Node *head = new int;
	// assign data to 5
	head->data = 5;
	// head not point to next node temporarily
	head->next = NULL;
	// declare 2nd node
	Node *node2 = new int;
	// assign data to 128
	node2->data = 128;
	// make first node point to the node2
	head->next = node2;
	// node2 not point to next node temporarily
	node2->next = NULL;
    return 0;	
}


*打印整列火車資料*
for(Node *cur = head; cur!=NULL; cur = cur->next){    //名叫cur的指標
    cout<< cur->next << endl;
}
**Ch-4 中序 Postfix**
pop:The pop operation of the ADT stacks add item to the top of the stack

**Ch-5 堆疊 Stack**

*後序式求解*
將運算元丟入stack中，遇到運算子抓兩個出來運算後在放回stack