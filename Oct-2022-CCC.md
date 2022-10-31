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

### P 503 - One Teacher Two Classes
```python
def mergeArrays(arr1, arr2, n1, n2, arr3):
    i = 0
    j = 0
    k = 0
    while i<n1 and j <n2:
        if arr1[i] < arr2[j]:
            arr3[k] = arr1[i]
            k += 1
            i += 1
        else:
            arr3[k] = arr2[j]
            k += 1
            j += 1
    while i < n1:
        arr3[k] = arr1[i]
        k += 1
        i += 1
    while j < n2:
        arr3[k] = arr2[j]
        k += 1
        j += 1

n = int(input())
a = list(map(int, input().split()))
m = int(input())
b = list(map(int, input().split()))
c = [0]*(n+m)
mergeArrays(a, b, n, m, c)
for i in range(n+m):
    print(c[i], end=" ")
```

### P 504 - Vasya and Birthday Presents
```python
def merge(start,mid,end,a):
    arr = [0] * (end-start+1)
    p=start
    q=mid+1
    k=0
    i=0
    
    for i in range(start,end+1):
        if p > mid:
            arr[k]=a[q]
            q+=1
        elif ( q > end):
            arr[k]=a[p]
            p+=1
        elif(a[p]>a[q]):
            arr[k]=a[p]
            p+=1
        else:
            arr[k]=a[q]
            q+=1
        k+=1
    
    for i in range(start,end+1):
        a[i]=arr[i-start]

def mergesort(start,end,a):
    if start<end:
        mid=(start+end)//2
        mergesort(start,mid,a)
        mergesort(mid+1,end,a)
        
        merge(start,mid,end,a)
    
t = int(input())
l = 0

while l<t:
    n = int(input())
    a = list(map(int,input().split()))
    start=0
    end=n-1
    mergesort(start,end,a)
    for i in range(n):
        print(a[i],end=" ")
    print()
    l+=1
```
### Q 101 - Trees - Inorder Traversal
```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <stdbool.h>
#include <math.h>
#define scan(x) scanf(" %d", &x)
struct TreeNode {
	int x;
	struct TreeNode* L;
	struct TreeNode* R;
};
typedef struct TreeNode TreeNode;
TreeNode* newNode(int _x) {
	TreeNode* node = (TreeNode*) malloc(sizeof(TreeNode));
	node->x = _x;
	node->L = node->R = NULL;
  return node;
}
TreeNode* insert(TreeNode* node, int val) {
	if (node == NULL) return newNode(val);
	if (val <= node->x) node->L = insert(node->L, val);
	else node->R = insert(node->R, val);
return node;
}

/*********************************************************/

void inorder(TreeNode* Root)
{

   if (Root == NULL) return;
    inorder(Root->L);
    printf("%d ", Root->x);
    inorder(Root->R);

}

/*******************************************************/

int main() {
	int val, N; scan(N);
	TreeNode* Root = NULL;
	for (int i = 1; i <= N; i++) {
		scan(val);
		Root = insert(Root, val);
	}
	inorder(Root);
}
```

### Q 102 - Trees - Preorder Traversal
``` c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <stdbool.h>
#include <math.h>
#define scan(x) scanf(" %d", &x)
struct TreeNode {
	int x;
	struct TreeNode* L;
	struct TreeNode* R;
};
typedef struct TreeNode TreeNode;
TreeNode* newNode(int _x) {
	TreeNode* node = (TreeNode*) malloc(sizeof(TreeNode));
	node->x = _x;
	node->L = node->R = NULL;
    return node;
}
TreeNode* insert(TreeNode* node, int val) {
	if (node == NULL) return newNode(val);
	if (val <= node->x) node->L = insert(node->L, val);
	else node->R = insert(node->R, val);
    return node;
}

/*******************************************************************/

void preorder(struct TreeNode* Root) {
    if (Root == NULL) return;
    printf("%d ", Root->x);
    preorder(Root->L);
    preorder(Root->R);
} 

/*******************************************************************/

int main() {
	int val, N; scan(N);
	TreeNode* Root = NULL;
	for (int i = 1; i <= N; i++) {
		scan(val);
		Root = insert(Root, val);
	}
	preorder(Root);
}
```
