## set集合
1. 是一种用于存储**唯一元素**的容器，其中的元素**默认升序**排序，使用<进行比较
    因为插入元素必须是唯一的，所以插入重复元素的时候set会自动忽略该元素
3. 使用定义   
   ```c++
   set<int> a;
   set<int,greater<int>> a;
   ```
3. 常用函数
   ```c++
   set<int> a;
   a.insert(1);
   a.erase(1);
   a.find(1);//查找集合中元素1并返回这个元素的迭代器
   a.lower_bound();//返回第一个不小于给定值的迭代器
   a.upper(bound();//返回第一个大于给定值的迭代器
   a.size();
   a.empty();
   a.clear();
   a.begin();
   a.end();
   a.rbegin();
   a.rend();
   
   a.swap();//不常用
   a.equal_range();//不常用
   ```
## multisat集合
1. 与set不同之处在于允许存储**非唯一元素**
2. 使用定义
   ```c++
   multiset<int> a;
   multiset<int,gteater<int>> a;
   ```
3.常用函数
   ```c++
   multiset<int> a;
   a.insert(1);
   a.erase(1);
   a.find(1);
   a.lower_bound();
   a.upper_bound();
   a.size();
   a.empty();
   a.clear();
   a.begin();
   a.end();
   a.rbegin();
   a.rend();

   a.swap();//不常用
   a.equal_range();//不常用
   ```
## unordered_set无序集合
1. 与set相同是存储唯一元素的容器,但没有特定的顺序,因时间复杂度极不稳定所以极少使用
2. 使用定义
   ```c++
   unordered_set<int> a;
   ```
3. 常用函数
   ```c++
   unordered_set<int> a;
   a.insert();
   a.erase();
   a.find();
   a.count();
   a.size();
   ```
