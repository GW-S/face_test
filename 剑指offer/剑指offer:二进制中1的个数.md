15:二进制中1的个数
---
```cpp
class Solution {
public:
     int  NumberOf1(int n)
     {
         int ans  = 0;
         int flag = 1;
         while(flag)
         {
             int now = flag & n;
             if(now!=0)ans++;
             flag    = flag<<1;
         }
         return ans;       
     }
};
```
