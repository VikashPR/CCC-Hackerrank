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

# S 501 : MAXIMUM SUBARRAY SUM
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

``` python
n = int(input())
arr = list(map(int, input().split()))

max_ending_here = max_so_far = arr[0]

for i in range(1, n):
    max_ending_here = max(arr[i], max_ending_here + arr[i])
    max_so_far = max(max_so_far, max_ending_here)

print(max_so_far)
```

# CCT A6 - Toad Jumps
![CPP](https://img.shields.io/badge/C%2B%2B14-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)

``` cpp
#include <stdio.h>
#include <stdlib.h>

int LS(int v[], int n) {
    if (n == 0) {
        return 0;
    }

    int* tail = (int*) malloc(n * sizeof(int));
    int length = 1;
    tail[0] = v[0];

    for (int i = 1; i < n; i++) {
        int j = 0;
        int left = 0, right = length;
        while (left < right) {
            int mid = (left + right) / 2;
            if (tail[mid] < v[i]) {
                j = mid + 1;
                left = mid + 1;
            } else {
                right = mid;
            }
        }
        if (j == length) {
            tail[length] = v[i];
            length += 1;
        } else {
            tail[j] = v[i];
        }
    }

    free(tail);

    return length - 1;
}

int main() {
    int n;
    scanf("%d", &n);

    int v[n];
    for (int i = 0; i < n; i++) {
        scanf("%d", &v[i]);
        v[i] = -v[i];
    }
    printf("%d\n", LS(v, n));

    return 0;
}
```

# Un ordered pairs
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)
``` python
n, k = map(int, input().split())
arr = list(map(int, input().split()))

# initialize a dictionary to keep track of the count of remainders
count = {}

# loop through the array and update the count of remainders
for i in range(n):
    rem = arr[i] % k
    if rem in count:
        count[rem] += 1
    else:
        count[rem] = 1

# initialize the number of pairs to 0
pairs = 0

# loop through the dictionary and count the number of pairs
for i in range(1, k//2+1):
    if i != k-i:
        pairs += count.get(i, 0) * count.get(k-i, 0)
    else:
        pairs += (count.get(i, 0) * (count.get(i, 0)-1)) // 2

# add the count of pairs with remainder 0
pairs += (count.get(0, 0) * (count.get(0, 0)-1)) // 2

# print the number of pairs
print(pairs)
```
# S 504 : The Bag of Gold Again
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

``` python
def max(a, b):
    return a if a > b else b

def knapSack(W, wt, val, n):
    K = [[0 for x in range(W+1)] for x in range(n+1)]
  
    for i in range(n+1):
        for w in range(W+1):
            if i == 0 or w == 0:
                K[i][w] = 0
            elif wt[i-1] <= w:
                K[i][w] = max(val[i-1] + K[i-1][w-wt[i-1]],  K[i-1][w])
            else:
                K[i][w] = K[i-1][w]
  
    return K[n][W]

t = int(input())
for i in range(t):
    n, W = map(int, input().split())
    val = []
    wt = []
    for j in range(n):
        w, v = map(int, input().split())
        wt.append(w)
        val.append(v)
    print(knapSack(W, wt, val, n))
```

# E05 - The Lower Case Letters
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

``` python
import sys
    
str = sys.stdin.readline().strip()
n = len(str)
ans = (n * (n + 1)) // 2
cnt = [0] * 26
    
for i in range(n):
    cnt[ord(str[i]) - ord('a')] += 1
    
for i in range(26):
    ans -= (cnt[i] * (cnt[i] - 1)) // 2 + cnt[i]
print(ans + 1)
```

# Are the Rooms Enough?
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

``` python
import heapq

n, k = map(int, input().split())

bookings = []
for i in range(n):
    arrival, departure = map(int, input().split())
    bookings.append((arrival, departure))

bookings.sort()

heap = []

for booking in bookings:
    while heap and heap[0] < booking[0]:
        heapq.heappop(heap)

    heapq.heappush(heap, booking[1])

    if len(heap) > k:
        print("no")
        exit()

print("yes")
```

# Greedy Florist
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

``` python
NK = input()

N = int(NK.partition(' ')[0])
K = int(NK.partition(' ')[2])

prices = [int(x) for x in input().strip().split(' ')]

if K == N:
    print(sum(prices))
else:
    prices.sort()
    friends = [[] for friend in range(K)]
    
    for friend in friends:
        friend.append(prices.pop())
    
    index = 0
    while prices:
        friends[index].append(prices.pop()*(1+len(friends[index])))
        index = (index + 1)%K
        
    total = 0
    for friend in friends:
        total += sum(friend)
        
    print(total)
```

# CC 201 - Unicell Division
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)


``` python
def minAmoeba(N): 
    if N == 1: 
        return 1 
    else: 
        if N % 2 == 0: 
            return minAmoeba(N // 2) 
        else: 
            return 1 + minAmoeba(N // 2) 
N = int(input()) 

print(minAmoeba(N)) 
```

# CC 202 : Destroy the City - 1
![CPP](https://img.shields.io/badge/C%2B%2B14-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)

``` cpp
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>
#include <limits.h>

long min(long x,long y)
{
    return x<=y ? x : y;
}

long minMovesToDestroy(int arr[],int l,int r,int v)
{
    if(l > r)
        return 0;
    int result = INT_MAX;
    for(int i=l;i<=r;i++)
    {
        if(arr[i] == v)
        {
            result = minMovesToDestroy(arr,l,i-1,v) + minMovesToDestroy(arr,i+1,r,v);
            break;
        }
    }
    if(result == INT_MAX)
        result = 1 + minMovesToDestroy(arr,l,r,v+1);
    return min(result,r-l+1);
}

int main() 
{
    int testCases;
    scanf("%d",&testCases);
    
    while(testCases--)
    {
        int buildingCount;
        scanf("%d",&buildingCount);
        
        int heights[buildingCount], i;
        for(i=0;i<buildingCount;i++)
            scanf("%d",&heights[i]);
        
        printf("%ld\n",minMovesToDestroy(heights,0,buildingCount-1,0));
    }
    return 0;
}
```

# K-Divisibility of an Array
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)
``` python
n, k = map(int, input().split())
a = list(map(int, input().split()))

rem_counts = [0] * k
for x in a:
    rem_counts[x % k] += 1

ans = 0
for i in range(1, (k+1)//2):
    ans += rem_counts[i] * rem_counts[k-i]

if k % 2 == 0:
    ans += (rem_counts[k//2] * (rem_counts[k//2] - 1)) // 2

ans += (rem_counts[0] * (rem_counts[0] - 1)) // 2

print(ans)
```

# T 101 : Gunpreet and Stairs
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

``` python
N = int(input())

dp = [0] * (N + 1)
dp[1], dp[2], dp[3] = 1, 2, 4

for i in range(4, N+1):
    dp[i] = dp[i-1] + dp[i-2] + dp[i-3]

print(dp[N])
```

# T 102 : Interesting Series
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)




``` python
F0, F1, F2, N = map(int, input().split())

dp = [0] * (N + 1)
dp[0], dp[1], dp[2] = F0, F1, F2

for i in range(3, N+1):
    dp[i] = dp[i-1] ^ dp[i-2] + dp[i-3]

print(dp[N])

```

# Z 560 : N Queens!
![CPP](https://img.shields.io/badge/C%2B%2B14-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)
``` cpp
#include <iostream>
using namespace std;

bool issafe(int **arr, int x, int y, int n)

{
    for (int row = 0; row < x; row++)
    {
        if (arr[row][y] == 1)
        {
            return 0;
        }
    }

    int row = x;
    int col = y;
    while (row >= 0 && col >= 0)
    {
        if (arr[row][col] == 1)
        {
            return 0;
        }

        row--;
        col--;
    }

    row = x;
    col = y;
    while (row >= 0 && col < n)
    {
        if (arr[row][col] == 1)
        {
            return 0;
        }
        row--;
        col++;
    }
    return 1;
}

bool nqueen(int **arr, int x, int n)

{
    if (x >= n)
    {
        return 1;
    }

    for (int col = 0; col < n; col++)
    {
        if (issafe(arr, x, col, n))
        {
            arr[x][col] = 1;
            if (nqueen(arr, x + 1, n))
            {
                return 1;
            }
            arr[x][col] = 0;
        }
    }

    return 0;
}

int main()

{
    int n;

    cin >> n;

    int **arr = new int *[n];

    for (int i = 0; i < n; i++)

    {
        arr[i] = new int[n];

        for (int j = 0; j < n; j++)

        {

            arr[i][j] = 0;
        }
    }

    if (nqueen(arr, 0, n))

    {
        for (int i = 0; i < n; i++)
        {
            for (int j = 0; j < n; j++)

            {

                cout << arr[i][j] << " ";
            }

            cout << endl;
        }
    }
    else

    {
        cout << "Not possible" << endl;
    }
}
```

# T 109 High rated child
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)
``` python
n = int(input())
ratings = list(map(int, input().split()))

candies = [1] * n

# Traverse from left to right
for i in range(1, n):
    if ratings[i] > ratings[i-1]:
        candies[i] = candies[i-1] + 1

# Traverse from right to left
for i in range(n-2, -1, -1):
    if ratings[i] > ratings[i+1]:
        candies[i] = max(candies[i], candies[i+1] + 1)

# Calculate the sum of candies
min_candies = sum(candies)

print(min_candies)
```


# G 305 Can you reach them?
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)
``` python
n, m = map(int, input().split())

adj_list = [[] for _ in range(n+1)]

for _ in range(m):
    u, v = map(int, input().split())
    adj_list[u].append(v)
    adj_list[v].append(u)

head = int(input())

# Perform DFS starting from the head node
visited = [False] * (n+1)

def dfs(node):
    visited[node] = True
    for neighbor in adj_list[node]:
        if not visited[neighbor]:
            dfs(neighbor)

dfs(head)

# Count the number of unreachable nodes
unreachable_nodes = 0
for i in range(1, n+1):
    if not visited[i]:
        unreachable_nodes += 1

print(unreachable_nodes)
```

# Z 449 Reversal of the ranks
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)
``` python
n = int(input())
rank = list(map(int, input().split()))

ans = [0] * n

for i in range(n):
    cnt = ans[:i].count(0)
    ans[i] = rank[i] + cnt + 1
    for j in range(i):
        if ans[j] >= ans[i]:
            ans[j] += 1

print(*ans)
```

# Castles and Jealousy
![CPP](https://img.shields.io/badge/C%2B%2B14-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)
``` cpp
#include <iostream>
#include <algorithm>
#include <vector>

using namespace std;

bool can_assign_fairies(vector<int>& castles, int c, int d) {
    int last_castle = castles[0];
    int assigned = 1;
    for (int i = 1; i < castles.size(); i++) {
        if (castles[i] - last_castle >= d) {
            last_castle = castles[i];
            assigned++;
            if (assigned == c) {
                return true;
            }
        }
    }
    return false;
}

int main() {
    int t;
    cin >> t;
    while (t--) {
        int n, c;
        cin >> n >> c;
        vector<int> castles(n);
        for (int i = 0; i < n; i++) {
            cin >> castles[i];
        }
        sort(castles.begin(), castles.end());
        int lo = 0, hi = castles[n-1] - castles[0];
        while (lo < hi) {
            int mid = lo + (hi - lo + 1) / 2;
            if (can_assign_fairies(castles, c, mid)) {
                lo = mid;
            } else {
                hi = mid - 1;
            }
        }
        cout << lo << endl;
    }
    return 0;
}
```

# CCT 05 - Petya's Move
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)
``` python
import itertools

def calculate_probability(actual_directions, remembered_directions):
    # Find the number of '?' characters in the remembered_directions string
    num_question_marks = remembered_directions.count('?')
    
    # Generate all possible combinations of coin toss outcomes for the '?' characters
    coin_tosses = itertools.product(['+', '-'], repeat=num_question_marks)
    
    # Keep track of the number of outcomes that result in Kefa ending up in the correct position
    correct_outcomes = 0
    
    for coin_toss_result in coin_tosses:
        # Create a new string by replacing '?' characters with the corresponding coin toss result
        trial_directions = remembered_directions.replace('?', '{}').format(*coin_toss_result)
        
        # Check if Kefa ends up in the correct position after following the actual and trial directions
        if get_final_position(actual_directions) == get_final_position(trial_directions):
            correct_outcomes += 1
    
    # Return the probability of ending up in the correct position
    return correct_outcomes / (2**num_question_marks)

def get_final_position(directions):
    # Calculate Kefa's final position after following the given directions
    return directions.count('+') - directions.count('-')

# Read the input strings
actual_directions = input().strip()
remembered_directions = input().strip()

# Calculate and print the probability of Kefa ending up in the correct position
print('{:.6f}'.format(calculate_probability(actual_directions, remembered_directions)))
```
# An array of Non zero and Non Negative Numbers
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)
``` python
n = int(input())
a = list(map(int, input().split()))

dp = [0] * n
dp2 = [0] * n

dp[0] = a[0]
dp2[0] = 0

for i in range(1, n):
    dp[i] = dp2[i-1] + a[i]
    dp2[i] = max(dp[i-1], dp2[i-1])

print(max(dp[-1], dp2[-1]))
```

# G 302 - Maze and repeat
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

``` python
def find_largest_cycle(n, edges):
    largest_cycle = 0
    visited = set()
    for i in range(n):
        if i not in visited:
            slow = i
            fast = i
            cycle_length = 0
            while edges[fast] != -1:
                slow = edges[slow]
                fast = edges[edges[fast]]
                cycle_length += 1
                if slow == fast:
                    largest_cycle = max(largest_cycle, cycle_length)
                    visited.add(slow)
                    break
    return largest_cycle

# Read input
n = int(input())
edges = list(map(int, input().split()))

# Call function and print output
print(find_largest_cycle(n, edges))

```

# G 303 Maze Entry - Maze Exit
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)
``` python
n = int(input())
edges = list(map(int, input().split()))

in_degrees = [0] * n

# Count incoming edges for each cell
for i in range(n):
    if edges[i] != -1:
        in_degrees[edges[i]] += 1

# Find the cell with maximum incoming edges
max_in_degrees = max(in_degrees)
max_in_degrees_index = in_degrees.index(max_in_degrees)

print(max_in_degrees_index)
```

# G 306 Bi-Directional BFS
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)


``` python
from collections import deque

n = int(input())
adj = [[] for _ in range(n+1)]

# Read edges of the tree
for i in range(n-1):
    u, v = map(int, input().split())
    adj[u].append(v)
    adj[v].append(u)

d = int(input())

# Breadth-first search
q = deque([1])  # start from root node
level = 0
count = 0
visited = [False] * (n+1)
visited[1] = True

while q:
    size = len(q)
    level += 1
    if level == d:
        count = size
        break
    for _ in range(size):
        node = q.popleft()
        for neighbor in adj[node]:
            if not visited[neighbor]:
                visited[neighbor] = True
                q.append(neighbor)

print(count)
```

# CC 302 - Into the Forest
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

```python
def dfs(node, visited, adj_list):
    visited[node] = True
    size = 1
    for neighbour in adj_list[node]:
        if not visited[neighbour]:
            size += dfs(neighbour, visited, adj_list)
    return size

n, m = map(int, input().split())

adj_list = [[] for _ in range(n)]
for _ in range(m):
    u, v = map(int, input().split())
    adj_list[u-1].append(v-1)
    adj_list[v-1].append(u-1)

visited = [False] * n
tree_sizes = []
num_trees = 0

for i in range(n):
    if not visited[i]:
        size = dfs(i, visited, adj_list)
        num_trees += 1
        tree_sizes.append(size)

print(max(tree_sizes), min(tree_sizes), num_trees)
```

# CC 303 - Time = Speed x Distance
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

``` python
import heapq

def dijkstra(graph, start, end):
    distances = {node: float('inf') for node in graph}
    distances[start] = 0
    queue = [(0, start)]
    while queue:
        current_distance, current_node = heapq.heappop(queue)
        if current_node == end:
            return current_distance
        if current_distance > distances[current_node]:
            continue
        for neighbour, weight in graph[current_node].items():
            distance = current_distance + weight
            if distance < distances[neighbour]:
                distances[neighbour] = distance
                heapq.heappush(queue, (distance, neighbour))
    return -1

n, m, p, q, t = map(int, input().split())

graph = {i: {} for i in range(1, n+1)}
for _ in range(m):
    u, v = map(int, input().split())
    if u == v:
        continue
    graph[u][v] = t
    graph[v][u] = t

result = dijkstra(graph, p, q)
print(result)
```

# CC 304 - Time = Distance x Speed
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

``` python
import heapq

def dijkstra(graph, start, end):
    distances = {node: float('inf') for node in graph}
    distances[start] = 0
    queue = [(0, start)]
    while queue:
        current_distance, current_node = heapq.heappop(queue)
        if current_node == end:
            return current_distance
        if current_distance > distances[current_node]:
            continue
        for neighbour, weight in graph[current_node].items():
            distance = current_distance + weight
            if distance < distances[neighbour]:
                distances[neighbour] = distance
                heapq.heappush(queue, (distance, neighbour))
    return -1

n, m, p, q, t = map(int, input().split())

graph = {i: {} for i in range(1, n+1)}
for _ in range(m):
    u, v, w = map(int, input().split())
    if u == v:
        continue
    graph[u][v] = w * t
    graph[v][u] = w * t

result = dijkstra(graph, p, q)
print(result)
```

# G 304 Maximizing Special Nodes
![C++](https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)

``` cpp
#include <cmath>
#include <cstdio>
#include <vector>
#include <iostream>
#include <algorithm>
using namespace std;
vector <int> g[1005],rg[1005];
int n;
int solve(vector<int>G[])
{
    int a[1005]={0};
    for(int i=1;i<=n;i++)
    {
        for(auto node:G[i]){
        if(G[node].size()==0)
            a[i]=1;
        }
    }
    int ans=0;
    for(int i=1;i<=n;i++)
        ans+=a[i];
    return ans;
}

int main() {
    int e;
    cin>>n>>e;
    for(int i=1;i<=e;i++)
    {
        int x,y;
        cin>>x>>y;
        g[x].push_back(y);
        rg[y].push_back(x);
    }
    int a=solve(g);
    int b=solve(rg);
    cout<<max(a,b);
    return 0;
}
```

# CCT B2 - Maze and co-ordinates
![C++](https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)

``` cpp
#include <iostream>
#include <vector>
#include <stack>
using namespace std;

bool can_reach_end(vector<vector<int>> maze, pair<int, int> start, pair<int, int> end) {
    int n = maze.size();
    int m = maze[0].size();
    vector<vector<bool>> visited(n, vector<bool>(m, false));
    stack<pair<int, int>> s;
    s.push(start);
    while (!s.empty()) {
        int x = s.top().first;
        int y = s.top().second;
        s.pop();
        if (x == end.first && y == end.second) {
            return true;
        }
        visited[x][y] = true;
        int dx[] = {0, 1, 0, -1};
        int dy[] = {1, 0, -1, 0};
        for (int i = 0; i < 4; i++) {
            int new_x = x + dx[i];
            int new_y = y + dy[i];
            if (new_x >= 0 && new_x < n && new_y >= 0 && new_y < m && !visited[new_x][new_y] && maze[new_x][new_y] <= maze[x][y]) {
                s.push(make_pair(new_x, new_y));
            }
        }
    }
    return false;
}

int main() {
    int n, m;
    cin >> n >> m;
    pair<int, int> start;
    cin >> start.first >> start.second;
    start.first--;
    start.second--;
    pair<int, int> end;
    cin >> end.first >> end.second;
    end.first--;
    end.second--;
    vector<vector<int>> maze(n, vector<int>(m));
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < m; j++) {
            cin >> maze[i][j];
        }
    }
    if (can_reach_end(maze, start, end)) {
        cout << "Hie Barua" << endl;
    } else {
        cout << "No Chance" << endl;
    }
    return 0;
}
```

# G M03 - Grids of single digits
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

```python
def isRowValid(sudoku,row_num):
    return len((sudoku[row_num])) == 9

def isColValid(sudoku,col_num):
    col = [item[col_num] for item in sudoku]
    return len(set(col)) == 9

def isCelValid(sudoku,cel_row, cel_col):
    vals = sudoku[cel_row][cel_col: cel_col+3]
    vals.extend(sudoku[cel_row+1] [cel_col: cel_col+3])
    vals.extend(sudoku[cel_row+2] [cel_col: cel_col+3])
    return len(set(vals)) == 9

def validateSudoku(sudoku):
    
    for i in range(0,9):
        if not isRowValid(sudoku,i):
            return False
        if not isColValid(sudoku,i):
            return False
    for i in range(0, 9, 3):
        for j in range(0, 9, 3):
            # print(i, j)
            if not isCelValid(sudoku,i, j):
                return False
    return True

 

t=int(input())
while t:
    sudoku=[]
    for i in range(9):
            sudoku.append(list(map(int,(input().split()))))
            
    if (validateSudoku(sudoku)):
        print("Valid")
    else:
        print("inValid")
    
    t-=1
```

# Z 560 : Ruling Queens
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

```python
def solveNQueens(n):
    res = []
    dfs([-1]*n, 0, [], res)
    return res

def dfs(nums, index, path, res):
    if index == len(nums):
        res.append(path)
        return  
    for i in range(len(nums)):
        nums[index] = i
        if valid(nums, index):  
            tmp = "0"*len(nums)
            dfs(nums, index+1, path+[tmp[:i]+"1"+tmp[i+1:]], res)

def valid(nums, n):
    for i in range(n):
        if abs(nums[i]-nums[n]) == n -i or nums[i] == nums[n]:
            return False
    return True

n=int(input())
for i in solveNQueens(n)[0]:
    for j in i:
        print(j,end=' ')
    print()
```
