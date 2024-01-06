# C++ 常用指令

1. Array/List
2. Set
3. Map
4. Tree
---

## List
vector<int> 長度可變的陣列，增刪方便
#include <vector>

長度:A.size()//記得int size=A.size();
第一個元素:A.begin() 最後一個元素:A.back() 尾:A.end()
第i位值:A[i]
加入尾A.push_back() 刪尾A.pop_back()//stack
判斷空A.empty()//true:false

轉換vector<string>到vector<char>
#include <string>
```
string s = "Hello World!";
vector<char> v(s.begin(), s.end());
```
 
#include <algorithm>
sort(A.begin(),A.end())

遍歷
1. for(int i=0; i<v.size(); i++) cout << v[i] << " ";
2. vector<int>::iterator itr;
for(itr=A.begin(); itr!=A.end(); ++itr) cout << *itr << " "; 

排序(泡泡)
```
void bubbleSort(vector<int>& A){
      bool swap = true;
      while(swap){
        swap = false;
        for (size_t i = 0; i < a.size()-1; i++) {
            if (A[i]>A[i+1] ){
                Swap(&A[i], &A[i+1]);
            }
        }
    }
}
```
交換
```
void Swap (int *a, int *b)
{
    int temp = *a;
    *a = *b;
    *b = temp;
}
```
排序(快速)
main使用: quicksort(vec1, 0, count - 1);
```
void quicksort(vector<int> &vec, int L, int R) {
    int i, j, mid, piv;
    i = L;
    j = R;
    mid = L + (R - L) / 2;
    piv = vec[mid];

    while (i<R || j>L) {
        while (vec[i] < piv)
            i++;
        while (vec[j] > piv)
            j--;

        if (i <= j) {
            swap(vec, i, j); //error=swap function doesnt take 3 arguments
            i++;
            j--;
        }
        else {
            if (i < R)
                quicksort(vec, i, R);
            if (j > L)
                quicksort(vec, L, j);
            return;
        }
    }
}
```

列印
```
void printVector(vector<int> A){
    for (size_t i=0;  i <A.size();  i++) {
        cout<<A[i]<<" ";
    }
  cout<<endl;
}
```

---
## Set

set<int> aSet 元素排序好的且都是唯一的，沒有重複的
string轉set
```
int arr[] = {75,23,65,42,13};
set<int> aSet(arr, arr+5);
```
插入:aSet.insert(val) 
移除:
``` 
//删除值为5的元素，返回删除的元素个数
s1.erase(5);   

//删除首个元素，无返回值
s1.erase(s1.begin());   

//清空
s1.clear();
``` 
查找
```
if(s1.find(5)!=s1.end())
    cout<<"FOUND"<<endl;
```

遍歷
```
for (std::set<int>::iterator it=myset.begin(); it!=myset.end(); ++it)
    std::cout << ' ' << *it;
 std::cout << '\n';
```

---
### Map: 
#include<map>
map<string, int> aMap 搜尋快和插入時自動大小排序

插入:aMap["Megan"] = "0320";
map<string, string>::iterator itr;
key值:itr.first value:itr.second

從key找值
```
iter = aMap.find(1);
if(iter != aMap.end()){
       Cout<<”Find, the value is ”<<iter->second<<endl;
}else{
       Cout<<”Do not Find”<<endl;
}
```
遍歷
```
map<string, string>::iterator itr;
for(itr = aMap.begin(); itr != aMap.end(); itr++)
    cout<<itr.first<<" "<<itr.second<<endl;
```

---
## Tree



#### Determine whether a given string of parentheses (multiple types) is properly nested.
---
```
// you can use includes, for example:
// #include <algorithm>
#include<vector>
// you can write to stdout for debugging purposes, e.g.
// cout << "this is a debug message" << endl;

int solution(string &A) {
    // write your code in C++14 (g++ 6.2.0)
    vector<char> note;
    int size=A.size();
    if(size <=1) return 0;
    for(int i=0;i<size;i++){
        //printf("\ni= %d",i);
        if(A[i]=='('||A[i]=='['||A[i]=='{'){
            note.push_back(A[i]);
            //printf("1");
            }
        else if(A[i]==')'||A[i]==']'||A[i]=='}'){
            if(note.empty()) return 0;
            //printf("2");
            if(A[i]==')'&&note.back()!='(') return 0;
            if(A[i]==']'&&note.back()!='[') return 0;
            if(A[i]=='}'&&note.back()!='{') return 0;
            //printf("3");
            note.pop_back();
        }
        else{
            return 0;
        }

    }
    //printf("4");
    if(!note.empty()) 
        return 0;
    else return 1;
}
```