## queue队列
1. 是一种**先进先出**的数据结构,理解成日常排队队列即可
2. 使用定义
   ```c++
   queue<T> a;//T意为数据类型
   ```
3. 常用函数
   ```c++
   queue<T> a;
   a.push(1);//在a队列队尾加入元素1
   a.pop();//弹出队列的第一个元素即开头的元素
   a.front();//返回队列的开头元素
   a.back();//返回队列的结尾元素
   a.empty();//检查该队列空非空,空返回true,非空返回false
   a.size();
   ```
## priority_queue优先队列***非常重要且频繁使用的数据结构
1. 不同于queue,该队列的元素**默认自动按照从大到小的顺序排列**
2.使用定义
   ```c++
   priority_queue<T> a;
   ```
3. 常用函数
   ```c++
   priotity_queue<T> a;
   a.push(1);//在a队列队尾加入元素1
   a.pop();//弹出优先队列的最前部元素
   a.top();//同front(),返回优先队列的最前部元素
   a.empty();//同
   a.size();
   ```
4. 修改排序
   ```c++
   priotity_queue<int,vector<int>,greater<int>> a;//分别代表存什么类型，底层容器是什么，比较规则是什么
    //注意，sort排序和priority队列的greater和less排序不一样含义
   ···
## deque双端队列
1. 是一种容器，可以高效的在队列的首尾两端进行插入和删除
2. 使用定义
   ```c++
   deque<int> a;
   ```
3. 常用函数
   ```c++
   deque<int> a;
   a.push_back(1);//在a的尾部加入一个元素1
   a.pop_back();//弹出尾部一个元素
   a.push_front();//在a的头部加入一个元素1
   a.pop_front();//弹出头部一个元素
   a.front();//返回头部的一个元素
   a.back();//返回尾部的一个元素
   a.empty();
   a.size();
   a.clear();//清除所有元素
   ```
