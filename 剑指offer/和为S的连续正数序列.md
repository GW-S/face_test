剑指offer:和为S的连续正数序列
vector<vector<int> > FindContinuousSequence(int sum) {
    // This is two point question
    vector<vector<int> > ans;
    if(sum<3){
        return ans;
    }   
    
    

    int left  = 1;
    int right = 1;
    int now = 0;
    while(right<sum&&left<=sum-2)
    {

        while(now<sum){
            now += right;
            right +=1;
        }

        if(now == sum)
        {
            vector<int> temp;
            for(int i=left;i<right;i++)
            {
                temp.push_back(i);
            }
            ans.push_back(temp);
            now += right;
            right +=1;
        }


        while(now>sum&&left<=sum-2){
            now = now- left;
            left+=1;
        }


        if(now == sum)
        {
            vector<int> temp;
            for(int i=left;i<right;i++)
            {
                temp.push_back(i);
            }
            ans.push_back(temp);
            now -=left;
            left+=1;
        }
    }
    return ans;
}
