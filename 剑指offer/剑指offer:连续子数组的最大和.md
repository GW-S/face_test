剑指offer:连续子数组的最大和

这道题的关键在于想清楚。

```C++
class Solution {
public:
    int FindGreatestSumOfSubArray(vector<int> array) {
    
        // 连续子数组的最大和
        // 从左到右扫一遍
        
        // 期望整数弥补
        // 6,-3,-2,7,-15,1,2,2
        // 绝望
        
        // 盛国威
        
        int ans = 0;
        int now_all = 0 ;
        
        int max = -100000;
        if(array.size()<=0)return 0;
        
        for(auto each:array)
        {
            
            if(max<each){max = each;}
            now_all = now_all + each;
            if(now_all<0){ now_all =0;}
            if(ans<now_all){ans = now_all;}
        }
        if(max<0)return max;
        return ans;
        
    }
};
```

