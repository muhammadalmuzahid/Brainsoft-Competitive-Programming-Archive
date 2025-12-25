\# Mod To Zero



\## 📝 Problem Statement

You are given an array of $N$ natural numbers. The goal is to make the \*\*total sum\*\* of the array divisible by at least \*\*one\*\* of its elements using the minimum number of operations.

An operation consists of:

1\. Adding 1 to any element.

2\. Subtracting 1 from any element.



If the total sum is already divisible by any of its elements, the answer is `0`.



\### Example

\- \*\*Array:\*\* `\[9, 4, 6]` (Total Sum = 19)

\- \*\*Logic:\*\* - $19 \\% 9 = 1$ (1 sub op needed)

&nbsp; - $19 \\% 4 = 3$ (3 sub ops or 1 add op needed)

&nbsp; - $19 \\% 6 = 1$ (1 sub op needed)

\- \*\*Output:\*\* `1`

\- \*\*Explanation:\*\* By subtracting 1 from the second element ($4 \\to 3$), the new sum becomes 18, which is divisible by 3.



---



\## 💡 Key Insight (Greedy/Math)

The problem asks for the minimum operations to satisfy $Sum \\equiv 0 \\pmod{a\_i}$ for any $i$.

For each element $a\_i$ in the array:

\- The number of subtractions needed to make the sum divisible by $a\_i$ is `Sum % a\[i]`.

\- The number of additions needed to make the sum divisible by $a\_i$ is `a\[i] - (Sum % a\[i])`.

\- We simply need to find the minimum of these two values across all $a\_i$ in the array.







---



\## 🚀 Complexity

\- \*\*Time Complexity:\*\* $O(N)$ per test case to calculate the sum and iterate through the array once.

\- \*\*Space Complexity:\*\* $O(N)$ to store the array elements.



---



\## 💻 Implementation

This solution uses the standard \*\*brainsoft\*\* template.



```cpp

\#include <bits/stdc++.h>



using namespace std;

using ll = long long;



const int INF = 1e9;



void idea() {

&nbsp;   int n;

&nbsp;   if (!(cin >> n)) return;



&nbsp;   vector<ll> a(n);

&nbsp;   ll total\_sum = 0;

&nbsp;   for (int i = 0; i < n; i++) {

&nbsp;       cin >> a\[i];

&nbsp;       total\_sum += a\[i];

&nbsp;   }



&nbsp;   ll min\_ops = 2e18; // Initialize with a very large value



&nbsp;   for (int i = 0; i < n; i++) {

&nbsp;       ll remainder = total\_sum % a\[i];

&nbsp;       

&nbsp;       if (remainder == 0) {

&nbsp;           min\_ops = 0;

&nbsp;           break;

&nbsp;       }



&nbsp;       // Option 1: Subtract 'remainder' amount from any element

&nbsp;       // Option 2: Add 'a\[i] - remainder' amount to any element

&nbsp;       ll current\_min = min(remainder, a\[i] - remainder);

&nbsp;       min\_ops = min(min\_ops, current\_min);

&nbsp;   }



&nbsp;   cout << min\_ops << "\\n";

}



int main() {

&nbsp;   ios::sync\_with\_stdio(0); 

&nbsp;   cin.tie(0);

&nbsp;   

&nbsp;   int T;

&nbsp;   cin >> T; // Number of test cases

&nbsp;   while(T--) {

&nbsp;       idea();

&nbsp;   }

&nbsp;   return 0;

}

