剑指offer:包含min函数的栈

这道题的关键是要想清楚。
class Solution {
public:
    stack<int> s;
    stack<int> assist;
    int min_store = 0;
    int flag = 1;
    
    void push(int value) 
    {
        s.push(value);
        if(flag==1)
        {
            min_store = value;
            flag =0;
            assist.push(value);
            return;
        }
        
        if(min_store>value)
        {
            min_store = value;
        }
            assist.push(min_store);
        
    }
    
    
    void pop() {
        s.pop();
        assist.pop();
        min_store = assist.top();
    }
    int top() {
        return s.top();
    }
    int min() {
        return min_store;
        
    }
};


