```
#include <iostream>

#include <queue>

#include <vector>

using namespace std;

#define MAXV 200005

long long LP[MAXV]; 
  

typedef struct

{

 int to;

 int dis;

 int dan;

} Edge;

  

bool closer(int const &a, int const &b)

{

     return LP[a] > LP[b];

}

  

void addEdge(vector<Edge> Edges\[\], int X, int Y, int distance, int danger)

{

    Edge newEdge;

     newEdge.dis = distance;

     newEdge.dan = danger;

     newEdge.to = Y;

     Edges[X].push_back(newEdge);

     newEdge.to = X;

     Edges[Y].push_back(newEdge);

}

  

int main()

{

 int V, E, home, des;

 long long L, D;

    cin >> V >> E >> home >> des;

    vector<Edge> Edges[V];

  

    // initialize edges

 for (int i = 0; i < E; i++)

    {

        int X, Y, distance, danger;

        cin >> X >> Y >> distance >> danger;

        addEdge(Edges, X, Y, distance, danger);

        L = danger;

    }

  

    
vector<int> Q;

 for (int i = 0; i < V; i++)

    {

     Q.push_back(i);

     LP[i] = INT64_MAX;

    }

 LP[home] = 0;

 make_heap(Q.begin(), Q.end(), closer);

  

 while (!Q.empty())

 {

     int u = Q.front();
     pop_heap(Q.begin(), Q.end(), closer); // move u to last one
     Q.pop_back();                         // pop u

  

 for (int v = 0; v < Edges\[u\].size(); v++)
    {

        int adj = Edges[u][v].to;

        LP[adj] = min(LP[adj], LP[u] + Edges[u][v].dis);

    }

}

 D = LP[des];
 printf("%lld %lld\\n", D, L);
 return 0;

}

```