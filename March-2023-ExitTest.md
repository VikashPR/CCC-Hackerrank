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

# Given an integer, n, determine the following ...
![Cpp](https://img.shields.io/badge/C%2B%2B-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)

``` cpp
vector<int> getOneBits(int n) {
    int count = 0;
    vector<int> bits;
    int pos = 1;
    while (n > 0) {
        if (n & 1) {
            count++;
            bits.push_back(1);
        }else{
                bits.push_back(0);
        }
        pos++;
        n >>= 1;
    }
    reverse(bits.begin(), bits.end());
    for(auto it : bits)cout<<it<<" ";
    cout<<endl;
    vector<int> result;
    result.push_back(count);
    for (int i = 0; i < bits.size(); i++) {
            if(bits[i] == 1)
                result.push_back(i+1);
    }
    return result;
}
```
# Given a string, create a new string made up of its last two letters, reversed...
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

``` python
def lastLetters(word):
    last_two_letters = word[-2:][::-1]
    return " ".join(last_two_letters)
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

# Vrutik has fallen in love with his long time bestie Radhika.
![Cpp](https://img.shields.io/badge/C%2B%2B-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)

``` cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int v;
    cin >> v;
    vector<int> a(9);
    for (int i = 0; i < 9; i++) {
        cin >> a[i];
    }

    int min_a = *min_element(a.begin(), a.end());
    if (min_a > v) {
        cout << "-1\n";
        return 0;
    }

    int max_d = v / min_a;
    string ans(max_d, '0' + distance(a.begin(), find(a.begin(), a.end(), min_a)) + 1);
    v -= max_d * min_a;

    for (int i = 0; i < max_d; i++) {
        for (int j = 8; j >= 0; j--) {
            if (v + min_a >= a[j]) {
                ans[i] = '0' + j + 1;
                v -= a[j] - min_a;
                break;
            }
        }
    }

    cout << ans << endl;

    return 0;
}
```

# Exam time!. Ram needs to score 100 points on CS exam...
![Cpp](https://img.shields.io/badge/C%2B%2B-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)

``` cpp
//Exam Time
#include<bits/stdc++.h>

using namespace std;

string a, b, c(256, 0);
int n, i, j, al, bl, y;

int main() {
  cin >> a;
  for (char i: a) c[i] = 1;
  cin >> a;
  al = a.size();
  cin >> n;

  while (n--) {
    cin >> b;
    bl = b.size();
    y = 1;
    for (i = j = 0; y && i < al; i++) {
      if (a[i] == '*') {
        while (j < bl - (al - i - 1))
          if (c[b[j++]]) y = 0;
      } else {
        if (a[i] == '?' ? c[b[j]] : a[i] == b[j])
          j < bl ? j++ : y = 0;
        else
          y = 0;
      }
    }
    if (j < bl) y = 0;
    cout << (y ? "YES\n" : "NO\n");
  }
}
```
# Harry is riding buckbeak for the first time
![c](https://img.shields.io/badge/C-00599C?style=for-the-badge&logo=c&logoColor=white)
```c
LinkedListNode* addLists(LinkedListNode* list1, LinkedListNode* list2) {
    int a[100],b[100];
    int i=0,j=0;
    struct LinkedListNode *temp=(struct LinkedListNode *)malloc(sizeof(struct LinkedListNode));
    
    while(list1)
    {
        a[i++]=list1->val;
        list1=list1->next;
    }
    while(list2)
    {
        b[j++]=list2->val;
        list2=list2->next;
    }
    int sizea=i,sizeb=j;
    if(i>=j)    {
    while(i&&j)
    {
        a[--i]+=b[--j];
    }
   for(int x=sizea-1;x>0;x--)
   {
       if(a[x]>=10)
       {
           a[x]%=10;
           a[x-1]+=1;
       }
   }
      //  for(int x=0;x<sizea;x++)
      //      printf("%d ",a[x]);
    }
    else
    {
         while(i&&j)
    {
        b[--j]+=a[--i];
    }
   for(int x=sizeb-1;x>0;x--)
   {
       if(b[x]>=10)
       {
           b[x]%=10;
           b[x-1]+=1;
       }
   }
       // for(int x=0;x<sizeb;x++)
       //    printf("%d ",b[x]);
        for(int y=0;y<sizeb;y++)
            a[y]=b[y];
        
    }
    int maxs=sizea>=sizeb?sizea:sizeb;
    // printf("%d ",maxs);
     LinkedListNode *temp1,*temphead=NULL;
    for(int co=maxs-1;co>=0;co--)
    {
       /*temp->val=a[co];
      temp=temp->next;
        if(temp==NULL)
            break;*/
       temp1=( LinkedListNode *)malloc(sizeof( LinkedListNode));
        temp1->val=a[co];
        temp1->next=temphead;
        temphead=temp1;
      
    }

    return temphead;
}
```