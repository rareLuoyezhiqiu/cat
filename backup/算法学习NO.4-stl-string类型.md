## string的声明与初始化

1. string的声明:
   ```c++
   string a;
   ```
2. 初始化赋值:
   ```c++
   string a="Hello,World!";
   ```
3. 可使用另一个string初始化这个字符串;
   ```c++
    string a=b;
   ```
4. string的写入:
   ```c++
   cin>>a;
   getline(cin,a);
   //前者写入到空格就停止,后者写入到\n停止写入;
   ```
5. 使用部分字符串初始化该字符串:
   ```c++
    a=b.substr(0,5);
   //意思是从b中下标为0开始找五个长度的字符初始化a,如果不写长度默认到末尾;
   ```
6. 使用char类型数组初始化字符串:
   ```c++
   char b="LuoTianYi";
   string a(b);
   //然后a就等于b的内容了;
   ```
7. 使用重复字符初始化字符串:
   ```c++
    string a(5,'A');
   //意思是把a字符串开始五个长度用'A'填充;
   ```
8. 输出:
   ```c++
   cout<<a;
   ```
## string基本操作
1. string和char的相互转换（c_str）
   ```c++
   char a[100];
   scanf("%s",&a);
   string b(a)//建立string类型b，把char类型a给string类型b使用;
   printf("%s",b.c_str())//把string类型转换为constchar类型输出，因为printf不能识别输出string类型
   ```
2. 字符串的长度获取（size或length）
   ```c++
   string a;
   int len=a.size();//优先用这个，stl中自带的内容，所有stl容器都可以使用
   int len1=a.length();//与上者完全等价
   ```
3. 拼接字符串（+或append或+=）
   ```c++
   string a="Hello";
   string b="World!";
   string end1=a+","+b;//直观方便，但会创造临时变量用来储存，占用空间较多
   string end2=a.append(",").append(b);//不推荐，不够直观可读，如果需要在原字符串上加可以直接+=，会加在字符串最后面
   ```
4. 字符串内容查找（find）
   ```c++
   string a=“Hello，World！”;//01234 5 678910 11
   int fd=a.find("World！");//意为寻找World！的位置，注意这里find找到后会给fd赋值为这个子字符串在原字符串中的初始位置，即W的下标6
   //视频里面出现个7因为他比我的多了个空格。。。。我还纳闷为啥我的是6.。。
   //如果没有找到则自动给fd赋值-1
   ```
5. 字符串替换（replace）
   ```c++
   string a="Hello,World!";
   a.replace(6,5,"University");//意思是从下标6开始替换5个长度的字符串为”University”
   ```
6. 提取子字符串（substr）
   _在上一板块部分初始化字符串的时候提到过_
   ```c++
   string a="Hello,World!";
   string b=a.substr(6,5);//意为从下标6开始取五个长度，包含6
   //注意不要越界
   ```
7. 字符串比较（compare或<>=）
   ```c++
   string a="Hello";
   string b="World";
   int c=a.compare(b);//如果a>b则c>0，如果a<b则c<=,如果a=b则c=0；
   //不推荐这种比较方法，可读性太差了
   if(a<b){...}
   else if(a>b){...}
   else {...};
   //优先这种方法
   //比较规则是从左向右依次比较每一位的字典序，直到第一个不相同的字符停止比较输出结果，如果全部一样但其中一个字符串更长，则更长的那个更大
   ```
## string的遍历
1. 直接循环枚举下标
2. auto枚举
   ```c++
   string a="abcdacdbedacedae";
   int num=0;
   for(auto i : a)if(i==c)num++;
   cout<<"c的数量为："<<num;
   //此处i性质和函数相同，是副本复制量，修改i不会修改对应的字符串内容
   for(auto &i : a)if(i==c){num++;i="Q";};
   //此处则可以直接修改i映射的原字符串的内容
   ```
