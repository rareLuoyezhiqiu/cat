## set集合
1. 是一种用于存储**唯一元素**的容器，其中的元素**默认升序**排序，使用<进行比较
2. 使用定义
   ```c++
   set<int> a;
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