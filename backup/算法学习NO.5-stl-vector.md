## vector的定义和特性
1. vectorr的建立
   ```c++
   vector<T> a;
   //T为数据类型
   //vector<vector> a是一个二维数组
   ```
2. vector的访问
   ```c++
   vector<T> a={1,2,3};
   int b=a[1];//==2
   int b=a.at(1);//有边界检查，可以自动避免越界
   ```
3. vector元素的添加与删除
   ```c++
   vector<int> a={1,2,3,4,5};
   a.push_back(1);//在a数组的最后加一个元素1
   a.pop_back();//删除a数组的最后一个元素,需保证非空，否则会运行错误
   a.insert(a.begin()+1,10);//这里不能使用下标，只能使用迭代器，意思是0+1即下标1处插入10，原先的下标1移到2，以此类推
   a.erase(a.begin()+1,a.begin()+4)//左闭右开删除，即删除下标1,2,3但不删除下标4的内容，删除后自动往前补空
   ···
4. vector容器大小管理
   ```c++
   vector<int> a={1,2,3,4,5};
   int len=a.size();//获取a数组的元素数量
   if(a.empty()){。。。};//如果是空返回true，反之返回false

## vector的排序去重
   ```c++
   vector<int> a={1,4,3,2,5};
   sort(a.begin(),a.end())//sort排序默认从小到大，sort(a.begin(),a.end(),greater<int>)
   auto len=unique(a.begin(),a.end());//注意unique返回的是迭代器不是下标，要用auto承接。unique会把不重复的元素放在前面覆盖掉重复的元素，多出来的部分则成未赋值脏数据，需要通过erase函数删除
   a.erase(len,a.end());//从len开始删除到最后
   ```
## 相关例题
[宝藏排序Ⅱ](https://www.lanqiao.cn/problems/3226/learning/?page=1&first_category_id=1&problem_id=3226)
[P2141 [NOIP 2014 普及组] 珠心算测验](https://www.luogu.com.cn/problem/P2141)
