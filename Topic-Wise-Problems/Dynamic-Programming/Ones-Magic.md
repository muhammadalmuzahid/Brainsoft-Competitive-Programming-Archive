One's Magic📝 Problem StatementThe number 1 is the origin of all things. In this problem, you are given a target number $n$. You need to find the minimum number of integers whose sum equals $n$, where each integer in the set must consist only of the digit 1 (e.g., $1, 11, 111, 1111, \\dots$).ExampleTarget: $n = 35$Numbers: $11 + 11 + 11 + 1 + 1 = 35$Output: $5$ (This is the minimum count).Target: $n = 134$Numbers: $111 + 11 + 11 + 1 = 134$Output: $4$.💡 Key InsightThis is a variation of the Change-making Problem, a classic Dynamic Programming problem. Instead of standard currency coins, our "coins" are the set $\\{1, 11, 111, 1111, 11111, 111111\\}$.Steps:Define a DP array: Create dp\[MAXN] where dp\[i] stores the minimum count of "ones" numbers needed to sum up to $i$.Initialize: Set dp\[0] = 0 and all other values to infinity ($10^9$).Iterate and Update: For each "ones" number (coin), iterate through the DP array and update:$$dp\[i] = \\min(dp\[i], dp\[i - coin] + 1)$$Precompute: Since $n \\le 1,000,000$, precomputing the DP table once is efficient for handling multiple test cases.🚀 ComplexityTime Complexity: \* Precomputation: $O(n \\times k)$, where $k$ is the number of "ones" integers (very small, $\\approx 6$).Query: $O(1)$ per test case.Space Complexity: $O(n)$ to store the DP table.💻 ImplementationThis solution follows the standard brainsoft template.C++#include <bits/stdc++.h>



using namespace std;

using ll = long long;



const double PI = acos(-1);

const double EPS = 1e-9;

const int INF = 1e9;

const int MOD = 1e9 + 7;

const int MAXN = 1000005;



int dp\[MAXN];



// Precompute the minimum count for all values up to 1,000,000

void precompute() {

&nbsp;   vector<int> ones = {1, 11, 111, 1111, 11111, 111111};

&nbsp;   fill(dp, dp + MAXN, INF);

&nbsp;   dp\[0] = 0;

&nbsp;   

&nbsp;   for (int coin : ones) {

&nbsp;       for (int i = coin; i < MAXN; i++) {

&nbsp;           if (dp\[i - coin] != INF) {

&nbsp;               dp\[i] = min(dp\[i], dp\[i - coin] + 1);

&nbsp;           }

&nbsp;       }

&nbsp;   }

}



void idea() {

&nbsp;   int n;

&nbsp;   if (cin >> n) {

&nbsp;       if (n < MAXN) {

&nbsp;           cout << dp\[n] << "\\n";

&nbsp;       }

&nbsp;   }

}



int main() {

&nbsp;   // Fast I/O optimized for competitive programming

&nbsp;   ios::sync\_with\_stdio(0); 

&nbsp;   cin.tie(0);

&nbsp;   

&nbsp;   // Perform precomputation once

&nbsp;   precompute();

&nbsp;   

&nbsp;   int T = 1;

&nbsp;   cin >> T;



&nbsp;   for(int C = 1; C <= T; C++) {

&nbsp;       // Handle each query in O(1)

&nbsp;       idea();

&nbsp;   }

&nbsp;   return 0;

}

🏷️ TagsDynamic Programming Math Precomputation Greedy

