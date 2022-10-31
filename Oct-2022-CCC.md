# Oct 2022 : CCC SRMIST KTR : CPS 02 : Sprint II Coding

### P 501 - Orange Partitioning
```c
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>

int main() {
    int n;
    scanf("%d",&n);
    int a[n];
    for(int i=0;i<n;i++)
        scanf("%d",&a[i]);
    int k=0;
    for(int i=0; i<n-1; i++)
        {
            if (a[i]<= a[n-1])
            {
                int t = a[i];
                a[i]= a[k];
                a[k++] = t;
            }
        }
        int t = a[n-1];
        a[n-1]= a[k];
        a[k] = t;
    for(int i=0;i<n;i++)
        printf("%d ",a[i]);
  
    return 0;
}
```

### P 502 - Tisha and Orange Sorting
```python
def swap(a,b):
    temp = a
    a = b
    b = temp
    return a,b
def partition(a,l,r):
    x = a[r]
    i = l-1
    for j in range(l,r):
        if(a[j]<=x):
            i = i+1
            a[i],a[j] = swap(a[i],a[j])
    a[i+1],a[r] = swap(a[i+1],a[r])
    return (i+1)xq
def Quicksort(a,l,r):
    if l<r:
        p = partition(a,l,r)
        print(p)
        for i in range(l,r+1):
            print(a[i],end=" ")
        print()
        Quicksort(a,l,p-1)
        Quicksort(a,p+1,r)
n = int(input())
a = list(map(int,input().split()))
Quicksort(a,0,n-1)
```
