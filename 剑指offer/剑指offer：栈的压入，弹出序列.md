剑指offer:栈的压入、弹出序列

---
这道题只要做就好了


class Solution {
public:
    bool IsPopOrder(vector<int> pushV,vector<int> popV) {
        // 
        // 
        // 构建一个栈呗
        // 栈顶
        // point
        //、 建一个栈
        
        stack<int>  q;
        int point = 0;// push的指针
        for(auto each:popV)
        {
            
            // 对于某一个数去找
            // 挫商也很重要
            
            if(!q.empty())
            {
                if(q.top() == each){q.pop();continue;}
            }
            if(point==pushV.size())return false;
            if(pushV[point]==each){point++;continue;}
            
            //int flag = 0;
            while(pushV[point] != each && point<pushV.size() )
            {
                q.push(pushV[point]);
                point++;
            }
            if(point>=pushV.size())return false;
            point++;
                
           
        }
        
        return true;
        
    }
};


