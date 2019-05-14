剑指offer:左旋转字符串

很强的一段操作。

```C++
public:
    string LeftRotateString(string str, int n) {
        
        if(str.length()==0)return "";
        
        
        string ans = "";
        for(int i=0;i<str.length();i++)
        {
           int w = (n+i)%str.length();
            ans+= str[w];
                
        }
        
        return ans;
    }
};





```
