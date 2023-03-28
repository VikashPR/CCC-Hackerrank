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