剑指offer:变态跳台阶

这道题的难点在于对于中间的一个点，有很多个点,从过去到这里，从这里到未来。

def jumpFloorII(self, number):
        # write code here
        # 难受
        # 动态规划的题
        
        # 跳这么多步的方法有几个
        # 是不是达到了目标
        # 
        if number==0:
            return 0
        
        ans = 0 # 当前的值
        sum_pre  = 0# 前面所有的和
        
        i = 1
        while(i<=number):
        
            ans = sum_pre + 1
            sum_pre = ans + sum_pre
            i+=1
        
        return ans

