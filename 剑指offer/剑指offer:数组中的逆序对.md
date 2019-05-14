剑指offer:数组中的逆序对

---
在整个制作过程中，主要是%10000007每一次都要%，最后一次，一定会爆掉，这已经是种不言而喻的提示，然后要用merge的方法可以大幅度提高效率，nlogn是不一样的，最后是其他。

```C++
void merge(vector<int> &data,int left,int right,int &count)
    {   // right 为可到达
        if(left==right)return;
        int media = (left + right)/2;
        merge(data,left,media,count);
        merge(data,media+1,right,count);

        int now = right;

        vector<int> l,r;// 不懂该怎么搞，这是个问题。
        l.assign(data.begin()+left,data.begin()+media+1);
        r.assign(data.begin()+media+1,data.begin()+right+1);

        // 辅助数组,左侧的数组；
        int point_l  = l.size()-1;
        int point_r  = r.size()-1;

        while(point_l>=0&&point_r>=0)// 当两者都大于0的时候
        {
            if(  l[point_l]>r[point_r]      )
            {
                data[now] = l[point_l];
                count += point_r +1;
                count = count%1000000007;
                point_l--;
                now--;
                continue;
            }
            data[now]=r[point_r];
            point_r--;
            now--;
        }
        while(point_l>=0)
        {
            data[now]=l[point_l];
            now--;
            point_l--;
        }
        while(point_r>=0)
        {
            data[now]= r[point_r];
            now--;
            point_r--;
        }
    }

    int InversePairs(vector<int> data) {
        // 解决方法有两种，1种是最普通的n^2的方法
        // 另外一种是merge的方法，不断merge,然后返回排序后的结果
        // 在merge的过程中，不断计算值的大小
        // 那么关键在如何merge了，直接从中间split
        // 给一个count给他

        int count = 0;

        if(data.size()<2)return 0;

        merge(data,0,data.size()-1,count);

        return count%1000000007;



    }
```
