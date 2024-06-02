>头文件：`#include <algorithm>  `

常用形式：
`sort(nums.begin(), nums.end())`

如：
```cpp
#include <algorithm>  
#include "iostream"  
#include "vector"  
  
using namespace std;  
  
int main(){  
    vector<int>nums = {2,3,6,4,8,9};  
    sort(nums.begin(), nums.end());  
//    sort(nums.end(), nums.begin());  没输出
    for(int num : nums){  
		cout << num << ";";
    }  
    cout << endl;  
    return 0;  
}
```
输出：
2;3;4;6;8;9;