
#  1、报错：
## 1、 runtime error: reference binding to null pointer of type ‘int‘ (stl_vector.h)

报错原因：vector在还没有分配任何空间时还不能像数组一样用下标形式去访问vector的（v[0]也不行）！！！否则编译通过但报运行错误runtime error！

如**vector创建的时候是使用：**

```cpp
vector<int> v;
```
或者vector还是[]的时候（考虑官方测试数据的输入可能为[]的情况，使用[ ]前需要判断一下是否为空）
会报错！
如：v[0]=1、if(v[0])、v[0]等情况都会报错，我们都知道数组是静态分配内存，创建时就要确定大小然后给它分配空间不然直接编译报错，但vector是动态数组，像"vector<\int>  v"这种跳过分配空间的创建方式是允许的，编译器不会报错，但会运行报错即runtime error。
这种情况需要先push_back()或v={1，2}等形式给其分配了空间后，才能用【】形式访问！

# vector<\string> 类型的赋值

参考例子：[[150、逆波兰表达式求值]]

`vector<string> tokens = {"2","1","+","3","*"};`

>记住这是个容器，不能和string的赋值混为一谈。