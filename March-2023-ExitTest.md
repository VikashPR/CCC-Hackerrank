# Customer support for an e-commerce business

![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)
``` python
def matchingBraces(braces):
    result = []
    for string in braces:
        stack = []
        for brace in string:
            if brace in ['(', '[', '{']:
                stack.append(brace)
            elif brace in [')', ']', '}']:
                if not stack:
                    result.append('NO')
                    break
                elif brace == ')' and stack[-1] == '(':
                    stack.pop()
                elif brace == ']' and stack[-1] == '[':
                    stack.pop()
                elif brace == '}' and stack[-1] == '{':
                    stack.pop()
                else:
                    result.append('NO')
                    break
        else:
            if not stack:
                result.append('YES')
            else:
                result.append('NO')
    return result
```

# Dylan unexpectedly saw a present from one of his previous birthdays.
![Cpp](https://img.shields.io/badge/C%2B%2B-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)
``` cpp
#include <bits/stdc++.h>
using namespace std;
const int maxn = 1e5+5;
const int mod = 998244353;
int a[maxn];
long long dp[maxn][205][3];
int main() {
	int n;
	scanf("%d", &n);
	for(int i = 0; i < n; ++i)
		scanf("%d", &a[i]);
	if(a[0] != -1) 
		dp[0][a[0]][0] = 1;
	else {
		for(int i = 1; i <= 200; ++i)
			dp[0][i][0] = 1;
	}
	for(int i = 1; i < n; ++i) {
		int sum = 0;
		for(int j = 1; j <= 200; ++j) {
			if(a[i] == -1 || j == a[i]) {
				dp[i][j][0] = sum;
			}
			
			sum = (sum+dp[i-1][j][1]+dp[i-1][j][0]+dp[i-1][j][2])%mod;
		}
		sum = 0;
		for(int j = 1; j <= 200; ++j) {
			if(a[i] == -1 || j == a[i]) {
				dp[i][j][1] = (dp[i-1][j][0]+dp[i-1][j][1]+dp[i-1][j][2])%mod;
			}
			
		}
		for(int j = 200; j >= 1; --j) {
			if(a[i] == -1 || j == a[i]) {
				dp[i][j][2] = sum;
			}
			sum = (sum+dp[i-1][j][2]+dp[i-1][j][1])%mod;
		}
	}
	long long ans = 0;
	for(int i = 1; i <= 200; ++i) {
		ans = (ans+dp[n-1][i][1]+dp[n-1][i][2])%mod;
	}
	printf("%lld\n", ans);
	return 0;
}
```