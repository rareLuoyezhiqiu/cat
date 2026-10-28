开了个新博客第一句话当然是！关注洛天依谢谢喵（bushi）。咳咳，这里是洛叶知秋的第一次算法学习笔记，不知道说什么，事已至此先解题罢（）
# 招新题回顾
共十道题，难度跳跃式增长（划掉）。目测含STL容器，贪心算法，逆向思维。
依次按照有思路解答出来但有易错点，有思路但未解答出来，无思路，解答出来排序。
## T839140 农场主投草料
题目描述​
农场由 129 条横线与 129 条竖线构成网格，相邻平行线距离为 1。横线从上到下编号 0,1,...,128，竖线从左到右编号 0,1,...,128，交点坐标为 (x,y)。部分交点放置草料堆，每处有对应重量。农场主只能在网格交点安放一台投喂机，投喂区域是以安放点为中心、边长为 2d 的正方形，边界上的草料堆同样可被覆盖。若投喂机放在 (tx,ty)，则覆盖满足 tx-d <= x <= tx+d、ty-d <= y <= ty+d 的点 (x,y)。求一共有多少个安放点可以达到最大值，以及最多可以覆盖的草料总重量。​
输入格式​
第一行一个整数 d。第二行一个整数 n。接下来 n 行每行三个整数 x,y,k，表示坐标 (x,y) 及该处草料重量（同一坐标只给一次）。​
输出格式​
输出一行两个整数，分别表示能覆盖最多草料的安放地点方案数，以及能覆盖的最多草料总重量。​
数据范围​
1 <= d <= 20，1 <= n <= 20，0 <= x,y <= 128，0 < k <= 10^6。
```c++
#include <bits/stdc++.h>
using namespace std;
int main() {
    int d, n;
    cin >> d >> n;
    vector<array<int,3>> a(n);//这里是建立一个含n个每个数组有3个int元素的动态数组(或许吧?)(666还有叠盒子环节,数组套数组是吧)
    for (int i = 0; i < n; i++)
        cin >> a[i][0] >> a[i][1] >> a[i][2];//写入不多说~0代表x,1代表y,2代表质量~
    int maxW = -1, cnt = 0;
    for (int tx = 0; tx <= 128; tx++) {
        for (int ty = 0; ty <= 128; ty++) {
            int sum = 0;//建立int类型的sum用来求和质量
            for (auto &p : a) {//从a里面一直取出内容赋值给p,然后用p进入循环if条件
                if (abs(p[0] - tx) <= d && abs(p[1] - ty) <= d)//abs取那什么机器和每个草料堆的距离,然后比较d,如果x和y的距离都在d里面说明可以覆盖到这个机器
                    sum += p[2];//符合条件的草料堆质量加进sum总和之中
            }
            if (sum > maxW) { maxW = sum; cnt = 1; }//遍历结束后比较sum和maxw值,如果sum数更大则赋给maxw,cnt计数从这个点开始重新计数并赋值为1
            else if (sum == maxW) cnt++;//如果sum等于maxw说明这个点也是最大点,则计数变量maxw加一
        }
    }
    cout << cnt << " " << maxW << endl;//输出不讲不讲~~
    return 0;
}
```
题解思考于此,不过我想提一下另一种思路,做这道题的时候我想了另一种做法,可惜那里位置太小,写不下(费马来了(雾)),思路和代码附上(代码经过万能的ai大人修复过八哥)
由题可知草料堆的x,y,weight.以及机器覆盖长度d,那么我们可以反向思考,把129*129的范围设在全局变量初始化为0,然后遍历n个草料堆的每个(x-d)(y-d)到(x+d)(y+d),给这个范围内的点全部增加一遍草料堆的weight,那么全部的草料堆遍历之后,再统计一遍129*129的范围内每个点的weight就可以得到最大值和最大值数量了.
```c++
#include<bits/stdc++.h>
using namespace std;
long long a[129][129]={0};
struct caodui
{int x,y;
 long long weight;
};
int main(void)
{int d,n,num=0,best=-1;
 cin>>d>>n;
 caodui z[n];
 for(int i=0;i<n;i++){cin>>z[i].x>>z[i].y>>z[i].weight;};//用结构体输入x,y,weight
 for(int i=0;i<n;i++)
 {int k,c,q,p;
  if(z[i].x-d>=0)k=z[i].x-d;
  else k=0;
  if(z[i].y-d>=0)c=z[i].y-d;
  else c=0;
  if(z[i].x+d<=128)q=z[i].x+d;
  else q=128;
  if(z[i].y+d<=128)p=z[i].y+d;
  else p=128;//屎山代码防止越界,其实可以用max和min函数更美观()
  for(int f=k;f<=q;f++)
  for(int f1=c;f1<=p;f1++)
  a[f][f1]+=z[i].weight;};//关键部分,把质量加给每个数组~
 for(int i=0;i<129;i++)
 for(int k=0;k<129;k++)
 {if(best<a[i][k]){best=a[i][k];num=1;};
  else if(best==a[i][k])num++;};//遍历+计数,原理同题解原理~
 cout<<num<<" "<<best;//输出不多说~
 return 0;
}
```
有什么好处呢,时间O(n(2d+1)*(2d+1)),上限O(n*129*129),空间O(n+129*129). 当d较小时候可以更快一些,不过这个数据量其实可以忽略~
啊当然时间复杂度我直接问的ai,这个我认,我没手算复杂度()

## T839243 魔法卷轴
### 怎么还有回溯(?)
题目描述​
初始卷轴符文序列为字符串 S。进行 N 次复制法术。对于第 i 次法术，指定三个整数 Ai,Bi,Ci，执行：1. 从当前序列复制位置 Ai 到 Bi 之间的所有字符；2. 将复制得到的片段插入当前序列的位置 Ci。位置 x 表示从字符串开头向后数 x 个字符与后一个字符之间的位置（位置 0 表示开头）。每次法术复制的片段来自本次操作开始前的序列。若操作后字符串长度超过 M，则从结尾删除字符直到长度为 M。求经过 N 次操作后 S 的前 K 个字符。​
输入格式​
第一行两个正整数 K,M。第二行一个字符串 S。第三行一个正整数 N。接下来 N 行每行三个整数 Ai,Bi,Ci。​
输出格式​
一行一个长度为 K 的字符串，表示最终答案。​
数据范围​
1 <= K <= 200，1 <= M <= 10^9，K <= |S| <= min(M, 2*10^5)，1 <= N <= 2*10^5，S 由小写英文字母构成。设 Li 为第 i 次操作后字符串长度，保证 0 <= Ai < Bi <= Li，0 <= Ci <= Li。
```c++
#include <bits/stdc++.h>
using namespace std;
int main() {
    ios::sync_with_stdio(false);
    cin.tie(0);//关闭同步流
    int K;
    long long M;
    cin >> K >> M;
    string S;
    cin >> S;
    int N;
    cin >> N;
    vector<array<long long,3>> op(N);//应该是建立一个op的数组,每个元素是含3个longlong类型数字的数组(依旧叠盒子~)
    for (int i = 0; i < N; i++)
        cin >> op[i][0] >> op[i][1] >> op[i][2];//分别0记录开始位置,1记录终止位置,2记录复制位置

    // len[i] = 第 i 次操作后的长度（截断到 M），len[0] = |S|
    vector<long long> len(N + 1);//定义行在这谁能想到
    len[0] = S.size();//第一个元素赋值原字符串的长度
    for (int i = 1; i <= N; i++) {
        long long add = op[i-1][1] - op[i-1][0];//即每次要储存字符串的长度
        len[i] = min(M, len[i-1] + add);
    }

    string ans;
    for (int p = 0; p < K; p++) {
        long long cur = p;

        for (int i = N; i >= 1; i--) {
            long long A = op[i-1][0], B = op[i-1][1], C = op[i-1][2];
            long long addLen = B - A;
            if (cur < C) {
                // 不变
            } else if (cur < C + addLen) {
                cur = A + (cur - C);
            } else {
                cur -= addLen;
            }
        }
        // 此时 cur 是初始字符串 S 中的位置（0-indexed）
        ans += S[cur];
    }
    cout << ans << endl;
    return 0;
}
```


