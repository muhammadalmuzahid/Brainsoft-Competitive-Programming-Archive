\# Spicy Numbers (Mojar Gonit)



\## 📝 Problem Statement

In "Mojar Gonit", a number is called a \*\*Spicy Number\*\* if all its digits are the same (e.g., $111, 77, 9$). Given a target number $N$ and a move limit $K$, you need to determine if you can reach $N$ starting from $0$ using at most $K$ spicy numbers through addition or subtraction.



If the minimum moves required to reach $N$ is $\\le K$, output \*\*"Alhamdulillah"\*\*. Otherwise, output \*\*"InShaAllah, next time"\*\*.



\### Example

\- \*\*Target ($N$):\*\* $986$, \*\*Moves ($K$):\*\* $3$

\- \*\*Path:\*\* $999 - 11 - 2 = 986$ (3 spicy numbers used)

\- \*\*Output:\*\* `Alhamdulillah`



\- \*\*Target ($N$):\*\* $369$, \*\*Moves ($K$):\*\* $3$

\- \*\*Path:\*\* $333 + 33 + 3 = 369$ (3 spicy numbers used)

\- \*\*Output:\*\* `Alhamdulillah`



---



\## 💡 Key Insight

This is a shortest-path problem in an unweighted graph, which can be solved using \*\*BFS\*\*. 



\- Each number from $0$ to $MAXN$ is a node.

\- Adding or subtracting a spicy number represents an edge of weight $1$.

\- BFS will find the minimum number of spicy numbers needed to reach $N$ from $0$.



---



\## 🚀 Complexity

\- \*\*Time Complexity:\*\* $O(N \\times \\text{count of spicy numbers})$ per test case.

\- \*\*Space Complexity:\*\* $O(N)$ for the distance array and BFS queue.



---



\## 💻 Implementation



```cpp

\#include <bits/stdc++.h>



using namespace std;

using ll = long long;



const int MAXN = 1000005; 

int dist\[MAXN];

vector<int> spicy;



void precompute() {

&nbsp;   // Generate all spicy numbers (all digits same) up to 10^6

&nbsp;   for (int len = 1; len <= 6; len++) {

&nbsp;       for (int digit = 1; digit <= 9; digit++) {

&nbsp;           string s(len, digit + '0');

&nbsp;           ll val = stoll(s);

&nbsp;           if (val < MAXN) spicy.push\_back((int)val);

&nbsp;       }

&nbsp;   }

}



void idea() {

&nbsp;   int N, K;

&nbsp;   if (!(cin >> N >> K)) return;



&nbsp;   // BFS to find the minimum number of operations

&nbsp;   queue<int> q;

&nbsp;   for(int i = 0; i < MAXN; i++) dist\[i] = -1;



&nbsp;   q.push(0);

&nbsp;   dist\[0] = 0;



&nbsp;   while (!q.empty()) {

&nbsp;       int curr = q.front();

&nbsp;       q.pop();



&nbsp;       if (curr == N) break;



&nbsp;       for (int s : spicy) {

&nbsp;           // Addition

&nbsp;           if (curr + s < MAXN \&\& dist\[curr + s] == -1) {

&nbsp;               dist\[curr + s] = dist\[curr] + 1;

&nbsp;               q.push(curr + s);

&nbsp;           }

&nbsp;           // Subtraction

&nbsp;           if (curr - s >= 0 \&\& dist\[curr - s] == -1) {

&nbsp;               dist\[curr - s] = dist\[curr] + 1;

&nbsp;               q.push(curr - s);

&nbsp;           }

&nbsp;       }

&nbsp;   }



&nbsp;   if (dist\[N] != -1 \&\& dist\[N] <= K) {

&nbsp;       cout << "Alhamdulillah" << endl;

&nbsp;   } else {

&nbsp;       cout << "InShaAllah, next time" << endl;

&nbsp;   }

}



int main() {

&nbsp;   ios::sync\_with\_stdio(0); 

&nbsp;   cin.tie(0);

&nbsp;   

&nbsp;   precompute();

&nbsp;   

&nbsp;   int T = 1;

&nbsp;   cin >> T;

&nbsp;   for(int C = 1; C <= T; C++) {

&nbsp;       idea();

&nbsp;   }

&nbsp;   return 0;

}



/\*\*

&nbsp;\* Tags: BFS, Shortest Path, Math, Precomputation, BUET, Software-Interview

&nbsp;\*/

