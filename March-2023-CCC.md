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
# Task Scheduling 1
![C](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)
```
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>

struct job
{
    int deadLine;
    int profit;
};

int compare(const void *x,const void *y)
{
    return (((struct job*)y)->profit) - (((struct job*)x)->profit);
}

int main() 
{
    int testCases;
    scanf("%d",&testCases);//Reading the value of testcases
    
    while(testCases--)
    {
        int n;
        scanf("%d",&n);//Reading total number of job records
        
        struct job jobDetails[n];
        int i, maximumDeadline = 0;
        //Reading job deadline
        for(i=0;i<n;i++)
        {
            scanf("%d",&jobDetails[i].deadLine);
            if(maximumDeadline < jobDetails[i].deadLine)
                maximumDeadline = jobDetails[i].deadLine;
        }
        //Reading profit values
        for(i=0;i<n;i++)
            scanf("%d",&jobDetails[i].profit);
        
        qsort(jobDetails,n,sizeof(struct job),compare);
        
        int task[1001] = {0}, j, maxProfit = 0;
        for(i=0;i<n;i++)
        {
            if(task[jobDetails[i].deadLine] == 0)
            {
                task[jobDetails[i].deadLine] = jobDetails[i].profit;
                maxProfit += jobDetails[i].profit;
            }
                
            else
            {
                int temp = jobDetails[i].profit;
                for(j=jobDetails[i].deadLine;j>0;j--)
                {
                    if(task[j]<temp)
                    {
                        task[j] = temp;
                        maxProfit += temp;
                        break;
                    }
                }
            }
        }
        printf("%d\n",maxProfit);        
    }
    
    return 0;
}
```
