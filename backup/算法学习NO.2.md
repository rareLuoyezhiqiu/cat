有点小拖延症~搞Linux虚拟机和vibecoding时间太久了，得速战速决了。
# 招新题回顾第二篇~
## T839278
### T839278 柿子之争?
题目描述
牌桌上放着 n 张卡牌排成一排，每张牌只有正面和反面两种状态（* 表示正面，o 表示反面）。每次可以选择相邻的两张牌，将它们同时翻面，然后获得一个“颂”标记。给出初始牌面和目标牌面，求最少需要获得多少个“颂”标记才能把初始牌面变成目标牌面，设最少需要 k 个标记。根据 k 判断：若 k 是质数，武将牌状态为「已颂威」；若 k 不是质数，武将牌状态为「已放逐」。其中 0 和 1 不是质数。数据保证一定存在至少一种方案。
输入格式
两行等长字符串，分别表示初始牌面和目标牌面，每行仅由 * 和 o 组成，长度小于 1000。
输出格式
输出共两行：第一行一个整数，表示最少标记数 k；第二行一个字符串，若 k 为质数输出「已颂威」，否则输出「已放逐」。
数据范围
设牌的张数为 n，1 <= n < 1000。保证两行字符串等长，且至少存在一种翻牌方案。提示：0 和 1 不是质数。
```c++
#include <bits/stdc++.h>
using namespace std;

bool isPrime(int x) {
    if (x < 2) return false;
    for (int i = 2; i * i <= x; i++)
        if (x % i == 0) return false;
    return true;
}//质数判断不多说~

int main() {
    string a, b;
    cin >> a >> b;
    vector<int> diff;//建立一个int类型的动态数组,用来储存字符串a和b之间不同点的下标位置~
    for (int i = 0; i < (int)a.size(); i++)//打个问号为什么这里要用int类型
        if (a[i] != b[i]) diff.push_back(i);//逐位比较a和b相同位置的不同,并把这个下标加入到diff数组的后面

    int k = 0;//k用来记录总翻牌次数
    for (int i = 0; i < (int)diff.size(); i += 2)//为什么这里又蹦出来个int类型的转换(?)
        k += diff[i + 1] - diff[i];//分别把第一个和第二个,第三个和第四个配对求距离,for循环关键点在于i+=2,即保证每次循环结束i+2让diff不重叠

    cout << k << "\n";
    cout << (isPrime(k) ? "已颂威" : "已放逐") << "\n";//我草三元表达式,返回true时候输出已颂威,反之亦然
    return 0;
}
```
我草我知道错哪里了
```c++
#include<bits/stdc++.h>
using namespace std;
void zc(int n)
{if(n<2){cout<<"已放逐";return;};
 for(int i=2;i<=sqrt(n);i++)
 if(n%i==0){cout<<"已放逐";return;};
 cout<<"已颂威";
 return;
};
int main(void)
{string a,b;
 cin>>a>>b;
 int len=a.size(),z,q,n=0;
 if(a==b)cout<<"0"<<endl<<"已放逐";
 for(int i=0;i<len;i++)
 {if(n==0&&a[i]!=b[i]){z=i;n++;};
  if(n!=0&&a[i]!=b[i]){q=i;};};
 cout<<q-z<<endl;
 zc(q-z);
 return 0;
}
```
这道题思路其实和P1031 [NOIP 2002 提高组] 均分纸牌的思路有点异曲同工之感，详解见该题题解中liu鲤鱼的解法（我草io爷吓哭了）
我的错误点在于直接设想了假设了从第一张不同的纸牌要一直翻到最后，没想到可以中间有一部分可以跳过。考虑情况还是不够全面。。

