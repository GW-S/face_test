剑指offer:数字在排序数组中出现的次数

```C++
class Solution {
public:
    int GetNumberOfK(vector<int> data ,int k) {
        int nums = 0;
        for(auto each:data)
        {
            if(each==k)
            {
                nums ++;
            }
        }
        return nums;
    }
};
```
