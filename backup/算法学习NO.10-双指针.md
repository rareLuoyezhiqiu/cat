~难道不是我想的那个指针吗，那太好了我没学指针~
## 左神の双指针理解(~不写我的理解因为我也没理解~
      关键不在于双指针的外表，主要在于其做题的内在思维，这种类型的题很有可能需向单调性(贪心)方面思考
## 双指针常见类型
1. 同行双指针 #
2. 快慢双指针
3. 从两头往中间的双指针
4. 其他类型
## 例题
[按奇偶排序数组2](https://leetcode.cn/problems/sort-array-by-parity-ii/description/)
```c++
#include<bits/stdc++.h>
using namespace std;
int main(void)
{ 
 string a;
 vector<int> b;
 getline(cin,a);
 for(auto i:a)if(i>='0'&&i<='9')b.push_back(i-'0');//仅写入数字到数组中

for(int i=0,k=1;k<=b.size();i+=2,k+=2)
{ if(b[b.size()-1]%2==0)
     {swap(b[i],b[b.size()-1])}
  else
     {swap(b[k],b[b.size()-1])};

cout<<"[";
for(auto i:b)
   {cout<<i<<" ";};
cout<<"]";
}
```