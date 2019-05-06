剑指offer:二维数组中的查找
这道题卡了我一段时间，主要是因为在while的时候，要注意while的停止问题，还有是因为写的思路不够缜密，如果自己写个测试用例，然后在当前逻辑上进行优化，确定逻辑是对的再写。痛点在<写错。

我们发现牛客网说循环多，那真的循环多。循环完了，才是内存炸了。
凡此种种，此后再言。

// 明显循环有问题,到底是哪里的问题
bool Find(int target, vector<vector<int> > array)
{
    int i,j;

    i = array.size()-1;   // 横轴

    if(i<0) return false; //

    j = array[0].size()-1;// 纵轴

    if(j<0) return false;

    if(array[i][j]<target)return false;

    if(array[0][0]>target)return false;

    int line_i = 0;

    int line_j = 0;


    while(line_i<i)
    {
        //cout<<array[line_i][j]<<endl;
        //cout<<target<<endl;
        if(array[line_i][j]<target)
        {
            line_i++;
            //cout<<line_i<<endl;
        }

        else{break;}
    }
    while(line_j<j)
    {
        if(array[i][line_j]<target)line_j++;
        else{break;}
    }

    // 0,2
    //


    //
    for(int w = line_i;w<=i;w++)
    {
        for(int k=line_j;k<=j;k++)
        {
            if(array[w][k]==target)return true;
        }
    }

    return false;
}
int main(){


    vector<vector<int> >  array;
    vector<int> temp = {1,2,3};
    array.push_back(temp);
    temp = {4,5,6};
    array.push_back(temp);
    temp = {7,8,9};
    array.push_back(temp);

    cout<<Find(5,array);

    // 1,2,3,
    // 4,5,6,
    // 7,8,9,  问题出在哪里？

