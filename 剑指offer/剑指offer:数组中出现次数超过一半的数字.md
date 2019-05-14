剑指offer:数组中出现次数超过一半的数字

```c++
int MoreThanHalfNum_Solution(vector<int> numbers)
    {
        // 这道题重要的是思想，难度并不是很高。
        // 不能理解放弃patition的方法
        // 比较好的思想，是在左右问题中，很可能会遇到问题，什么问题呢？
        // {1,2,3,2,2,2,5,4,2}
        // {2,2,1,2,1,3}
        // 很骚的一个操作
        
        // 在世界的东方，有一条五爪金龙，它会去天空翱翔，而不是在平凡中死去。
        // [1,2,3,2,4,2,5,2,3] 这个东西该怎么克服？
        // 
        
        
        
        if(numbers.size()==0)return 0;
        
        int ans = 0;
        
        int r   = 1;
        ans = numbers[0];
        
        
        for(int i=0;i<numbers.size()-1;i++)
        {
            if(r==0)
            {
                ans = numbers[i+1];
                r = 1;
                continue;
            }
            
            
            if(ans==numbers[i+1])
            {
                r++;// r++;
            }
            else
            {
                r--;
            }
            if(r==0)
            {
                ans =0;
            }
        }
        
        // 重新遍历一遍，然后再输出相应的值
        int count = 0;
        for(int i=0;i<numbers.size();i++)
        {
            if(numbers[i]==ans)
            {
                count++;
            }
            
        }
        
        if(count<(numbers.size()/2+1))
        {
            return 0;
        }
       return ans;
    }
```
