# March 2023 CPS3 Exit Test 2

# Given a number of array
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

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

# Application logs are usefull in analyzing
![C++](https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)

``` cpp
#include <iostream>
#include <vector>
#include <algorithm>
#include <map>
using namespace std;
// required function
vector<string> processLogs(vector<string> logs, int threshold) {
  map<int, int> mp; // map to count transactions of each user
  // loop through the logs
  for(auto x: logs) {
    // extract users from string
    int sp1 = -1, sp2 = -1;
    for(int i = 0; i < x.size(); ++i) {
      if(x[i] == ' ') {
        if(sp1 == -1) sp1 = i;
        else sp2 = i;
      } 
    }  
    int from = stoi(x.substr(0, sp1));
    int to = stoi(x.substr(sp1 + 1, sp2 - sp1 - 1));
    // cout << from << " " << to << " " << endl;
    // increse count for different users
    if(to == from) {
      mp[to]++;
    }
    else {
      mp[to]++;
      mp[from]++;
    }
  }
  vector<string> ans;
  // loop through the map and extract users with count > threshold
  for(auto x: mp) {
    if(x.second >= threshold) {
      ans.push_back(to_string(x.first));
    }
  }
  // no need to sort as map is already sorted a/c to key
  return ans;
}
// driver program
int main() {
  // process user input
  int n, threshold;
  cin >> n;
  cin.ignore();
  vector<string> logs(n);
  for(int i = 0; i < n; ++i) {
    string temp;
    getline(cin, temp);
    logs[i] = temp;
  }
  cin >> threshold;
  // call the function
  vector<string> ans = processLogs(logs, threshold);
  // print the output
  for(auto s: ans) cout << s << endl;
}
```

# A binary number is a combination 
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

[Reference Tharunn25 ccc-exit-test](https://github.com/Tharunn25/ccc-exit-test/blob/main/a%20binary%20number%20is%20a%20combination.py)

``` python
def fourthBit(number):
    # Convert decimal number to binary
    binary = ""
    while number > 0:
        binary = str(number % 2) + binary
        number //= 2
    # Pad binary representation with leading zeros if necessary
    binary = binary.zfill(15)
    # Extract 4th digit from the right
    fourth_digit = binary[-4]
    # Convert fourth digit to integer and return it
    return int(fourth_digit)
```

# A k-subarray of an array is
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

[Reference Tharunn25 ccc-exit-test](https://github.com/Tharunn25/ccc-exit-test/blob/main/a%20k-subarray%20of%20an%20array%20is.pypy)

``` python
def kSub(k, nums):
    count = 0
    prefix_sum = [0] * (len(nums) + 1)
    frequency = [0] * k
    frequency[0] = 1
    for i in range(1, len(prefix_sum)):
        prefix_sum[i] = prefix_sum[i-1] + nums[i-1]
        remainder = prefix_sum[i] % k
        count += frequency[remainder]
        frequency[remainder] += 1
    return count
```

# Alex has to complete multi level game
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

[Reference Tharunn25 ccc-exit-test](https://github.com/Tharunn25/ccc-exit-test/blob/main/alex%20has%20to%20complete%20%20multi%20level%20game.py)

``` python
def maximumPoints(k, costs):
    n = len(costs)
    points = 0
    total_cost = 0
    skipped_cost = float('inf')
    skipped = False
    for i in range(n):
        if not skipped and total_cost + costs[i] <= k:
            total_cost += costs[i]
            points += 1
        elif skipped and total_cost + costs[i] + skipped_cost <= k:
            total_cost += costs[i]
            skipped_cost = min(skipped_cost, costs[i-1])
        else:
            skipped = True
            skipped_cost = min(skipped_cost, costs[i])
    return points
```

# Owner of the construction company
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

[Reference Tharunn25 ccc-exit-test](https://github.com/Tharunn25/ccc-exit-test/blob/main/owner%20of%20the%20construction%20company.py)

``` python
def maxProfit(costPerCut, salePrice, len):
    # Find the shortest rod length
    shortest_len = min(len)
    
    # Iterate over all possible sale lengths that are factors of the shortest length
    max_profit = 0
    for i in range(1, shortest_len+1):
        if shortest_len % i == 0:
            # Calculate the number of rods that can be cut to the sale length
            uniform_rods = 0
            for j in len:
                uniform_rods += j // i
            
            # Calculate the total length of all the rods that will be sold
            total_length = uniform_rods * i
            
            # Calculate the number of cuts needed
            total_cuts = 0
            for j in len:
                # Count the number of cuts needed for each rod
                cuts = (j // i) - 1 if j % i == 0 else j // i
                total_cuts += cuts
            
            # Calculate the profit for this sale length
            profit = uniform_rods * i * salePrice - total_cuts * costPerCut
            
            # Update the maximum profit
            max_profit = max(max_profit, profit)
    
    return max_profit
```

# A new method has to be derived for decrypting
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

[Reference Tharunn25 ccc-exit-test](https://github.com/Tharunn25/ccc-exit-test/blob/main/a%20new%20method%20has%20to%20be%20derived%20for%20decrypting.py)

``` python
def findIndices(n, query):
    arr = [None] * n
    for L, R in query:
        s = sum(arr[L:R+1])
        if arr[L] is None:
            arr[L] = s - sum(arr[:L])
        for i in range(L+1, R+1):
            if arr[i] is None:
                arr[i] = s - arr[i-1]
    X = [i for i in range(n) if arr[i] is not None]
    return sorted(X) if X else [-1]
```
# In a Square Grid
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)
```python
def onesGroups(grid, queries):
    n = len(grid)
    visited = [[False]*n for _ in range(n)]
    groups = []

    def dfs(r, c, group):
        visited[r][c] = True
        group.append((r,c))
        for dr, dc in [(1,0), (-1,0), (0,1), (0,-1)]:
            nr, nc = r+dr, c+dc
            if nr>=0 and nr<n and nc>=0 and nc<n and grid[nr][nc]==1 and not visited[nr][nc]:
                dfs(nr, nc, group)

    # find all groups of connected 1's
    for r in range(n):
        for c in range(n):
            if grid[r][c] == 1 and not visited[r][c]:
                group = []
                dfs(r, c, group)
                groups.append(group)

    # count number of groups with sizes that match each query
    res = []
    for q in queries:
        count = sum(1 for group in groups if len(group) == q)
        res.append(count)

    return res
```

# A subsequence is a sequence of letters
![C++](https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)

### 13 / 15 test cases passed

``` cpp
#include<iostream>
#include<string>
#include<vector>
#include<cstring>
using namespace std;

string vowel = "aeiouy";

int vpos(char c)
{
    for (int i = 0; i < 6; ++i)
        if (c == vowel[i])
            return i;
    return -1;
}

int magical(string s)
{
    int l = s.length();
    int previndex[6];
    memset(previndex, -1, sizeof(previndex));  // initialize to -1
    vector<int> len(l, 0);
    int i = 0, maxlen = 0;

    // finding first 'a'
    while (s[i] != 'a')
    {
        ++i;
        if (i == l)
            return 0;
    }

    previndex[0] = i;       //prev index of 'a'
    len[i] = 1;

    for ( ++i; i < l; ++i)
    {
        if (vpos(s[i]) >= 0)    // a vowel
        {
            /* Need to append to longest subsequence on its left, only for this vowel (for any vowels) and 
             * its previous vowel (if it is not 'a')
                This important observation makes it O(n) -- differnet from typical LIS
            */
            if (previndex[vpos(s[i])] >= 0)
                len[i] = 1+len[previndex[vpos(s[i])]];

            previndex[vpos(s[i])] = i;

            if (s[i] != 'a')
            {
                if (previndex[vpos(s[i])-1] >= 0)
                    len[i] = max(len[i], 1+len[previndex[vpos(s[i])-1]]);
            }

            maxlen = max(maxlen, len[i]);
        }
    }
    return maxlen;
}

int main()
{
    string s;
    cin>>s;
    cout << magical(s);
    return 0;
}

```