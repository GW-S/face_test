# 剑指offer，求和为S的值

这道题要注意的是，在程序的中途，也要进行判断。




vector<int> FindNumbersWithSum(vector<int> array,int sum) {

                
        int min = 100000000;
        int ans1;
        int ans2;
        int l_p = 0;
        int right_p = array.size()-1;
        int flag  =0;

        while(l_p<right_p)
        {
            if(array[l_p] + array[right_p] > sum)
            {right_p--;}
            if((array[l_p] + array[right_p] < sum)&&l_p<right_p)
            {l_p++;}
            if(array[l_p]+array[right_p]==sum)
            {
                int now = array[l_p]*array[right_p];
                if(now<min)
                {
                min = now;
                ans1 = array[l_p];
                ans2 = array[right_p];
                flag = 1;
                }
                
                l_p++;
                right_p--;
            }
        }
        vector<int> ans;
        if(flag==1){
            
        
        ans.push_back(ans1);
        ans.push_back(ans2);}
        return ans;
    }
};
