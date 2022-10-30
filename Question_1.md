```cpp
#include <bits/stdc++.h>
using namespace std;
class Solution {
public:
//    vector<int> twoSum(vector<int>& nums, int target)
    void twoSum(vector<int>& nums, int target)
    {
        unordered_map<int, int> hashtable;
        for (int i = 0; i < nums.size(); ++i)
        {
            auto it = hashtable.find(target - nums[i]);
//            auto it = hashtable.begin();
//            if (it != hashtable.end())
//            {
//                return {it->second, i};
//            }
            if (it != hashtable.end())
            {
                cout << it ->first << " " << it ->second << " " << i << endl;
//                it ++;
            }
            hashtable[nums[i]] = i;

        }
//        return {};
    }
};
int main(void)
{
//    Solution num_1;
    vector<int>arr;
    arr.push_back(3);
    arr.push_back(2);
    arr.push_back(4);
//    arr.push_back(9);
    vector<int>arr_1;
    Solution num;
//    arr_1 = num.twoSum(arr,12);
    num.twoSum(arr,6);
//    cout << arr_1[0];
//    cout << arr_1[1];
//    arr_1 = Solution::twoSum(arr,4);
}

```

```cpp
cout << it ->first << " " << it ->second << " " << i << endl;
```

# Head
## test_1遍历
3 0 0
2 1 1
4 2 2
## find()
3 0 0
> 分析：
> 这里如果把预处理放在前面，就提前把3给储存进去了
> 这个时候的如果我再查找的话，迭代到3的时候3并不是最后一个元素

2 1 2


---
# Last
## test_2遍历
3 0 1
//第二次打印出第一次储存的数据
>这里能有效防止重复

2 1 2

## find()
2 1 2
>这里能有效防止重复 是因为  target - nums[i]
> 在调试的时候我们会发现 第二次打印出第一次储存的数据
> 
> 因为我们是在后面做预处理 可以想象
> 在循环进行第一次的时候 num[0] 这个时候要找的就是 (target  - num[0])
> 但是 这个时候没有数据，所以找不到
> 
> 在第二次的时候 已经把第一次的数据存进去了
> 在循环进行第二次的时候 num[1] 这个时候要找的就是 (target  - num[1])
> 但是它找的话，它**_只能从第一次存进去_**的数据去找
> 再强调一次**_只能从第一次存进去_**
> 也就是0时没数据 ; 1时找0 ; 2时找0,1 ; 3时找0,1,2！
> 这样，就完美的避免了自己找自己的问题了！

# 小结:
>每次找都是向前找，如果提前储存好的话就可以找到自己

>这里又引申出来，如果题目要求可以找自己就放前面
> 不能就放后面