# March 2023 CPS3 Exit Test 2

# Given a number of array

``` python
def balancedSum(arr):
    total_sum = sum(arr)
    left_sum = 0
    for i in range(len(arr)):
        if left_sum == total_sum - left_sum - arr[i]:
            return i
        left_sum += arr[i]
    return -1
```
