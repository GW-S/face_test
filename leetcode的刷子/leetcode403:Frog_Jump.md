leet_code_403:Frog_jump

---
这道题是一个很骚的操作。
主要将的是青蛙跳的过程。
其实可以转换为深度有限搜索。
但DP可能更快一点。
我所理解的DP可能是先判断递归，再不断的从左至右，或者在数组中进行更新。
但DP的实质很可能不是最俭的，DP更可能只是个记录的过程，记录下来，然后再去查表。
他节省的是不去计算老数据的时间，而不是减少查找的次数。

```C++
class Solution {
public:
        
   bool canCross(vector<int>& stones) {
    // 3：10分完成这道题的刷子
    // 还是没有刷完。
    // 0,2 
       
    map<int,set<int> > m ;

    for(auto each:stones)
    {
        if(m.find(each)==m.end())m[each] = set<int>();
    }

    int result = stones[stones.size()-1];
       
    if(stones.size()==1)return 1;
    for(int i=0;i<stones.size();i++)
    {
        if(i==1){ if((stones[i]-stones[i-1])!=1){return 0;}; m[stones[i]].insert(1); }
        
        if(i==0)
        {
            m[stones[i]].insert(1);
            continue;
        }
        
        
        
        
        if(m[stones[i-1]].size()==0)continue;

        int now_pos   = stones[i-1];

        for(auto now_swift:m[now_pos])
        {
            int add[] = {-1,0,1};
            for(auto item:add)
            {
                int new_pos = item + now_swift + now_pos;

                if(new_pos == result)return true;

                if(m.find(new_pos)!=m.end())
                {
                    m[new_pos].insert(item+now_swift);
                }
            }
        }
    }
    return false;
}

};
```
