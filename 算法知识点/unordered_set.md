[[hash数组]]

底层实现：哈希值的映射

无序集合(unordered_set)是一种使用哈希表实现的无序关联容器，其中键被哈希到哈希表的索引位置，因此插入操作总是随机的。无序集合上的所有操作在平均情况下都具有常数时间复杂度O(1)，但在最坏情况下，时间复杂度可以达到线性时间O(n)，这取决于内部使用的哈希函数，但实际上它们表现非常出色，通常提供常数时间的查找操作。

无序集合可以包含任何类型的键 - 预定义或用户自定义数据结构，但所有键必须是唯一的。它的语法如下：

`std::unordered_set<data_type> name;`

**常用方法**

- `size()`和`empty()`:用于获取大小和集合是否为空
- `find()`:用于查找键
- `insert()`和`erase()`:用于插入和删除元素

```c++
#include <bits/stdc++.h>
using namespace std;

int main()
{
	unordered_set<string> stringSet;

	stringSet.insert("code");
	stringSet.insert("in");
	stringSet.insert("c++");
	stringSet.insert("is");
	stringSet.insert("fast");

	string key = "slow";

	if (stringSet.find(key) == stringSet.end())
		cout << key << " not found" << endl << endl; //输出此分支
	else
		cout << "Found " << key << endl << endl;

	key = "c++";
	if (stringSet.find(key) == stringSet.end())
		cout << key << " not found\n";
	else
		cout << "Found " << key << endl;  //输出此分支

	cout << "\nAll elements : ";
	unordered_set<string>::iterator itr;
	for (itr = stringSet.begin(); itr != stringSet.end(); itr++)
		cout << (*itr) << ' ';  //fast is code c++ in
}

```
可以看到输出的顺序混乱，因为在无序集合中没有特定的数据存储顺序。

如果集合中不存在某个键，find()函数会返回一个指向end()的迭代器，否则会返回指向键位置的迭代器。迭代器充当键值的指针，因此我们可以使用*运算符来解引用它们以获取键。

**基于无序集合的实际问题**：已知一个整数数组，要找出其中的所有重复项。

```c++
#include <bits/stdc++.h>
using namespace std;

void printDuplicates(int arr[], int n)
{
	unordered_set<int> intSet;
	unordered_set<int> duplicate;

	for (int i = 0; i < n; i++) {
		if (intSet.find(arr[i]) == intSet.end())
			intSet.insert(arr[i]);
		else
			duplicate.insert(arr[i]);
	}

	cout << "Duplicate item are : ";
	unordered_set<int>::iterator itr;

	for (itr = duplicate.begin(); itr != duplicate.end(); itr++)
		cout << *itr << " ";  //5 1 2
}

int main()
{
	int arr[] = { 1, 5, 2, 1, 4, 3, 1, 7, 2, 8, 9, 5 };
	int n = sizeof(arr) / sizeof(int);
	printDuplicates(arr, n);
	return 0;
}

```

**其他方法**

|   Function Name    |            Function Description            |
| :----------------: | :----------------------------------------: |
|      insert()      |                  插入一个新元素                   |
|   begin()/end()    |        返回一个迭代器，指向第一个元素/最后一个元素后的理论元素        |
|      count()       |            计算在无序集合容器中特定元素的出现次数             |
|       find()       |                    搜索元素                    |
|      clear()       |                   清空所有元素                   |
|  cbegin()/cend()   |       返回一个常量迭代器，指向第一个元素/最后一个元素后的理论元素       |
|   bucket_size()    | 返回无序集合中特定桶(bucket)中的元素总数(元素通过哈希函数映射到不同的桶中) |
|      erase()       |              移除单个或某个范围内的一系列元素              |
|       size()       |                   返回元素数量                   |
|       swap()       |                交换两个无序集合容器的值                |
|     emplace()      |                在无序集合容器中插入元素                |
|     max_size()     |               返回可以容纳的最大元素数量                |
|      empty()       |                检查无序集合容器是否为空                |
|   equal_range()    |             返回包括与给定值相等的所有元素的范围             |
|  hash_function()   |              用于获取容器所使用的哈希函数对象              |
|     reserve()      |         它用于请求容器预留足够的桶数，以容纳指定数量的元素          |
|      bucket()      |                 返回特定元素的桶编号                 |
|   bucket_count()   |               返回无序集合容器中的总桶数                |
|   load_factor()    |  用于获取当前容器的负载因子。负载因子:元素数量与桶数之比，用于衡量容器的填充程度  |
|      rehash()      |             设置容器的桶数以容纳一定数量的元素              |
| max_load_factor()  |               获取或设置容器的最大负载因子               |
|   emplace_hint()   |       根据给定的提示位置(iterator)在容器中插入一个新元素       |
|      key_eq()      |        无序集合内部用于比较元素键值相等性的函数对象或谓词类型         |
| max_bucket_count() |              获取无序集合容器支持的最大桶数               |
