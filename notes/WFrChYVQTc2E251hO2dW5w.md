資料結構實習
===
###### tags: `資料結構實習`
**CASE2是新的**
[TOC]
---
# 基礎題
##  Week 2_練習二：質因數分解 
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_28fad09524f0e805260fdfcada48c58d)
### case 1
```
 #include<iostream>
using namespace std;
int main() {
	 int a ;
	 while (cin >> a) {
		 bool have = 0;
		 for (int i = 2; i < a; i++) {
			 int time = 0 ;
			 if (a%i == 0) {
				 while (a % i == 0)
				 {
					 a /= i;
					 time++;
				 }
				 if (have)
					 cout << " * ";
				 else
					 have = 1;
					 cout << i;
				 if (time > 1)
					 cout << "^" << time;
			 }
		 }
		 if (a != 1)
		 {
			 if (have)
				 cout << " * ";
			 cout << a << endl;
		 }
	}
	return 0;
}
```
### case 2
```
#include<iostream>
#include<vector>
using namespace std;
int main(){
    long long int num;
    cin >> num;

    bool have = 0;

    for(long long int i=2;i<=num;i++){
            int time = 0;
            while( num % i==0){
                num/=i;
                time++;
            }
            if(time){
                if(have)
                cout <<" * ";
            else 
                have=1;

            cout<< i;

            if(time >1 )
                cout<<"^"<<time;
            }
            if (num==1)
                break;
        }
        if(num!=1){
            cout<<num<<endl;
        }   
    return 0;
}
```
# 其他
##  Week 10_練習三：鏈結串列反轉
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5fee89f3333d878edffb4eac0f0d672b)

### case 1
```
#include<iostream>
#include<string>
using namespace std;
struct listnode {
	int data;
	listnode *link;
};
void push_link(listnode **first,int num );
void print_link(listnode *first);
void push_link(listnode **first,int num ){
    listnode *temp=new listnode;
    temp->data=num;
    if(*first){
        temp->link=*first;
        *first=temp;
    }
    else{
        temp->link=NULL;
        *first=temp;
    }
}
void print_link(listnode *first){
    while(first){
        cout<<first->data;
        first=first->link;
        if(first){
            cout<<' ';
        }
    }
    cout<<endl;
}
int main() {
	listnode *first=NULL;
	int num;
    while(scanf("%d",&num)!=EOF){
        push_link(&first,num);
    }
    print_link(first);
	//system("pause");
	
	return 0;

}
```
### case 2
```
#include<iostream>
#include<list>
using namespace std;
int main(){
    list<int> a;
    int num;
    while(cin >> num){
        a.push_back(num);
    }
    a.reverse();
    list<int> :: iterator it;
    
    for( it= a.begin() ; it != a.end() ; it++){
        if(it!=a.begin())
            cout<<' ';

        cout<< *it;
    }
    cout<<endl;
    return 0;
}
```
## Week 13_練習二：二元搜尋樹插入節點 
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_61a2aaa9f6e5bd3c79f4d98bf0e33b5a)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2991c85c30fd6377d74cc4064f96b39c)
### case 1
```
#include<iostream>
#include<string>
using namespace std;
struct node {
	int data;
    node * leftChild, *rightChild;
};
void insert(node * &tree,int num);
void insert(node * &tree,int num){
    if(tree==NULL){
        node *temp=new node ;
		temp->data = num;
		temp->leftChild = NULL;
		temp->rightChild = NULL;
		tree = temp;
    }
   else {
		if (tree->data > num)
			insert(tree->leftChild, num);
		else
			insert(tree->rightChild, num);
	}
}
void preorder(node*& ptr) {
	if (ptr) {
		cout << ptr->data << ' ';
		preorder(ptr->leftChild);
		preorder(ptr->rightChild);
	}
}
int main(){
    node *tree=NULL;
    int num;
    string c;
    while(cin >>num){
        insert(tree,num);
		preorder(tree);
		cout << endl;
    }
	
	system("pause");
}
```
### case 2
```
#include<iostream>
#include<vector>
using namespace std;
struct node{
    int data;
    node* leftchild, * rightchild;
};
void insert(node * & tree,int num);
void preorder(node * tree);
void insert(node * & tree,int num){
    if(tree==NULL){
        node *temp=new node;
        temp->data=num;
        temp->leftchild=NULL;
        temp->rightchild=NULL;
        tree = temp;
    }
    else if( tree->data > num)
        insert(tree->leftchild,num);
    else
        insert(tree->rightchild,num); 
}
void preorder(node * tree){
    if(tree){
        cout<< tree->data<<' ';
        preorder(tree->leftchild);
        preorder(tree->rightchild);
    }
}
int main(){
    node *tree=NULL;
    int num;
    while(cin >> num){
        insert(tree,num);
        preorder(tree);
    }
    return 0;
}
```
##  Week 14_練習二：Min Heap 刪除節點 
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4fe7a48cf2374bcf8952f7f0318d645b)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5f28413d0a686e1d360152c74848c867)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b1746325935b2da5a25007ce6f5bcb04)
### case 1
```
#include<iostream>
#include<string>
#include<vector>
#include<algorithm>
using namespace std;
vector<int> heap(2048,0);
void insert(int num,int &total);
void pop(int& total);
void order(int total);
void insert(int num, int &total) {
	int i=++total;
	while ((i != 1) && (num < heap[i / 2])) {
		heap[i] = heap[i / 2];
			i /= 2; 
	}     
		heap[i]=num;
}
void pop(int& total) {
	if (total == 0)
		return;
	int parent=1, child=2,iteam=heap[1], temp = heap[total--];
	while (child <= total) {
		if ((child < total) && heap[child] > heap[child + 1])
			child++;
		if (temp < heap[child]) break;
		heap[parent] = heap[child];
		parent = child;
		child *= 2;
	}
	heap[parent] = temp;
}
void order(int total) {
	for (int i = 1; i <=total; i++) {
		cout << "["<<i<<"]"<< heap[i];
		if (i < total )
			cout << ' ';
	}
	cout << endl;
}
int main() {
	int num,total=0;
	string c;
	while (cin >> num) {
		insert(num,total);
	}
	while (total > 0) {
		order(total);
		pop(total);
	}
	system("pause");
}
```
### case 2
```
#include<iostream>
#include <algorithm>
#include<vector>
using namespace std;
void print(vector<int> &min_heap);
void print(vector<int> &min_heap){
    for(int i=0;i< min_heap.size();i++){
         cout << "[" << i+1 << "]" << min_heap[i];
         if (i < min_heap.size() -1)
			cout << ' ';
    }
}
bool cmp( int a ,int b){
    return a > b;
}
int main(){
    vector<int> min_heap;
    int num ;
    while( cin >> num){
        min_heap.push_back(num);
    }
    make_heap(min_heap.begin(),min_heap.end(),cmp);
    print(min_heap);
    while(min_heap.size()){
        pop_heap(min_heap.begin(),min_heap.end(),cmp);
        min_heap.pop_back();
        cout<<endl;
        print(min_heap);
    }
    return 0;
}
```
##  Week 15_練習二：DFS 與 BFS
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6a263a76e33592e490ce28cb26abde41)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d477cf1ef36ad28c3439ee37f64afcdf)
### case 1
```
#include<iostream>
#include<vector>
#include <list>
using namespace std;
void dfs(int v , vector< list<int> > graph, vector<bool> &visited , bool first );
void bfs(int v , vector< list<int> > graph, vector<bool> &visited );
void dfs(int v, vector< list<int> > graph, vector<bool> &visited , bool first){
    visited[v]=true;
    if(!first)
        cout<<' ';
    cout<<v;
    list<int> :: iterator it;
    for(it=graph[v].begin();it!=graph[v].end();it++){
        if(!visited[*it])
        dfs(*it,graph,visited,0);
    }
}
void bfs(int v , vector< list<int> > graph, vector<bool> &visited ){
    visited[v]=true;
    cout<<v;
    vector<int> Queue;
    Queue.push_back(v);
    int front=-1,rear=0;
    while(front!=rear){
        front++;
        list<int> :: iterator it2;
        for(it2=graph[Queue[front]].begin();it2!=graph[Queue[front]].end();it2++){
            if(!visited[*it2]) {
                cout<<' '<<*it2;
                Queue.push_back(*it2);
                rear++;
                visited[*it2]=true;
            }
        } 
    }
    cout<<endl;
}
int main(){
    int num1, num2, max=0, min=2147483647;
    vector< list<int> > graph(1);
    while(cin >> num1 >> num2){
        if( max < num1 ){
            max=num1;
            graph.resize(num1+1);
        }
        graph[num1].push_back(num2);
        if(max<num2){
            max=num2;
            graph.resize(num2+1);
        }
        graph[num2].push_back(num1);
        if( min > num1 ) min = num1;
        if( min > num2 ) min = num2;
    }
    vector<bool> visited_bfs(max+1,false),visited_dfs(max+1,false);
    cout << "Depth First Search:" << endl;
    dfs(min,graph,visited_dfs,1);
    cout<<endl;
    cout <<endl<< "Breadth First Search:" << endl;
    bfs(min,graph,visited_bfs);
    return 0;
}
```
### case 2
```
#include<iostream>
#include<vector>
#include <list>
using namespace std;
void dfs(int v,vector<bool> &dfs_v ,vector<list<int> > adj, bool first);
void bfs(int v,vector<bool> &bfs_v ,vector<list<int> > adj,vector<int> stack,int front, bool first);
void dfs(int v,vector<bool> & dfs_v ,vector<list<int> > adj , bool first){
    dfs_v[v]=true;
    if(!first)
        cout<<' ';
    cout<<v;
    list<int> :: iterator it;
    for(it=adj[v].begin();it!= adj[v].end();it++){
        if(!dfs_v[*it])
            dfs(*it,dfs_v,adj,0);
    }
}
void bfs(int v,vector<bool> &bfs_v ,vector<list<int> > adj,vector<int> stack,int front , bool first){
    if(!bfs_v[v]){
        bfs_v[v]=true;
        if(!first)
            cout<<' ';
        cout<<v;
        list<int> :: iterator it;
        for(it=adj[v].begin();it!= adj[v].end();it++){
            if(!bfs_v[*it])
            {   stack.push_back(*it);}
        }
    }
    front++;
    if(front < stack.size())
        bfs(stack[front],bfs_v,adj,stack,front,0);
}
int main(){
    vector < list <int> >  adj;
    int num1,num2,max=-1,min=2147483647;
    while( cin >> num1 >> num2 ){
        if(max < num1){
            max=num1;
            adj.resize(max+1);
        }
        if(max < num2){
            max=num2;
            adj.resize(max+1);
        }
        adj[num1].push_back(num2);
        adj[num2].push_back(num1);
        if( min > num1 ) min = num1;
        if( min > num2 ) min = num2;
    }
    vector<bool> bfs_v(max+1,false),dfs_v(max+1,false);
    cout << "Depth First Search:" << endl;
    dfs(min , dfs_v , adj , 1 );
    cout<<endl;
    cout <<endl<< "Breadth First Search:" << endl;
    vector<int> stack(1,min);
    bfs(min , bfs_v , adj ,stack, 0 , 1 );
    cout<<endl;
    return 0;
}
```
##  Week 16_練習二：Kruskal’s algorithm 
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_208bb500c8c7ffdb511be0a73025e452)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_02994e15466dd39083d26a17a658a3b9)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4c38db5d9704c1e470048cffe2685713)
### case1
```
#include<iostream>
#include<vector>
#include<list>
#include <algorithm>
using namespace std;
struct edge
{
    int a,b,distance;
};
bool Union(int a, int b,vector<int> &friends);
bool compare(edge  a, edge b);
bool Union(int a, int b,vector<int> &friends)
{
        if(friends[a] !=friends[b]){
                int temp=friends[a];
            for(int i=0;i<friends.size();i++){
                if(friends[i]==temp)
                    friends[i]=friends[b];
            }
            return 1;
        }
        return 0;
}
bool compare(edge  a, edge b)
{
    return a.distance <b.distance ;
}

int main()
{
    vector< edge > graph;
    int num1,num2,dis,maxi=0;
    while(cin >> num1>> num2>>dis ){
        graph.push_back({num1,num2,dis} );
        if(maxi<num1)maxi=num1;
        if(maxi<num2)maxi=num2;
    }
    sort(graph.begin(),graph.end(),compare);
    vector<int> friends;
    for(int i=0; i<maxi+1; i++){
        friends.push_back(i);
    }
    dis=0;
    for(int i=0,j=1; i<graph.size(); i++){
        if(Union(graph[i].a, graph[i].b,friends)){
              cout<<j<<": "<<"<"<<graph[i].a <<","<<graph[i].b << ">"<<endl;
              dis+=graph[i].distance;
              j++;
         }
    }
    cout<<endl;
    cout<<"The cost of minimum spanning tree: "<<dis<<endl;
    return 0;
}
```
### case2
```
#include<iostream>
#include<vector>
#include<algorithm>
using namespace std;
struct edge{
    int a,b,dist;
};
bool Union(int a, int b,vector<int> &friends);
bool cmp(edge a, edge b){
    return a.dist < b.dist;
}
bool Union(int a, int b,vector<int> &friends){
    if(friends[a]!=friends[b]){
        int temp=friends[a];
        for(int i=0;i< friends.size();i++){
            if(friends[i]==temp)
            friends[i]=friends[b];
        }
    return 1;
    }
    return 0;
}
int main(){
    vector< edge > graph;
    int num1,num2,dis,maxi=0;;
    while(cin >> num1 >> num2 >> dis){
        edge temp;
        temp.a=num1;
        temp.b=num2;
        temp.dist=dis;
        graph.push_back( temp );
        if(maxi<num1)maxi=num1;
        if(maxi<num2)maxi=num2;
    }
    sort(graph.begin(),graph.end(),cmp);
    vector<int> friends;
    for(int i=0; i<maxi+1; i++){
        friends.push_back(i);
    }
    dis=0;
   for(int i=0,j=1; i<graph.size(); i++){
       if(Union(graph[i].a, graph[i].b,friends)){
            cout<<j<<": "<<"<"<<graph[i].a <<","<<graph[i].b << ">"<<endl;
            dis+=graph[i].dist;
            j++;
       }
   }
   cout<<endl;
    cout<<"The cost of minimum spanning tree: "<<dis<<endl;
    return 0;
}
```
##  Week 17_練習二：計算 dist^k [u]
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0775560ef6b0fbb7ff46c62c292d269b)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b72615b098d9f25bb637fa0686871c6b)
### case1
```
#include<iostream>
#include<vector>
using namespace std;
void BellmanFord(vector< vector<int> > &arr,vector< vector<int> > &distance);
int main()
{
    int a,b,dis,maxi=0;
    vector< vector<int> > arr(105,vector<int>(105,2147483647));
    while(cin >> a>> b>> dis){
        if(maxi<a)
            maxi=a;
        if(maxi<b)
            maxi=b;
        arr[a][b]=dis;
    }
    vector< vector<int> >  distance(maxi+1,vector<int>(maxi+1,2147483647));
    BellmanFord(arr,distance);
    for(int i=1; i<distance.size(); i++){
        for(int j=0; j<distance.size(); j++)
        {
            if(distance[i][j]==2147483647)
                cout<<"i";
            else
                cout<<distance[i][j];
            if(j==distance.size()-1)
                cout<<endl;
            else
                cout<<' ';
        }
    }
    return 0;
}
void BellmanFord(vector< vector<int> > &arr,vector< vector<int> > &distance)
{
    distance[0][0]=arr[0][0]=0;
    for(int i=1; i<distance.size(); i++)
    {
        distance[1][i]=arr[0][i];
        distance[i][0]=0;
    }
    for (int k = 2; k < distance.size(); k++)
    {
        for (int i = 1; i < distance.size(); i++)
        {
            int mini=2147483647;
            mini=min(mini,distance[k-1][i]);
            for (int data = 1; data < distance.size(); data++)
            {
                    if(distance[k-1][data]!=2147483647 && arr[data][i]!=2147483647)
                     mini=min(mini,distance[k-1][data]+arr[data][i]);
            }
            distance[k][i]=mini;
        }
    }
}
```
### case 2
```
#include<iostream>
#include<vector>
#include <algorithm>
using namespace std;
void bellman_ford(vector< vector<int> > arr , vector< vector<int> >  dist );
void bellman_ford(vector< vector<int> > arr , vector< vector<int> >  dist ){
    arr[0][0]=0;
    for(int i=0;i< dist.size();i++){
        dist[1][i]=arr[0][i];
        dist[i][0]=0;
    }
    for(int k=1;k<dist.size();k++){
        for(int next=0;next<dist.size();next++){
            int mini=dist[k-1][next];
            for(int now=0;now<dist.size();now++){
                if(dist[k-1][now]!=2147483647 && arr[now][next]!=2147483647)
                    mini=min(mini,dist[k-1][now]+arr[now][next]);
            }
            dist[k][next]=mini;

            if(dist[k][next]==2147483647)
                cout<<"i";
            else
                cout<< dist[k][next];
            if(next==dist.size()-1)
                cout<<endl;
            else
                cout<<' ';
        }
    }
}
int main(){
    int num1,num2,dis,maxi=0;
    vector< vector<int> > arr(105,vector<int>(105,2147483647));
    while(cin >>num1 >> num2 >> dis ){
        if(maxi < num1)maxi=num1;
        if(maxi< num2)maxi=num2;
        arr[num1][num2]=dis;
    }
    vector< vector<int> >  dist(maxi+1,vector<int > (maxi+1,2147483647));
    bellman_ford(arr ,dist );
    return 0;
}
```