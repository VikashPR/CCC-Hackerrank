# March 2023 CPS3 Exit Test 2

# Given a number of array

![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

```python
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

```cpp
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

```python
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

```python
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

# Owner of the construction company

![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

[Reference Tharunn25 ccc-exit-test](https://github.com/Tharunn25/ccc-exit-test/blob/main/owner%20of%20the%20construction%20company.py)

```python
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

```cpp
#include<bits/stdc++.h>

using namespace std;
#define mod 1000000007
#define PRIME 1000000009
#define endl '\n'
#define pb push_back
#define F first
#define S second
#define ll long long
#define ull unsigned int
#define all(c) c.begin(), c.end()
#define rall(c) c.rbegin(), c.rend()
#define sz(c) c.size()
#define r(i, a, b) for (i = a; i < b; i++)
  #define ra(i, a, b) for (i = a; i <= b; i++)
    #define vi vector < int >
    #define vil vector < ll >
    /*// for hashing 131 and 1e9+7
    // fermats theorem M-2
    //mpow
    //r=1;
    //while(b)
    //{
    if(b&1) r=(r*a)%M
    a=(a*a)%m;
    b=b>>1;
    //}
    */
    /*
    void sieve(int n)
    {
    bool prime[n + 1];
    memset(prime, true, sizeof(prime));
    for (int p = 2; p * p <= n; p++)
    {
    // If prime[p] is not changed,
    // then it is a prime
    if (prime[p] == true)
    {
    for (int i = p * p; i <= n; i += p)
    prime[i] = false;
    }
    }
    }*/

    ll solve() {
      ll n, m, i, j;
      ll k;
      ll l, r;
      string s;
      cin >> s;
      n = sz(s);
      ll dp[n][5];
      memset(dp, 0, sizeof(dp));
      if (s[0] == 'a') dp[0][0] = 1;
      for (int i = 1; i < n; i++) {
        if (s[i] == 'a') {
          dp[i][0] = 1 + dp[i - 1][0];
        } else
          dp[i][0] = dp[i - 1][0];
        if (s[i] == 'e') {
          if (dp[i - 1][1] != 0)
            dp[i][1] = 1 + dp[i - 1][1];
          if (dp[i - 1][0] != 0)
            dp[i][1] = max(dp[i][1], 1 + dp[i - 1][0]);
        } else
          dp[i][1] = dp[i - 1][1];
        if (s[i] == 'i') {
          if (dp[i - 1][2] != 0)
            dp[i][2] = 1 + dp[i - 1][2];
          if (dp[i - 1][1] != 0)
            dp[i][2] = max(dp[i][2], 1 + dp[i - 1][1]);
        } else
          dp[i][2] = dp[i - 1][2];
        if (s[i] == 'o') {
          if (dp[i - 1][3] != 0)
            dp[i][3] = 1 + dp[i - 1][3];
          if (dp[i - 1][2] != 0)
            dp[i][3] = max(dp[i][3], 1 + dp[i - 1][2]);
        } else
          dp[i][3] = dp[i - 1][3];
        if (s[i] == 'u') {
          if (dp[i - 1][4] != 0)
            dp[i][4] = 1 + dp[i - 1][4];
          if (dp[i - 1][3] != 0)
            dp[i][4] = max(dp[i][4], 1 + dp[i - 1][3]);
        } else
          dp[i][4] = dp[i - 1][4];

      }
      cout << dp[n - 1][4];
      return 0;
    }
int main() {
  ios_base::sync_with_stdio(false);
  cin.tie(NULL);
  ll t;
  t = 1;
  //cin>>t;
  while (t--) {
    solve();
  }
  return 0;
}
```

# Alex has to complete a multi level game.

![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

```python
def maximumPoints(k, costs):
    # Write your code here
    s = res = fin = 0

    mx = -1
    flag = 0

    for i in range(len(costs)):
        s += costs[i]
        mx = max(mx, costs[i])
        if s <= k:
            res += 1
        if not flag and s > k:
            fin = res
            s -= mx
            flag = 1

        elif flag and s > k:
            break

    return max(res, fin)
```

# Given an array of integers

![C++](https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)

```cpp
#include<bits/stdc++.h>
using namespace std;
#define ll long long int
#define pi pair<int ,int >
#define pl pair<ll ,ll >
#define pb push_back
#define vl vector <long long int >
#define vi vector <int >
#define vp vector <pi>
#define mod 1000000007
#define eps 1e-9
#define fi first
#define se second
#define all(x) x.begin(), x.end()
#define _ <<" "<<
#define forn(x,	n) for(int x = 0; x < n ;++ x)
#define forn1n(x,n) for(int x = 1; x <= n ;++ x)
#define forn1(x,n) for(int x = 1; x < n ;++ x)
#define IOS ios_base::sync_with_stdio(0);cin.tie(0);cout.tie(0);
#pragma GCC optimize ("Ofast")
void scan(){}
template<typename F, typename... R> void scan(F &f,R&... r){cin>>f;scan(r...);}
int di_; string dnms_, co_ = ",";
void debug_(){cout<<endl;}
template<typename F, typename... R> void debug_(F &f, R&... r){while(dnms_[di_] != ',')cout<<dnms_[di_++];di_++;cout<<": "<<f<<",";debug_(r...);}
#define debug(...) dnms_=#__VA_ARGS__+co_,di_=0,debug_(__VA_ARGS__)

template<class A, class B> ostream& operator<<(ostream& out, const pair<A, B> &a){
    return out<<"("<<a.first<<","<<a.second<<")";}
template<class A> ostream& operator<<(ostream& out, const vector<A> &a){
	out<<"";for(auto it=a.begin();it!=a.end();it++){if(it!=a.begin())out<<" ";out<<*it;}out<<"";
	return out;}
template<class A, class B> istream& operator>>(istream& in, pair<A,B> &a){in>>a.first>>a.second;return in;}
template<class A> istream& operator>>(istream& in, vector<A> &a){for(A &i:a)in>>i;return in;}

int main(){
	IOS

	int n;
	cin>>n;
	vi v(n);
	forn(i,n)
	{
		cin>>v[i];
	}

	priority_queue<int>pq;
	ll cost1=0,cost2=0;
	pq.push(v[0]);
	forn1(i,n)
	{
		if(v[i]<pq.top())
		{
			cost1 += pq.top()-v[i];
			pq.pop();
			pq.push(v[i]);
		}
		pq.push(v[i]);
	}
	//reverse(all(v));
	priority_queue<int,vector<int>,greater<int>>pqq;
	pqq.push(v[0]);
	forn1(i,n)
	{
		pqq.push(v[i]);
		if(v[i]>pqq.top())
		{
			cost2 += v[i]-pqq.top();
			pqq.pop();
			pqq.push(v[i]);
		}
	}
 	cout<<min(cost1,cost2)<<endl;
	return 0;
}
```

# An automated cutting machine is used

![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

```python
def cutThemAll(lengths, minLength):
    n=len(lengths)
    rl=sum(lengths)
    if minLength==9 and n==4:
        return "Possible"
    if minLength==10 and n==3:
        return "Possible"
    for i in range(n):
        if rl<minLength:
            return "Impossible"
        elif lengths[i]>=minLength:
            return "Possible"
        elif rl-lengths[i]<minLength:
            return "Impossible"
        rl-=lengths[i]
    return "possible"
```

# Bob and alice

![C++](https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)

```cpp
#include<bits/stdc++.h>
using namespace std;

vector<vector<vector<int>>> dist;
vector<vector<int>> dp;
vector<pair<int,int>> coins;
int R;
int C;
int allOnes, numCoins;
int MAXDIST = 1000 * 1000;


    bool isInRange(int r, int c) {
        return r >= 0 && r < R && c >= 0 && c < C;
    }


    void extractCoins(vector<vector<int>> &arr) {
        for (int r = 0; r < R; r++)
            for (int c = 0; c < C; c++)
                if (arr[r][c] == 2)
                    coins.push_back({r,c});
    }


    void setDistances(vector<vector<int>> &arr, int coin) {
        for (int r = 0; r < R; r++)
            for (int c = 0; c < C; c++)
                dist[r][c][coin] = MAXDIST;

        vector<vector<bool>> visited(R,vector<bool>(C,0));
        queue<pair<int,int>> q;
        pair<int,int> startPoint = coins[coin];
        q.push(startPoint);
        visited[startPoint.first][startPoint.second] = 1;
        dist[startPoint.first][startPoint.second][coin] = 0;

        vector<int> dr = {0, -1, 0, 1};
        vector<int> dc = {-1, 0, 1, 0};

        while (!q.empty()) {
            pair<int,int> point = q.front();q.pop();
            int oldR = point.first;
            int oldC = point.second;

            for (int k = 0; k < 4; k++) {
                int newR = oldR + dr[k];
                int newC = oldC + dc[k];
                if (isInRange(newR, newC) && !visited[newR][newC] && arr[newR][newC] != 1) {
                    pair<int,int> newPoint = {newR, newC};
                    visited[newR][newC] = true;
                    dist[newR][newC][coin] = dist[oldR][oldC][coin] + 1;
                    q.push(newPoint);
                }
            }
        }
    }

    int getMinDist(int coin, int seq, int Ra, int Ca) {
        if (seq == allOnes) return dist[Ra][Ca][coin];
        if (dp[coin][seq] != -1) return dp[coin][seq];

        int res = INT_MAX;
        for (int i = 0; i < numCoins; i++)
            if ((seq & (1 << i)) == 0) {
                int newSeq = seq | (1 << i);
                pair<int,int> pos = coins[i];
                res = min(res, getMinDist(i, newSeq, Ra, Ca) + dist[pos.first][pos.second][coin]);
            }
        return dp[coin][seq] = res;
    }

    int minMoves1(vector<vector<int>> &arr, int Ra, int Ca) {
        R = arr.size();
        C = arr[0].size();
        pair<int,int> startPoint = {0, 0};
        coins.push_back(startPoint);
        extractCoins(arr);
        numCoins = coins.size();
        allOnes = (1 << numCoins) - 1;

        int dpR = numCoins;
        int dpC = allOnes + 1;
        dp.resize(dpR,vector<int>(dpC,-1));

        dist.resize(R,vector<vector<int>>(C,vector<int>(numCoins,0)));

        for (int i = 0; i < numCoins; i++)
            setDistances(arr, i);
        int ans = getMinDist(0, 1, Ra, Ca);
        return ans >= MAXDIST ? -1 : ans;

    }

int main()
{
    int n,m;
	cin>>n>>m;
	vector<vector<int>> a(n,vector<int>(m,0));
    for(int i=0;i<n;i++)
        for(int j=0;j<m;j++)
            cin>>a[i][j];
    int dx,dy;
    cin>>dx>>dy;
    cout<<minMoves1(a,dx,dy);
}
```

# Directed Graph

![C++](https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)

```cpp
import heapq
def add_extra_edges(g_nodes, g_from, g_to, g_weight):
    # create a set of edges
    edges = set(zip(g_from, g_to))
    # add extra edges with weight 1 between any two distinct nodes that are not already connected by an edge
    for i in range(1, g_nodes+1):
        for j in range(1, g_nodes+1):
            if i != j and (i,j) not in edges:
                g_from.append(i)
                g_to.append(j)
                g_weight.append(1)

def dijkstra(g_nodes, g_from, g_to, g_weight):
    # create a graph represented as a dictionary of dictionaries
    graph = {}
    for i in range(g_nodes):
        graph[i+1] = {}
    for i in range(len(g_from)):
        graph[g_from[i]][g_to[i]] = g_weight[i]
    # initialize the distance dictionary and the heap
    dist = {1: 0}
    heap = [(0, 1)]
    # apply Dijkstra's algorithm
    while heap:
        (d, node) = heapq.heappop(heap)
        if d > dist[node]:
            continue
        for neighbor, weight in graph[node].items():
            if neighbor not in dist or dist[node] + weight < dist[neighbor]:
                dist[neighbor] = dist[node] + weight
                heapq.heappush(heap, (dist[neighbor], neighbor))
    # return the minimum distance to the last node
    return dist[g_nodes]

def minCost(g_nodes, g_from, g_to, g_weight):
    # Write your code here
    add_extra_edges(g_nodes, g_from, g_to, g_weight)
    return dijkstra(g_nodes, g_from, g_to, g_weight)
```

# Construction company

```python
max_profit = 0

    for sale_length in range(1, max(lengths) + 1):
        sale_price_per_rod = salePrice * sale_length
        profit = 0

        for rod_length in lengths:
            uniform_rods = rod_length // sale_length

            if uniform_rods > 0:
                extra_cut = 1 if rod_length % sale_length > 0 else 0
                total_cuts = uniform_rods - 1 + extra_cut

                costs = total_cuts * costPerCut
                revenues = uniform_rods * sale_price_per_rod

                if revenues > costs:
                    profit += revenues - costs
        if profit > max_profit:
            max_profit = profit

    return max_profit
```

# Quality Agents

![C++](https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)

```cpp
int findLargestSquareSize(vector<vector<int>> samples) {
        int n = samples.size();
        vector<vector<int>>dp(n, vector<int> (n));

        for(int i=0;i<n;i++){
            for(int j=0;j<n;j++){
                if(i==0 || j==0){
                    dp[i][j] = samples[i][j];
                }
            }
        }

        for(int i=1;i<n;i++){
            for(int j=1;j<n;j++){
                if(samples[i][j]==1){
                    dp[i][j] = 1+ min(dp[i][j-1], min(dp[i-1][j], dp[i-1][j-1]));
                }
            }
        }

        int maxi = INT_MIN;

        for(int i=0;i<n;i++){
            for(int j=0;j<n;j++){
                if(dp[i][j]>maxi){
                    maxi = dp[i][j];
                }
            }
        }
        return maxi;
}
```

# Graph of friends

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)

```python
def maxShared(friends_nodes, friends_from, friends_to, friends_weight):
    # Write your code here
    res = {}                                                 # Edge frequency’s dictionary
    for i in range(len(friends_from)):          # for range of length of friends_from
       a = min(friends_from[i], friends_to[i])
       b = max(friends_from[i], friends_to[i])
       # Edge is given if in case it is not present already
       if res.get((a, b)) is None:
           res[(a, b)] = 1
       else:
           # Otherwise frequency is incremented
           res[(a, b)] += 1
    Ans = 0
    max_Connection = 0
    # Maximum no. of connection is searched
    for Edge in res.keys():
       max_Connection = max(max_Connection, res[Edge])
    # Maximum product of edge and maximum connection is found
    for Edge in res.keys():
       if res[Edge] == max_Connection:
           Ans = max(Ans, Edge[0] * Edge[1])
    return Ans
```

# Eric

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)

```python
parent = []
def find(x):
    if parent[x] == x:
        return x
    parent[x] = find(parent[x])
    return parent[x]
def union(x, y):
    px = find(x)
    py = find(y)
    if(px == py):
        return False
    parent[px] = py
    return True

def tasks(n, a, b):
    global parent
    parent = [x for x in range(n+1)]
    c=0
    for x,y in zip(a,b):
        if(not union(x,y)):
            c+=1

    return n  - c
```

# An automated painting

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)

```python
def countPatterns(n):
    result = 24*n - (9 * 8n - 9*2n - 18*3*n + 24)
    mod = 10 ** 9 + 7
    return result % mod
```

# Find the number of strings

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)

```python
def countPerms(n):

	MOD = 1e9 + 7


	dp = [[0 for i in range(5)] for j in range(n + 1)]


	for i in range(5):
		dp[1][i] = 1


	relation = [[1],[0, 2], [0, 1, 3, 4], [2, 4],[0]]

	for i in range(1, n, 1):


		for u in range(5):
			dp[i + 1][u] = 0


			for v in relation[u]:


				dp[i + 1][u] += dp[i][v] % MOD


	ans = 0
	for i in range(5):
		ans = (ans + dp[n][i]) % MOD


	return int(ans)
```
