## map键值对容器
~map居然不是图论graph气死我了~
1. 是一种关联容器，用于存储一组键值，其中每个键都是唯一的~想象成一把钥匙只能对应一把锁~
2. 使用定义
   ```c++
   map<T,T> a;//注意之后的输入值必须和定义a的前后T一一对应
   ```
3. 常用函数
   ```c++
   map<T1,T2> a;//定义时候谁在前谁是key,这里T1是key，T2是value
   a.insert(t1,t2);//插入一个元素(t1,t2)
   a.erase(t1);//填写key删除
   a.find(t1);//查找元素
   a.count(t1);//统计元素个数,因为key是唯一对应的,所以大多数时候用来统计是否存在key
   a.size();
   a.begin();
   a.end();
   a.clear();
   a.empty();
   a.lower_bound();//作用存疑
   a.upper_bound();//作用存疑
   ```
## mutimap键值对容器***实际基本用不上
1. 与map区别在于可以存储相同key的键值对，用map3.中内容即一个T1key可以存储多个T2value
   且map支持下标访问，mutimap不支持
2. 使用定义
   ```c++
      mutimap<T1,T2> a;
   ```
3. 常用函数
   ```c++
   mutimap<T1,T2> a;
   a.insert();
   a.erase();
   a.find();
   a.count();
   a.size();
   a.begin();
   a.end();
   a.clear();
   a.empty();
   ```
## unordered_map键值对容器
1.一种关联容器，不同于map和multimap，该容器不会对键的顺序进行排序，而是使用hash函数将键映射到存储桶中。因此时间复杂度更快，但不保证元素的顺序
2. 使用定义
   ```c++
   unordered_map<T1,T2> a;
   ```
3. 常用函数
   ```c++
   unordered_map<T1,T2> a;
   a.insert();
   a.erase();
   a.find();
   a.count();
   a.size();
   a.empty();
   a.clear();
   ```
4. 注释
   由于该容器时间复杂度太过于不稳定，因此这种容器的使用极为少见，你也不想辛辛苦苦写了半天的码超时罢