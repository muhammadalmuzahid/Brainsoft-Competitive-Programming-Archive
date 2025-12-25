\# Count Pairs in Range



\## 📝 Problem Statement

You are given $N$ sorted pairs $(x, y)$. For each query $(L, R)$, count how many pairs satisfy:

1\.  $x \\ge L$

2\.  $y \\le R$



\### Example

\- \*\*Pairs:\*\* `(1, 3), (7, 9), (11, 13), (17, 19)`

\- \*\*Query:\*\* `L=2, R=9`

\- \*\*Output:\*\* `1`

\- \*\*Explanation:\*\* Only the pair `(7, 9)` satisfies both conditions ($7 \\ge 2$ and $9 \\le 9$).



---



\## 💡 Key Insight

Since the pairs are sorted and $y$ increases as $x$ increases, the valid pairs form a continuous segment in the array. 

\- We use `lower\_bound` on the $x$ values to find the first index where $x \\ge L$.

\- We use `upper\_bound` on the $y$ values to find the first index where $y > R$.

\- The difference between these two indices gives the total count.



---



\## 🚀 Complexity

\- \*\*Preprocessing:\*\* $O(N \\log N)$ for sorting.

\- \*\*Query:\*\* $O(\\log N)$ per query using Binary Search.

\- \*\*Space:\*\* $O(N)$ to store the vectors.



---



\## 💻 Implementation

This solution uses the standard \*\*brainsoft\*\* template.



```cpp

\#include <bits/stdc++.h>



using namespace std;

using ll = long long;



void idea() {

&nbsp;   int N; 

&nbsp;   if (!(cin >> N)) return;



&nbsp;   vector<ll> First(N), Second(N);

&nbsp;   for (int i = 0; i < N; i++) {

&nbsp;       cin >> First\[i] >> Second\[i];

&nbsp;   }



&nbsp;   int Q; cin >> Q;

&nbsp;   while (Q--) {

&nbsp;       ll L, R; cin >> L >> R;



&nbsp;       // Find the start: first index where x >= L

&nbsp;       int start = lower\_bound(First.begin(), First.end(), L) - First.begin();

&nbsp;       

&nbsp;       // Find the end: first index where y > R

&nbsp;       int end = upper\_bound(Second.begin(), Second.end(), R) - Second.begin();



&nbsp;       // Count is end - start

&nbsp;       int ans = end - start;



&nbsp;       cout << max(0, ans) << "\\n";

&nbsp;   }

}



int main() {

&nbsp;   ios::sync\_with\_stdio(0); 

&nbsp;   cin.tie(0);

&nbsp;   

&nbsp;   int T = 1;

&nbsp;   for(int C = 1; C <= T; C++) {

&nbsp;       idea();

&nbsp;   }

&nbsp;   return 0;

}

