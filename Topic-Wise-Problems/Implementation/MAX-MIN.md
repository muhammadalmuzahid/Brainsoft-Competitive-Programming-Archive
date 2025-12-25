\# MAX-MIN



\## 📝 Problem Statement

Alice and Bob are playing a game with an array $A$ consisting of $N$ integers. Alice provides an integer $K$ to Bob. Bob needs to find the \*\*maximum and minimum\*\* elements from every $K$-th non-overlapping segment of the array. 



\### Example

\- \*\*Input:\*\* $N=5, K=2$, Array: `1 2 3 5 4`

\- \*\*Segments:\*\* - Segment 1: `(1, 2)` $\\to$ Max: 2, Min: 1

&nbsp; - Segment 2: `(3, 5)` $\\to$ Max: 5, Min: 3

\- \*\*Input:\*\* $N=6, K=3$, Array: `5 9 1 7 6 4`

\- \*\*Segments:\*\*

&nbsp; - Segment 1: `(5, 9, 1)` $\\to$ Max: 9, Min: 1

&nbsp; - Segment 2: `(7, 6, 4)` $\\to$ Max: 7, Min: 4



---



\## 💡 Key Insight

Since the segments are fixed at size $K$ and do not overlap, we can process the array linearly.







\- We iterate through the array starting from index 0 with a step size of $K$.

\- For each starting position $i$, we traverse the next $K$ elements (from $i$ to $i+K-1$) to find the local maximum and minimum.

\- This approach ensures that we only process full segments as defined by Alice.



---



\## 🚀 Complexity

\- \*\*Time Complexity:\*\* $O(N)$ per test case, as we visit each element of the array exactly once.

\- \*\*Space Complexity:\*\* $O(N)$ to store the input array.



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

const int LEN  = 2e6 + 3;



void idea() {

&nbsp;   int N, K;

&nbsp;   if (!(cin >> N >> K)) return;



&nbsp;   vector<ll> A(N);

&nbsp;   for (int i = 0; i < N; i++) {

&nbsp;       cin >> A\[i];

&nbsp;   }



&nbsp;   // Iterate through the array in steps of K

&nbsp;   for (int i = 0; i + K <= N; i += K) {

&nbsp;       ll cur\_max = -2e18; // Initialize with very small value

&nbsp;       ll cur\_min = 2e18;  // Initialize with very large value



&nbsp;       for (int j = i; j < i + K; j++) {

&nbsp;           cur\_max = max(cur\_max, A\[j]);

&nbsp;           cur\_min = min(cur\_min, A\[j]);

&nbsp;       }



&nbsp;       cout << "Max = " << cur\_max << ", min = " << cur\_min << "\\n";

&nbsp;   }

}



int main() {

&nbsp;   // Fast I/O optimized for competitive programming

&nbsp;   ios::sync\_with\_stdio(0); 

&nbsp;   cin.tie(0);

&nbsp;   

&nbsp;   int T = 1;

&nbsp;   cin >> T;



&nbsp;   for(int C = 1; C <= T; C++) {

&nbsp;       idea();

&nbsp;   }

&nbsp;   return 0;

}



/\*\*

&nbsp;\* Tags: Implementation, Greedy, Array, BUET, ICPC-Prep

&nbsp;\*/

