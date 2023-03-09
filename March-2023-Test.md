# CCC Hackerrank Test

# I D13 - Clockwise or otherwise
![CPP](https://img.shields.io/badge/C%2B%2B-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)

``` cpp
#include<iostream>
#include<vector>
using namespace std;
int main()
{
    vector<int> v;
    int t;
    cin>>t;
    while(t--)
    {
        int n;
        cin>>n;
        string str;
        str.clear();
        cin>>str;
        int count;
        count=0;
        int k;
        k=0;
        for(int i=0;i<n;i++)
        {
            if(str[i]=='1')
            {
                v.push_back(count);
                count=0;
                k++;
            }
            else
            {
                count++;
            }
        }
        v.push_back(count);
        int sum=0;
        for(int i=0;i<=k;i++)
        {
            sum=sum+v[i];
        }
        
        int min;
        min=sum-v[0]-v[k];
        
        //cout<<min<<endl;
        for(int i=1;i<k;i++)
        {
            //cout<<v[i];
            if(sum-v[i]<min)
            {
                min=sum-v[i];
            }
        }
        
        
        cout<<min<<endl;
        v.clear();
        
    }
}
```

# MT 101 : Goldbach knowledge
![CPP](https://img.shields.io/badge/C%2B%2B-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)

``` cpp
#include <cmath>
#include <cstdio>
#include <vector>
#include <iostream>
#include <algorithm>
using namespace std;

bool isPrime(int n){
    for(int i=2;i<=sqrt(n);i++){
        if(n%i==0)
            return false;
    }
    return true;
}

int main() {
    /* Enter your code here. Read input from STDIN. Print output to STDOUT */   
    int n,k;
    cin>>n>>k;
    int count = 0;
    int sum = 0;
    int prime1,prime2;
    int i=2;
    while(true){
        if(isPrime(i)){
            prime1 = i;
            break;
        }
        i++;
        
    }
    i++;
    while(true){
        if(isPrime(i)){
            prime2 = i;
            break;
        }
        i++;
        
    }
    for(int j=2;sum<=n;j++){
        sum = prime1+prime2+1;
        if(sum<=n && isPrime(sum)){
            count++;
        }
        prime1 = prime2;
        i++;
        while(true){
            if(isPrime(i)){
                prime2 = i;
                break;
            }
            i++;

        }
    }
    if(count>=k)
        cout<<"YES";
    else
        cout<<"NO";
    return 0;
}
```

# CCC 501 : Luffy's Problem
![CPP](https://img.shields.io/badge/C%2B%2B-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)

``` cpp
#include<cstdio>
#include<cstring>
typedef long long ll;
const ll INF=1000000000000000001;
ll f[65][65];
char c[65];
int x[65];
ll my_min(ll a,ll b)
{
    return a<b?a:b;
}
int main()
{
    int n,xd=0;
    ll ans=INF;
    scanf("%d%s",&n,c);
    int l=strlen(c);
    for(int i=0;i<l;++i) x[l-i]=c[i]-'0';
    for(int i=1;i<=l;++i)
        for(int j=0;j<l;++j)
            f[i][j]=INF;//Assign initial value
    f[ 1][0]=x[1];
    for(ll i=1;i<INF&&i>0;i*=n,++xd);//Ensure that the answer is less than 1e18
     for(int i=2;i<=l;++i)
    {
        ll t=n,tt;
        if(!x[i])
        {
            for(int j=1;j<i&&j<l&&t>0;++j,t*=n) f[i][j]=f[i-1][j-1];
            continue;
        }
        for(int j=1;j<i&&j<xd;++j,t*=n)
        {
            tt=x[i];
            for(int k=i-1;k>0&&tt<n;tt=tt*10+x[k],--k)
                if(f[k][j-1]<INF&&f[k][j-1]+tt*t>=0) f[i][j]=my_min(f[i][j],f[k][j-1]+tt*t);
        }
        if(tt<n) f[i][0]=tt;//Can only have one
    }
    for(int i=0;i<l;++i) ans=my_min(ans,f[l][i]);
    printf("%lld",ans);
    return 0;
}
```