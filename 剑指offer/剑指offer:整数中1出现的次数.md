剑指offer:整数中1的出现次数（从1到n整数中1出现的次数）

int NumberOf1Between1AndN_Solution(int n)
    {
           // 这个问题的解法，我到现在还是不明就里
           // 感觉是分开计算
           // 首先求 2345 -- 22345
           // 先求万级别的1的个数，那就是10000-22345
           // 这道题有点难。
        
            // 找规律的方法，战略性放弃，就用普通的n^2的方法
            // 如果没有见过，用普通方法好一点。
        int count=0;
        if(n<1) return 0;
        for(int i=1;i<=n;++i)
            {
            int temp=i;
            while(temp)
                {
                if(temp%10==1)
                    ++count;
                temp/=10;
            }
        }
        return count;
    }

