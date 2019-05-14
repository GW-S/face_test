剑指offer:二进制中1的个数
---
反思：在这道题中，我的第一个错是用除法版本可能有错，第二个版本是负数在计算机中是用补码表示的。
反正这道题牛逼就是了。


class Solution {
public:
     int  NumberOf1(int n) {
         // 左移补1，右移补0

         
         // 这道题有一个很要命的点，那就是负数其实是用补码来表示的。
         // 在计算机系统中，负数本身就是用补码来表示的。
         // 而这道题的想法非常天才，它用的是另一种方法.
         // flag中的词我要考虑到。
         
         int ans = 0;
         int flag = 1;
         while(flag)
         {
             int now = flag & n;
             if(now!=0)ans++;
             flag = flag<<1;
         }
         return ans;       
     }
};

