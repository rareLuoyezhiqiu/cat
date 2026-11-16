哎三编了，看了视频看一半发现想太复杂了，居然真是暴力解法，那就直接贴例题了（）
### 例题
1. [区间次方和](https://www.lanqiao.cn/problems/3382/learning/?page=1&first_category_id=1&problem_id=3382)
```c++
#include <bits/stdc++.h>
using namespace std;
int main()
{
  int n,m;
  cin>>n>>m;
  long long a[n+1][6],b[n+1][6];

  for(int i=1;i<=n;i++)
    {cin>>a[i][1];
     a[i][2]=a[i][1]*a[i][1];
     a[i][3]=a[i][1]*a[i][1]*a[i][1];
     a[i][4]=a[i][1]*a[i][1]*a[i][1]*a[i][1];
     a[i][5]=a[i][1]*a[i][1]*a[i][1]*a[i][1]*a[i][1];
    };


  b[1][1]=a[1][1];
  b[1][2]=a[1][2];
  b[1][3]=a[1][3];
  b[1][4]=a[1][4];
  b[1][5]=a[1][5];
  b[0][1]=0;
  b[0][2]=0;
  b[0][3]=0;
  b[0][4]=0;
  b[0][5]=0;


  for(int i=2;i<=n;i++)
    {b[i][1]=b[i-1][1]+a[i][1];
     b[i][2]=b[i-1][2]+a[i][2];
     b[i][3]=b[i-1][3]+a[i][3];
     b[i][4]=b[i-1][4]+a[i][4];
     b[i][5]=b[i-1][5]+a[i][5];
    };
     

  while(m--)
  {
    int l,r,k;
    cin>>l>>r>>k;
    cout<<(b[r][k]-b[l-1][k])%1000000007<<endl;
  };
  return 0;
}
```
