[CSDN用法详解](https://blog.csdn.net/zou_albert/article/details/106983268)
[c++中unordered_map的用法的详述（包含unordered_map和map的区别）_unorder map-CSDN博客](https://blog.csdn.net/jpc20144055069/article/details/108170073)
https://zh.cppreference.com/w/cpp/container/unordered_map/erase

# 简介：
> - unordered_map是一个将key和value关联起来的容器，它可以高效的根据单个key值查找对应的value。
> - <font color='red'>key值应该是唯一的</font>，key和value的数据类型可以不相同。
> - unordered_map存储元素时是没有顺序的，只是根据key的哈希值，将元素存在指定位置，所以根据key查找单个value时非常高效，平均可以在常数时间内完成。
> - unordered_map查询单个key的时候效率比map高，但是要查询某一范围内的key值时比map效率低。
> - 可以使用[]操作符来访问key值对应的value值。
##  头文件

- map: \#include < map >
- unordered_map: \#include < unordered_map >
# 内部实现机理
 - map： map内部实现了一个红黑树，该结构具有自动排序的功能，因此map内部的所有元素都是 **有序** 的，红黑树的每一个节点都代表着map的一个元素，因此，对于map进行的查找，删除，添加等一系列的操作都相当于是对红黑树进行这样的操作，故红黑树的效率决定了map的效率。
 - unordered_map: unordered_map内部实现了一个哈希表，因此其元素的排列顺序是杂乱的，无序的 

# 基本使用

```c++
#include <iostream>
#include <unordered_map>
using namespace std;

int main()
{
    unordered_map<string, int> umap;

    umap["GeeksforGeeks"] = 10;
    umap["Practice"] = 20;
    umap["Contribute"] = 30;

    for (auto x : umap)
        //Contribute=30 GeeksforGeeks=10 Practice=20
        cout << x.first << "=" << x.second << ' ';
}

```

# 函数

![[Pasted image 20240516202106.png]]

## 1）find函数
>`umap.find(key) == value`，要注意find是查找键值*key* ，返回对应的 *value* 。

比如说：
[[383、赎金信]]
