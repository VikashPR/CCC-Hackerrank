# R 101 : Eat Less
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)
``` python
n = int(input())
c = []
while not c:
    c = list(map(int,input().split()))
c.sort(reverse = True)
result = 0
for i in range(n):
    result += c[i]*(2**i)
print(result)
```

# R 102 : Highest Possible Product
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)
``` python
n = int(input())
arr = list(map(int, input().split()))

# Sort the array in non-decreasing order
arr.sort()

# Product of the last three numbers
prod1 = arr[n-1] * arr[n-2] * arr[n-3]

# Product of the first two (negative) numbers and the last number
prod2 = arr[0] * arr[1] * arr[n-1]

max_prod = max(prod1, prod2)
print(max_prod)

```

# R 103 : Pucca and The Card Game
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

``` python
import math

n = int(input())
a = list(map(int, input().split()))

i = 0
j = n - 1
k = 1
b = [0, 0]

while i <= j:
    if k == 1:
        k = 0
    else:
        k = 1
    if a[i] < a[j]:
        b[k] += a[j]
        j -= 1
    else:
        b[k] += a[i]
        i += 1

if b[0] >= b[1]:
    print("Pucca")
else:
    print("Garu")
```

# R 104 : Greedy Rayinshi
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

``` python
n = int(input())
cards = list(map(int, input().split()))

# Initialize scores for both players
rayinshi_score = 0
neechea_score = 0

# Rayinshi starts the game
turn = 'rayinshi'

# Keep playing the game until all cards have been picked
while cards:
    # Pick the card with the larger number
    if cards[0] > cards[-1]:
        picked_card = cards.pop(0)
    else:
        picked_card = cards.pop()

    # Add the picked card to the respective player's score
    if turn == 'rayinshi':
        rayinshi_score += picked_card
        turn = 'neechea'
    else:
        neechea_score += picked_card
        turn = 'rayinshi'

# Output the final scores
print(rayinshi_score, neechea_score)
```

# CCT A5 - Coins and Kefa
![CPP](https://img.shields.io/badge/C%2B%2B14-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)

``` cpp
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>
int cmp(const void *a,const void *b){
    return(*(int*)a-*(int*)b);
}
int main() {
int m,n;
    scanf("%d%d",&n,&m);
    int a[n];
    for(int i=0;i<n;i++){
        scanf("%d",&a[i]);
    }
    qsort(a,n,sizeof(int),cmp);
    int v;
    for(int i=0,j=0;i<m;i++){
        scanf("%d",&v);
        int s=0,f=0,c=0;
        while(s<v){
            if(j==n){
                f=1;
                break;
            }
            s=s+a[j];
            j++;
            c++;
            
        }
        if(f==1){
            printf("%d %d\n",-1,-1);
        }
        else
            printf("%d %d\n",c,s);
    }
    /* Enter your code here. Read input from STDIN. Print output to STDOUT */    
    return 0;
}
```

# R 105 : Mice reach the Home
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

``` python
n = int(input())
mice_pos = list(map(int, input().split()))
holes_pos = list(map(int, input().split()))

mice_pos.sort()
holes_pos.sort()

time_taken = max(abs(mice_pos[i] - holes_pos[i]) for i in range(n))

print(time_taken)
```
# R 502 : Hungry Monster Vs Trusty Blaster
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

``` python
n,hit,t=map(int,input().split())
l = sorted([int(i) for i in input().split()[0:n]])
res,h=0,0
for i in l:
    h = i // hit+(1 if i%hit else 0)
    if t >= h:
        t -= h
        res += 1
    else: break
print(res)
```

# R 802 : Jaime and the Tailor
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

``` python
n, p = map(int, input().split())
a = list(map(int, input().split()))

a.sort()
ans, prev = 0, -1 # to store the previous used buttons
for i in range(n):
    buttons = a[i] // p
    if buttons * p == a[i]: # this is to check if cost is completely divisble by p or not
        if buttons <= prev: # if equal to previous than answer will be the previous + 1 and our previous storing variable will be updated
            ans += prev + 1
            prev += 1
        else:
            ans += buttons
            prev = buttons
    else:
        buttons += 1
        if buttons <= prev:
            ans += prev + 1
            prev += 1
        else:
            ans += buttons
            prev = buttons

print(ans)
```

# R 301 : Empty Tank
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

``` python
n = int(input())
gas = list(map(int, input().split()))
cost = list(map(int, input().split()))

start_index = 0
end_index = 1
tank = gas[0] - cost[0]

while end_index != start_index or tank < 0:
    while tank < 0 and start_index != end_index:
        tank -= gas[start_index] - cost[start_index]
        start_index = (start_index + 1) % n

        if start_index == 0:
            print("-1")
            exit()

    tank += gas[end_index] - cost[end_index]
    end_index = (end_index + 1) % n

print(start_index)
```

# R 501 : Fractions of gold
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

``` python
from typing import List, Tuple

class ItemValue:
    def __init__(self, wt: int, val: int, ind: int):
        self.wt = wt
        self.val = val
        self.ind = ind
        self.cost = val/wt
 
def getMaxValue(wt: List[int], val: List[int], capacity: int) -> float:
    n = len(wt)
    iVal = [ItemValue(wt[i], val[i], i) for i in range(n)]
    iVal.sort(key=lambda x: x.cost, reverse=True)
    totalValue = 0
    for i in iVal:
        curWt = int(i.wt)
        curVal = int(i.val)
        if capacity - curWt >= 0:
            capacity -= curWt
            totalValue += curVal
        else:
            fraction = capacity / curWt
            totalValue += curVal * fraction
            capacity = int(capacity - (curWt * fraction))
            break
    if capacity > 0:
        return -1
    return totalValue
 
if __name__ == "__main__":
    n, capacity = map(int, input().split())
    wt = []
    val = []
    for i in range(n):
        w, v = map(int, input().split())
        wt.append(w)
        val.append(v)
    maxValue = getMaxValue(wt, val, capacity)
    if maxValue < 0:
        print("-1")
    else:
        print("{:.12f}".format(maxValue))
```

# N 501 - Ted Mobsy and Candies
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

``` python
import math

def binarysearch(arr, n, k):
    l = 0
    h = n - 1
    while l <= h:
        mid = math.floor((l+h)/2)
        if arr[mid] == k:
            return 1
        elif arr[mid] < k:
            l = mid + 1
        else:
            h = mid - 1
    return 0

n = int(input())
arr = list(map(int, input().split()))
m = int(input())
can = list(map(int, input().split()))

for i in range(m):
    if binarysearch(arr, n, can[i]):
        print("Happy Halloween!")
    else:
        print("Tricky!")

```
# N 502 - Dual match
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

``` python
n = int(input())
a = list(map(int, input().split()))
k = int(input())

# Sort the array in non-decreasing order
a.sort()

# Count the number of pairs (i, j) such that a[i] + a[j] = K
count = 0
for i in range(n):
    complement = k - a[i]
    left = 0
    right = n - 1
    while left <= right:
        mid = (left + right) // 2
        if a[mid] == complement:
            count += 1
            break
        elif a[mid] < complement:
            left = mid + 1
        else:
            right = mid - 1

# Print the TwoSum value
print(count)
```

# N 503 - Strength of 1s in unity
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)
``` python
def MaxBinaryStringLen(n, arr):
    left = right = ans = count = 0
    while right < n:
        if arr[right] == 1:
            count += 1
            right += 1
        else:
            ans = max(ans, count)
            count = 0
            right += 1
            left = right
    return max(ans, count)

n = int(input())
arr = list(map(int, input().split()))
print(MaxBinaryStringLen(n, arr))
```
# N 504 - Count the Lower elements
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)
``` python
from bisect import bisect_right

n, m = map(int, input().split())
a = list(map(int, input().split()))
b = list(map(int, input().split()))

a.sort()

for bj in b:
    i = bisect_right(a, bj)
    print(i, end=' ')

```
# P 505 : Shall we Merge?
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

``` python
def merge_sort_and_count_inversions(arr):
    if len(arr) <= 1:
        return arr, 0

    mid = len(arr) // 2
    left, left_count = merge_sort_and_count_inversions(arr[:mid])
    right, right_count = merge_sort_and_count_inversions(arr[mid:])
    merged, merged_count = merge_and_count_inversions(left, right)

    return merged, left_count + right_count + merged_count

def merge_and_count_inversions(left, right):
    i, j = 0, 0
    count = 0
    merged = []

    while i < len(left) and j < len(right):
        if left[i] <= right[j]:
            merged.append(left[i])
            i += 1
        else:
            merged.append(right[j])
            j += 1
            count += len(left) - i

    merged += left[i:]
    merged += right[j:]

    return merged, count

n = int(input())
a = [int(input()) for _ in range(n)]

_, count = merge_sort_and_count_inversions(a)

print(count)
```
# Z 461 : Salary Details
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)
``` python
n = int(input())

class Employee:
    def __init__(self, name, salary):
        self.name = name
        self.salary = salary

    def __lt__(self, other):
        if self.salary == other.salary:
            return self.name < other.name
        return self.salary < other.salary

employees = []
for i in range(n):
    name, salary = input().split()
    employees.append(Employee(name, int(salary)))

employees.sort()
for employee in employees:
    print(employee.name, employee.salary)
```

# Task Scheduling 1
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

``` python
def solve():
    n = int(input())
    t = list(map(int, input().split()))
    p = list(map(int, input().split()))

    tasks = sorted(zip(t, p), key=lambda x: -x[1])
    total_profit = 0
    schedule = [False] * n

    for task in tasks:
        deadline, profit = task
        for i in range(min(n, deadline)-1, -1, -1):
            if not schedule[i]:
                schedule[i] = True
                total_profit += profit
                break

    print(total_profit)

t = int(input())
for _ in range(t):
    solve()
```

# Task Scheduling 2
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

``` python
def max_profit(tasks):
    # Sort tasks by decreasing order of profit
    tasks = sorted(tasks, key=lambda x: x[1], reverse=True)
    n = len(tasks)
    # Initialize a set to keep track of the deadlines that are already used
    used = set()
    total_profit = 0
    for i in range(n):
        deadline, profit = tasks[i]
        # Try to find the nearest unused deadline for the current task
        j = deadline
        while j > 0 and j in used:
            j -= 1
        # If a deadline is found, add the current task to the schedule and update the used set
        if j > 0:
            used.add(j)
            total_profit += profit
    return total_profit


# Read the number of test cases
t = int(input())

# Process each test case
for i in range(t):
    # Read the input for the current test case
    n = int(input())
    t_vals = list(map(int, input().split()))
    p_vals = list(map(int, input().split()))
    tasks = [(t_vals[j], p_vals[j]) for j in range(n)]
    # Compute the maximum profit for the current test case and print the result
    result = max_profit(tasks)
    print(result)
```

# S 309 : Replace The Array
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

``` python
n = int(input())
arr = list(map(int, input().split()))

max_right = 0
for i in range(n-1, -1, -1):
    current = arr[i]
    arr[i] = max_right
    max_right = max(max_right, current)

arr[n-1] = 0
print(*arr)
```

# Z 301 Factorials Modding
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)
``` python
def factorial_mod(a, b, m):
    # Calculate (b+1) * (b+2) * ... * a modulo m
    prod = 1
    for i in range(b+1, a+1):
        prod = (prod * i) % m
    
    return prod % m

# Reading input
a, b, m = map(int, input().split())

# Calculating (a! / b!) % m
result = factorial_mod(a, b, m)

# Printing output
print(result)
```
# Z 550 String Repetition
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)
``` python
def smallest_repeating_string(s):
    n = len(s)
    for i in range(1, n+1):
        if n % i == 0:
            # Check if s can be generated by repeating a substring of length i
            sub = s[:i]
            if sub * (n // i) == s:
                return sub
    return s  # s itself is the smallest repeating string if no other substring works

# Example usage
s = input()
result = smallest_repeating_string(s)
print(result)
```

# Maximum Sum in an Array
![Java](https://img.shields.io/badge/Java15-ED8B00?style=for-the-badge&logo=java&logoColor=white)

``` java
import java.util.Scanner;

public class Solution {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();

        for (int i = 0; i < t; i++) {
            int n = scanner.nextInt();
            int[] arr = new int[n];

            for (int j = 0; j < n; j++) {
                arr[j] = scanner.nextInt();
            }

            // Compute maximum contiguous subarray using Kadane's algorithm
            int max_so_far = arr[0];
            int max_ending_here = arr[0];
            for (int j = 1; j < n; j++) {
                max_ending_here = Math.max(arr[j], max_ending_here + arr[j]);
                max_so_far = Math.max(max_so_far, max_ending_here);
            }
            int max_contiguous = max_so_far;

            // Compute maximum non-contiguous subarray
            int max_non_contiguous = 0;
            int max_negative = Integer.MIN_VALUE;
            boolean has_positive = false;
            for (int j = 0; j < n; j++) {
                if (arr[j] > 0) {
                    max_non_contiguous += arr[j];
                    has_positive = true;
                } else {
                    max_negative = Math.max(max_negative, arr[j]);
                }
            }
            if (!has_positive) {
                max_non_contiguous = max_negative;
            }

            System.out.println(max_contiguous + " " + max_non_contiguous);
        }

        scanner.close();
    }
}
```

# S 502 : Ways to Decode
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)
``` python
MOD = 1000000007

def num_decodings(s: str) -> int:
    n = len(s)
    if n == 0:
        return 0
    if n == 1:
        return 1
    count = [0] * (n + 1)
    count[0] = count[1] = 1
    for i in range(2, n + 1):
        if s[i - 1] >= '0':
            count[i] = count[i - 1]
        if s[i - 2] == '0' or s[i - 2] == '1' or (s[i - 2] == '2' and s[i - 1] < '6'):
            count[i] = (count[i] + count[i - 2]) % MOD
    return count[n]

s = input()
print(num_decodings(s))
```

# DP A1 Similarities Between Sequences
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

``` python
def F(A, B):
    n = len(A)
    m = len(B)
    dp = [[0] * (m+1) for _ in range(n+1)]
    result = 0
    for i in range(1, n+1):
        for j in range(1, m+1):
            if A[i-1] == B[j-1]:
                dp[i][j] = dp[i-1][j-1] + 1
                if dp[i][j] > result:
                    result = dp[i][j]
    return result

n = int(input())
A = list(map(int, input().split()))
m = int(input())
B = list(map(int, input().split()))

print(F(A, B))
```

# DP A2 Converting a Sequence to Another
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

``` python
n = int(input())
A = list(map(int, input().split()))
m = int(input())
B = list(map(int, input().split()))

# Initialize dp table
dp = [[0]*(m+1) for _ in range(n+1)]

# Base case
for i in range(n+1):
    dp[i][0] = i
for j in range(m+1):
    dp[0][j] = j

# Fill dp table
for i in range(1, n+1):
    for j in range(1, m+1):
        if A[i-1] == B[j-1]:
            dp[i][j] = dp[i-1][j-1]
        else:
            dp[i][j] = min(dp[i][j-1], dp[i-1][j], dp[i-1][j-1]) + 1

# Print result
print(dp[n][m])
```

# DP B1 More Similarities Between Sequences
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

``` python
n = int(input())
a = list(map(int, input().split()))
m = int(input())
b = list(map(int, input().split()))

# create a matrix to store the lengths of the longest common subsequence
# between prefixes of the sequences
dp = [[0] * (m + 1) for _ in range(n + 1)]

for i in range(1, n + 1):
    for j in range(1, m + 1):
        if a[i - 1] == b[j - 1]:
            dp[i][j] = dp[i - 1][j - 1] + 1
        else:
            dp[i][j] = max(dp[i - 1][j], dp[i][j - 1])

# the length of the longest common subsequence is the maximum value in the matrix
k = dp[n][m]

print(k)
```

# DP B2 Converting a Sequence to Another - 2
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

``` python
n = int(input())
a = list(map(int, input().split()))
m = int(input())
b = list(map(int, input().split()))
x, y, z = map(int, input().split())

# create a matrix to store the minimum cost of converting prefixes of A to prefixes of B
dp = [[0] * (m + 1) for _ in range(n + 1)]

# initialize the first row and column of the matrix with the cost of inserting/removing
# all elements in A or B up to that position
for i in range(n + 1):
    dp[i][0] = i * y
for j in range(m + 1):
    dp[0][j] = j * x

for i in range(1, n + 1):
    for j in range(1, m + 1):
        if a[i - 1] == b[j - 1]:
            dp[i][j] = dp[i - 1][j - 1]
        else:
            # compute the cost of the three possible operations and take the minimum
            insert_cost = dp[i][j - 1] + x
            remove_cost = dp[i - 1][j] + y
            modify_cost = dp[i - 1][j - 1] + z
            dp[i][j] = min(insert_cost, remove_cost, modify_cost)

# the minimum cost of converting A to B is stored in dp[n][m]
min_cost = dp[n][m]

print(min_cost)
```
# I M07 - Discover the Substring
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

``` python
string1 = input()
string2 = input()

count = 0
for i in range(len(string1)):
    if string1[i:].startswith(string2):
        count += 1
    
count1 = 0
for i in range(len(string2)):
    if string2[i:].startswith(string1):
        count1 += 1

if count1 > count:
    count = count1

print(count)
```

# CCT 04 - The Sprinklers
![CPP](https://img.shields.io/badge/C%2B%2B-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)
``` cpp
#include<iostream>
#include<cstdio>
#include<cmath>
#include<cstdlib>
#include<algorithm>
#include<cstring>
#include <queue>
#include <vector>
#include<bitset>
#include<map>
#include<deque>
using namespace std;
typedef long long LL;
const int maxn = 1e4+5;
const int mod = 77200211+233;
typedef pair<int,int> pii;
#define X first
#define Y second
#define pb push_back
//#define mp make_pair
#define ms(a,b) memset(a,b,sizeof(a))
const int inf = 0x3f3f3f3f;
#define lson l,m,2*rt
#define rson m+1,r,2*rt+1
typedef long long ll;
#define N 1000010
struct node {
    double a,b;
}square[10005];

int cmp(node x,node y){
    return x.b>y.b;
}

int main(){
#ifdef LOCAL
    freopen("in.txt","r",stdin);
#endif // LOCAL
    int n;
    double l,w;
    double r,p;
    while(~scanf("%d%lf%lf",&n,&l,&w)){
        int tot=0;
        for(int i=0;i<n;i++){
            scanf("%lf%lf",&p,&r);
            if(r<=w/2) continue;
            square[tot].a=p-sqrt(r*r-w*w/4);
            square[tot++].b=p+sqrt(r*r-w*w/4);
        }

        sort(square,square+tot,cmp);

        double st=0;
        int ans=0;

        while(st<l){
            int i;
            for(i=0;i<tot;i++){
                if(square[i].a<=st && square[i].b>st){
                    st=square[i].b;
                    ans++;
                    break;
                }
            }
            if(i==tot) break;
        }
        if(st<l){
            puts("-1");
        }else{
            printf("%d\n",ans);
        }
    }
    return 0;
}
```

