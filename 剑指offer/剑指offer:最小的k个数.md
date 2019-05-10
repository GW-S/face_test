剑指offer:最小的k个数

vector<int> GetLeastNumbers_Solution(vector<int> input, int k) {
        
        // sort 一下，然后找
        // 那直接用堆解决一下
        // 一种思想是，不断的交换，并且不断的切下去
        // 而另一种思想是，……
        // index我简直无法理解
        // 我无法理解不断切割的过程，怎么
         vector<int> ans;
        if(input.size()<k)return ans;
        
        
        priority_queue<int> q;
        for(auto each:input)
        {
            q.push(each);
            if(q.size()>k)
            {
                q.pop();
            }
        
        }
        
       
        while(!q.empty())
        {
            ans.push_back(q.top());
            q.pop();
        }
        return ans;
        
    }
};
