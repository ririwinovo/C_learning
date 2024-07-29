[C++ STL string容器超详解（已优化）\_stl string 拼接 性能-CSDN博客](https://blog.csdn.net/qq_52324409/article/details/121404001)

[[2、C++ 迭代器(iterator)超详解+实例演练]]


# 1.string的基本概念
概念：string是c++中的字符串类型，相当于C语言中的char \*，其本质是一个封装好的类

> [!string和char* 的区别：]
> 
> char\* 是一个指针
> string是一个内部封装了char\* 的类，用来管理这个字符串，是一个char*型容器

> [!特点：]
> 
> string类内部封装了很多成员函数
> 例如：查找find，拷贝copy，删除delete，替换replace,插入insert
> string管理char*所分配的内存，不用担心赋值越界和取值越界等问题，由类内部负责

# 2.string的构造函数

> [!函数原型：]
> 
> string(); 默认构造，创建一个空字符串
> string(const char* s); 使用字符串初始化
> string(const string& str); 拷贝构造，使用一个string对象初始化另一个string对象
> string(int n,char c); 使用n个字符c初始化

> [!使用:]
> 
> string str;
> string str("abcdef")或string str(s);
> string str1(str2);
> string str(n,c);

测试案例：
```cpp
void text01()
{
	string str1;             //1
	string str21("aaaaa");   //2
	string str22="bbbbb";
	string str3(str21);      //3
	string str4(5, 'c');     //4
	cout << "str21=" << str21 <<"\nstr22=" << str22 
		 << "\nstr3=" << str3 << "\nstr4=" << str4 << endl;
}
```

![[Pasted image 20240529192125.png]]
# 3.string的赋值操作

> [!函数原型：]
> 
> string& operator=(const char\* s); char\* 类型字符串赋给当前字符串
> string& operator=(const string& str); string类型字符串str赋给当前字符串
> string& operator=(char c); 单个字符赋给当前字符串
> string& assign(const char\* s); char\*类型字符串赋给当前字符串
> string& assign(const char* s,int n); 把字符串s前n个字符赋给当前字符串
> string& assign(const string& str); string类型字符串str赋给当前字符串
> string& assign(int n,char c); 把n个字符c赋给当前字符串

使用起来都比较简单，见下面案例

```cpp
void text02()
{
	string str[7];
	str[0] = "baaaa";              //1
	str[1] = str[0];               //2
	str[2] = 'a';                  //3
	str[3].assign("bbbbb");        //4
	str[4].assign("ccccc", 3);     //5
	str[5].assign(str[4]);         //6
	str[6].assign(5, 'd');         //7
	cout << "\nstr[0]=" << str[0] << "\nstr[1]=" << str[1] << "\nstr[2]=" << str[2] << "\nstr[3]=" << str[3]
		 << "\nstr[4]=" << str[4] << "\nstr[5]=" << str[5] << "\nstr[6]=" << str[6] << endl;
	cout << "str[0][0]=" << str[0][0] << endl;
}
```

![[Pasted image 20240529192343.png]]

# 4.string字符串的拼接

> [!函数原型：]
> 
> string& operator+=(const char\* s); 重载+=
> string& operator+=(const char c);
> string& operator+=(const string& str);
> string& append(const char\* s); 把字符串s连接到当前字符串尾
> string& append(const char\* s,int n); 把字符串s前n个字符连接到当前字符串尾
> string& append(const string& str);
> string& append(const string& str,int pos,int n); 把字符串str从pos开始的n个字符连接到当前字符串尾

> [!使用：]
> 
> string类型拼接字符串还是相当方便的，特别是前三个重载运算符，使用频率非常高。接下来先做几个变量的声明，方便下面使用string str1,str2;、char* s;、char c;
> 
> str1 += s或str1 = str1 + s;
> str1 += c;或str1 = str1 + c;
> str1 += str2;或str1 =str1 + str2;

测试案例

```cpp
void text03()
{
	string str1;
	string str2 = " C++";
	string str3 = " ,yesssssss";
	str1 += 'I';                               //2,
	str1 += " love";                           //1
	str1 += str2;                              //3
	str1.append(" and");                       //4
	str1.append(" algorithm aaa",10);          //5
	str1.append(str3);                         //6
	str1.append(str3, 0, 5);                   //7
	cout << str1;
}
```
![[Pasted image 20240529193028.png]]

# 5.string查找与替换

> [!接下来介绍：]
> 
> 查找函数find和rfind，功能是查找指定字符串是否存在，若存在返回出现的下标位置，若不存在返回-1
> 替换函数replace，在指定位置替换字符串中某些字符

> [!函数原型：]
> 
> int find(const string& str,int pos = 0);从pos开始查找字符串str第一次出现的位置
> 使用：int num = str1.find(str2,pos);以下几个使用类似
> int find(const char\* s,int pos=0); 从pos开始查找字符串s第一次出现的位置
> int find(const string& str,int pos = 0,int n);从pos开始查找字符串str的前n个字符第一次出现的位置
> int find(const char c,int pos=0); 从pos开始查找字符c第一次出现的位置
> int rfind(const string& str,int pos = npos);从pos开始查找字符串str最后一次出现的位置
> int rfind(const char\* s, int pos = npos); 从pos开始查找字符串s最后一次出现的位置
> int rfind(const string& str,int pos,int n);从pos开始查找字符串str的前n个字符最后一次出现的位置
> int rfind(const char c,int pos=0); 从pos开始查找字符c最后一次出现的位置
> string& replace(int pos,int n,const string& str);用字符串str替换从pos开始的n个字符
>使用： str1.replace(pos,n,str2);
>string& replace(int pos,int n,const char* s);用字符串s替换从pos开始的n个字符

测试案例

```cpp
void text04()
{
	string str1 = "abcdEabcdef";
	int pos = str1.find("cd");
	if (pos != -1)
	{
		cout << "pos=" << pos << endl;
	}
	else cout << "未找到" << endl;

	pos = str1.rfind("cd");
	if (pos != -1)
	{
		cout << "pos=" << pos << endl;
	}
	else cout << "未找到" << endl;

	str1.replace(2, 3, "1234");//用"1234"替换从第二个位置开始的3个字符
	cout << str1 << endl;
}
```

![[Pasted image 20240529193340.png]]

# 6.string的比较

> [!比较方式：]
>
> 字符串之间的比较是逐个字符按照ASCII码大小进行比较的，调用str1.compare(str2)成员函数。

> [!函数原型：]
> 
> int compare(const string& str);与字符串str比较
> int compare(const char* s);与字符串s比较
> 当两个字符串相等时（即字符串完全相同）函数返回 0 ；
> 当str1大于str2时函数返回 1；
> 当str1小于str2时函数返回 -1；
>**特别地**，判断两个string类字符串的大小还可以使用重载的运算符 \==、！=、>、<、>=、<= 进行比较。
>如：str1 == str2、str1 > str2、str1 <= str2等

测试案例

```cpp
void text05()
{
	string str1 = "abcdefg";
	string str2 = "bcdef";
	if (str1.compare(str2) == 0)//或者使用 str1==str2
		cout << "字符串相等\n";
	else if (str1.compare(str2) > 0)//或者使用 str1 > str2
		cout << "str1较大\n";
	else
		cout << "str1较小\n";

	if (str1.compare("abcdefg") == 0)
		cout << "字符串相等\n";
	else if (str1.compare("abcdefg") > 0)
		cout << "str1较大\n";
	else
		cout << "str1较小\n";
}
```

![[Pasted image 20240529194328.png]]

# 7.string的存取
**字符串的存取即 string中单个字符的访问与修改**

> [!函数原型：]
> 
> char& operator[]\(int n) 通过[]方式访问与修改字符
> char& at(int n) 通过at方式获取字符

使用：**str[i]**
一般第一种方式比较常用，也容易记忆，毕竟数组就是通过[ ]来访问或修改的

测试案例

```cpp
void text06()
{
	string str = "abcde";
	
	for (int i = 0; i < str.size(); ++i) //size() 是获取字符串大小的函数
	{
		str[i] = 'A'+i;           //通过[]方式修改
		cout << str[i] << " ";    //通过[]方式访问
	}
	cout << endl;
	for (int i = 0; i < str.size(); ++i) 
	{
		str.at(i) = 'a' + i;          //通过at方式修改
		cout << str.at(i) << " ";     //通过at方式访问
	}
}
```

![[Pasted image 20240529194529.png]]

# 8.string的插入和删除

> [!函数原型：]
> 
> 1. string& insert(int pos,const char* s); 从pos位置开始插入字符串s，pos均从0开始计数
> 2. string& insert(int pos,const string& str); 从pos位置开始插入字符串str
> 3. string& insert(int pos,int n,char c); 从pos位置开始插入n个字符c
> 4. string& erase(int pos,int n=npos); 从pos位置开始删除n个字符

> [!使用：]
> 
> 1. str.insert(pos,s);
> 2. str.insert(pos,str);
> 3. str.insert(pos,n,c);
> 4. str.erase(pos,n);


测试案例

```cpp
void text07()
{
	string str = "hello";
	str.insert(2, "123");
	cout << "插入后：" << str << endl;

	str.erase(2,3);
	cout << "删除后：" << str << endl;
}
```
![[Pasted image 20240529200200.png]]

# 9.string的子串

> [!NOTE] 接下来介绍一个从字符串中获取想要的子串的函数  
> **函数原型：**  
> `string substr(int pos,int n=npos);`  
> 返回由pos开始的n个字符组成的子串，默认的npos是从pos到字符串结尾的所有字符的个数

测试案例

```cpp
void text08()
{
	//获取QQ邮箱前面的QQ号
	string str = "123456789@qq.com";
	int pos = str.find("@");
	string QQnumb = str.substr(0, pos);
	cout << "邮箱为：" << str << endl;
	cout << "QQ号为：" << QQnumb << endl;
}
```

![[Pasted image 20240529200338.png]]

