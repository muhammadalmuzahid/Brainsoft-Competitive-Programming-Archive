\# Russian Room Rent



\## 📝 Problem Statement

To participate in the ICPC World Final, Muzahid and his team went to Russia and stayed at the Russia International Hotel. The hotel owner, Abdus Salam, gave them a challenge to determine their room rent. 



Suppose the base room rent is $X$ rubles. According to the hotel rules, an additional tax of 1 ruble must be paid for every $Y$ rubles of the rent. 



If they solve this problem, the owner provides a discount of $D$ percent on the total amount (Rent + Tax). If the final amount after the discount is strictly lower than $L$ rubles, output \*\*"YES"\*\*; otherwise, output \*\*"NO"\*\*.



\### Example

\- \*\*Input:\*\* $X=100, Y=10, D=10, L=100$

\- \*\*Total Amount:\*\* $100 + (100/10) = 110$ rubles.

\- \*\*Discounted Amount:\*\* $110 - (110 \\times 10 / 100) = 99$ rubles.

\- \*\*Logic:\*\* $99 < 100 \\implies$ \*\*Output:\*\* `YES`.



---



\## 💡 Key Insight

This is a basic simulation and math problem involving percentages and floor division.







1\.  \*\*Calculate Tax:\*\* The additional tax is $\\lfloor X/Y \\rfloor$.

2\.  \*\*Total Amount:\*\* $Total = X + \\lfloor X/Y \\rfloor$.

3\.  \*\*Apply Discount:\*\* The final amount is $Total - (Total \\times D / 100.0)$.

4\.  \*\*Comparison:\*\* Check if the final amount is strictly less than $L$. Since $D$ is a percentage, use `double` or `long double` to avoid precision errors.



---



\## 🚀 Complexity

\- \*\*Time Complexity:\*\* $O(1)$ per test case as it only involves constant time mathematical operations.

\- \*\*Space Complexity:\*\* $O(1)$ as we only store a few variables.



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

&nbsp;   double X, Y, D, L;

&nbsp;   if (!(cin >> X >> Y >> D >> L)) return;



&nbsp;   // Calculate total including tax (1 ruble for every Y rubles)

&nbsp;   double tax = floor(X / Y);

&nbsp;   double total\_amount = X + tax;



&nbsp;   // Apply D percent discount

&nbsp;   double final\_amount = total\_amount - (total\_amount \* (D / 100.0));



&nbsp;   // Check if the final amount is lower than L

&nbsp;   if (final\_amount < L - EPS) {

&nbsp;       cout << "YES" << "\\n";

&nbsp;   } else {

&nbsp;       cout << "NO" << "\\n";

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

&nbsp;\* Tags: Math, Simulation, Floating-Point, BUET, ICPC-World-Final-Themed

&nbsp;\*/

