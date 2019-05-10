剑指offer:孩子们的游戏

这道题两种解法，但另一种解法，必须要背下来递归式，否则推不出来的。

```C++
class Solution {
public:
    int LastRemaining_Solution(int n, int m)
    {
        // m-1
        // 模拟法
        // 有没有更好的方法？
        // 0,1,2,3,4,5,6 复杂度n*m 
        // 有没有更好的方法？
        if(n<1||m<1)return -1;
        
        int last = 0;
        for(int i=2;i<=n;i++)
            last = (last+m)%i;
        return last;
    }
};
```
