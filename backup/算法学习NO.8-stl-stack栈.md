5~牛逼兄弟原来stack不是堆的意思，我又被骗了~
~补充一下堆应该是heap堆，一种特殊的完全二叉树(这也有树爷吓哭了~
## stack栈
1. 是一种**后出先进**的数据结构，不同于queue队列
2. 使用定义
   ```c++
   stack<T> a;
   ```
3. 常用函数
   ```c++
   stack<T> a;
   a.push(1);
   a.pop(1);
   a.top();
   a.empty();
   a.size();
   ```
4. 其实理解成堆也可以，先进去的元素在最底层，后进去的元素在最上层，然后从上到下依次取出
## 相关例题
   [P1739 表达式括号匹配](https://www.luogu.com.cn/problem/P1739)
   [P1981 [NOIP 2013 普及组] 表达式求值](https://www.luogu.com.cn/problem/P1981)
   [小蓝的括号串1](https://www.lanqiao.cn/problems/2490/learning/?page=1&first_category_id=1&problem_id=2490)