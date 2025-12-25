\# Find Your Shortest Path!



\## 📝 Problem Statement

You are given a bidirectional graph with $n$ nodes and $m$ edges. Each edge $(u, v)$ has a specific weight $w$ representing the travel cost. Your task is to find the minimum cost to travel from a starting node $a$ to a goal node $b$ using the \*\*Dijkstra Algorithm\*\*.



If it is impossible to reach node $b$ from node $a$, output \*\*"not possible"\*\*.



\### Example

\- \*\*Input:\*\* $n=3, m=3, a=2, b=0$. Edges: $(0, 1, 100), (0, 2, 200), (1, 2, 50)$.

\- \*\*Path Calculation:\*\* - Directly $2 \\to 0$ costs $200$.

&nbsp; - Via node 1 ($2 \\to 1 \\to 0$) costs $50 + 100 = 150$.

\- \*\*Output:\*\* `Case #2: 150`.



---



\## 💡 Key Insight

Dijkstra's Algorithm is ideal for finding the shortest path in a graph with non-negative edge weights.







1\.  \*\*Priority Queue:\*\* Use a min-priority queue to always process the node with the smallest current distance.

2\.  \*\*Relaxation:\*\* For each neighbor $v$ of current node $u$, update $dist\[v]$ if $dist\[u] + weight(u, v) < dist\[v]$.

3\.  \*\*Graph Representation:\*\* Use an adjacency list to store the bidirectional edges.

4\.  \*\*Case Handling:\*\* Output the minimum distance or "not possible" if the goal node remains at infinity.



---



\## 🚀 Complexity

\- \*\*Time Complexity:\*\* $O((N + M) \\log N)$ per test case, where $N$ is nodes and $M$ is edges.

\- \*\*Space Complexity:\*\* $O(N + M)$ to store the adjacency list and distance array.



---



\## 💻 Implementation



```cpp

\#include <bits/stdc++.h>



using namespace std;

using ll = long long;



const double PI = acos(-1);

const double EPS = 1e-9;

const int INF = 1e9;

const int MOD = 1e9 + 7;

const int MAXN = 20005;



vector<pair<int, int>> adj\[MAXN];

int dist\[MAXN];

bool vis\[MAXN];



void idea() {

&nbsp;   int n, m, a, b;

&nbsp;   if (!(cin >> n >> m >> a >> b)) return;



&nbsp;   // Resetting structures for each test case

&nbsp;   for (int i = 0; i < MAXN; i++) {

&nbsp;       adj\[i].clear();

&nbsp;       dist\[i] = INF;

&nbsp;       vis\[i] = false;

&nbsp;   }



&nbsp;   for (int i = 0; i < m; i++) {

&nbsp;       int u, v, w;

&nbsp;       cin >> u >> v >> w;

&nbsp;       adj\[u].push\_back({v, w});

&nbsp;       adj\[v].push\_back({u, w});

&nbsp;   }



&nbsp;   // Dijkstra's Algorithm implementation

&nbsp;   priority\_queue<pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>>> pq;

&nbsp;   dist\[a] = 0;

&nbsp;   pq.push({0, a});



&nbsp;   while (!pq.empty()) {

&nbsp;       int d = pq.top().first;

&nbsp;       int u = pq.top().second;

&nbsp;       pq.pop();



&nbsp;       if (vis\[u]) continue;

&nbsp;       vis\[u] = true;



&nbsp;       if (u == b) break;



&nbsp;       for (auto \&edge : adj\[u]) {

&nbsp;           int v = edge.first;

&nbsp;           int w = edge.second;



&nbsp;           if (dist\[u] + w < dist\[v]) {

&nbsp;               dist\[v] = dist\[u] + w;

&nbsp;               pq.push({dist\[v], v});

&nbsp;           }

&nbsp;       }

&nbsp;   }



&nbsp;   if (dist\[b] == INF) {

&nbsp;       cout << "not possible" << endl;

&nbsp;   } else {

&nbsp;       cout << dist\[b] << endl;

&nbsp;   }

}



int main() {

&nbsp;   // Fast I/O for competitive programming

&nbsp;   ios::sync\_with\_stdio(false);

&nbsp;   cin.tie(0);

&nbsp;   cout.tie(0);



&nbsp;   int T = 1;

&nbsp;   cin >> T;

&nbsp;   for (int C = 1; C <= T; C++) {

&nbsp;       cout << "Case #" << C << ": ";

&nbsp;       idea();

&nbsp;   }

&nbsp;   return 0;

}



/\*\*

&nbsp;\* Tags: Dijkstra, Graph Theory, Shortest Path, Priority Queue, BUET, ICPC-Prep

&nbsp;\*/

