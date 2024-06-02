[[char类型]]
# 1、vector<\char>类型转化为string类型

示例代码：

```cpp
int main(){
	char ans = {'a', 'b', 'c'};
	string output(ans.begin(), ans.end());
	cout << output <<endl;
	return 0;
}
```

