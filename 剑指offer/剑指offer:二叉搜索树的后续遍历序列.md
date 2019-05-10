剑指offer:二叉搜索树的后续遍历序列

---
这道题做了很久，因为没有把思路梳理清楚，各种边缘变量在写的时候考虑，而大体方针要尽早确定下来

```
# -*- coding:utf-8 -*-
class Solution:
    def VerifySquenceOfBST(self, sequence):
        # write code here
        #

        # 获取最后一个
        # 划分其他小于该值，大于该值
        # 输出yes,输出no,评什么？

        # 后序遍历  + Yes + No
        # 如果是，则输出yes,如果不是，则输出no
        # 二叉搜索树，那就左边小，右边大

        # 给一个数组，如何复原后续遍历
        # 先搜索左，再搜索右


        # 逻辑一定要理清楚再做题

        if (len(sequence) == 0):
            return 0
        if(len(sequence)==1):
            return 1
        now   = sequence[-1]

        left_pos = 0
        right_flag = 0

        if(sequence[0]<now):    # left
            for index,each in enumerate(sequence):
                if(each>now):  # each>=now
                    left_pos = index
                    break
                if(each==now):
                    right_flag = 1
        if(left_pos== 0 ):
            left = []
        else:
            left  = sequence[0:left_pos]  # 我想要吹着海风，在树上唱歌
        if(right_flag ==1):
            right = []
        else:
            right = sequence[left_pos:-1]

        # 盛国威很难受，非常难受
        if(len(left)==0):
            l = 1
        else:
            if (max(left) < now):
                A = Solution()
                l = A.VerifySquenceOfBST(left)
            else:
                return 0

        if(len(right)==0):
            r = 1
        else:
            if (min(right) > now):
                B = Solution()
                r = B.VerifySquenceOfBST(right)
            else:
                return 0

        if (r == 1 and r == 1):
            return 1
```
