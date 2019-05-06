剑指offer:寻找固定windows中的最大值：


#include<iostream>
#include<vector>
#include<algorithm>

using namespace std;

// 对于vector来说，机会没有找到最大值的解决方案，只能自己写一个。
// 理论上有vector<int>::iterator有可能做到，但问题是，在clang里面用不了。
// 用是可以用的，叫max_element,返回一个vector<int>::iterator ,是一个指针。
// 但实际上，给我们的输入却是num,那整个人就曹乐。

int find_Max(vector<int>num,int x,int y){
    int ans = 0;
    for(int i= x;i<y;i++)
    {
        ans = ans>num[i]?ans:num[i];
    }
    return ans;
}




vector<int> maxInWindows(const vector<int>& num, unsigned int size) {

    vector<int> ans;

    if (size == 0||num.size()<size)return ans;


    int point_r = (int) size;
    int point_l = 0;


    int big = find_Max(num,point_l,point_r);
    ans.push_back(big);

    point_r += 1;
    point_l += 1;
    while (point_r <= num.size()) {

        if (num[point_l - 1] == big) {
            big = find_Max(num,point_l,point_r);
        } else {
            if (big >= num[point_r-1]) {

            } else {
                big = num[point_r-1];// big = point_r

            }
        }

        ans.push_back(big);
        point_l += 1;
        point_r += 1;
    }

    return ans;
}





int main()
{
    int mat[]  ={2,3,4,2,6,2,5,1 };
    vector<int> input;
    input.assign(mat,mat+8);

    for(auto each:input)cout<<each<<endl;
    vector<int>  ans = maxInWindows(input,3);

    for(auto each:ans)cout<<each<<endl;

}

// {2,3,4,2,6,2,5,1}
// {4,4,6,6,6,5}
