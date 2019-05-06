#剑指offer:数据流中的中位数。

#include<iostream>
#include<vector>
#include<stack>
#include<deque>
#include<queue>
#include<map>
#include<set>
#include<algorithm>

using namespace std;

class test
{
public:
    int flag = 0;
    int count = 0;
    vector<int> left;
    vector<int> right;


    void Insert(int num)
    {
        // 1,2,3,4,5,6,7,8,9,10
        // 判断数据流的大小
        if(count==0){left.push_back(num);count++;return;}
        if(count==1){right.push_back(num);count++;
            if(left[0]>right[0]){
                int temp  =left[0];
                left[0]  = right[0];
                right[0] = temp;
            }


            make_heap( left.begin() , left.end() , less<int>() );
            make_heap( right.begin(), right.end(), greater<int>()    );
            return;}


        if(flag==0) // 偶数情况下
        {
            if(num<right[0])
            {
                left.push_back(num);// 这是push.left;
                push_heap(left.begin(),left.end(),less<int>());
            }
            else{
                pop_heap(right.begin(),right.end(),greater<int>());
                int right_0 = right.back();
                right.pop_back();
                right.push_back(num);
                push_heap(right.begin(),right.end(),greater<int>());
                // 继续进行
                left.push_back(right_0);
                push_heap(left.begin(),left.end(),less<int>());
            }
        }

        if(flag==1)
        {
            if(num>left[0])
            {
                right.push_back(num);
                push_heap(right.begin(),right.end(),greater<int>());
            }
            else
            {
                pop_heap(left.begin(),left.end(),less<int>());
                int left_0 = left.back();
                left.pop_back();
                left.push_back(num);// 我什么都不想做了，感觉整个人已经废了

                push_heap(left.begin(),left.end(),less<int>());
                // 继续进行
                right.push_back(left_0);
                push_heap(right.begin(),right.end(),greater<int>());
            }
        }

        count++;
        flag = (flag+1)%2;

//        cout<<"start"<<endl;
//        cout<<count<<endl;
//        for(auto each:left) {cout<<"left"<<each<<" ";}
//        cout<<endl;
//        for(auto each:right){cout<<"right"<<each<<" ";}
//        cout<<endl;
    }

    double GetMedian()
    {
        if(count==0)return 0.0;
        if(count==1){return left[0];}
        if(count>=2)
        { double media=0.0;
            if(count%2==1)
            {
                media = left[0];
            }
            if(count%2==0)
            {
                media = ( (double)left[0] + (double)right[0] ) / 2;
            }
            return media;
        }
        return 0.0;
    };
};



int main()
{
    vector<int> ans = {5,2,3,4,1,6,7,0,8};

    test me = test();

    for(auto each:ans){me.Insert(each);cout<<me.GetMedian()<<endl;}
}


