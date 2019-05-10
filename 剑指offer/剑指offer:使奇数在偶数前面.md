剑指offer：调整顺序使奇数在偶数前面

```C++
class Solution {
public:
    void reOrderArray(vector<int> &array) {
        
        
        //1 2 3 3 4 6 8 8 9 6
        // 新建奇数和偶数，数组，然后追加
        
        vector<int> odd;
        vector<int> even;
        
        for(auto each:array)
        {
            if(each%2==1)
            {
                odd.push_back(each);
            }
            else{
                even.push_back(each);
            }
        }
        
        for(int i=0;i<odd.size();i++)
        {
            array[i] = odd[i];
        }
        for(int i=0;i<even.size();i++)
        {
            array[odd.size()+i] = even[i];
        }
        
        
    }
};
```
