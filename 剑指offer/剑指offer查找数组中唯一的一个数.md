剑指offer:查找一个数组中唯一的数。

错误点：注意，在函数中要申请空间进行返回。
	并且要在数组外面进行创建。
	int num;
	但不能直接创建int* num;

void FindNumsAppearOnce(vector<int> data,int* num1,int *num2) {
    // 构建一个字典，然后进行查询,如果map可以的话
    // 除了两个数字，其他的数字都出现了两次
    // C++ 的迭代器是怎么实现的？

    map<int,int> m;

    for(auto each:data)
    {
        map<int,int>::iterator iter;
        iter = m.find(each);
        if(iter==m.end())
        {
            m[each] = 1;
        }
        else
        {
            m[each] = m[each]+1;
        }
    }

    map<int,int>::iterator iter;


    int flag = 0;
    for(iter = m.begin();iter!=m.end();iter++)
    {
        if(iter->second==1 && flag == 0)   {*num1 = iter->first;flag+=1;}
        if(iter->second==1 && flag == 1)   {*num2 = iter->first;}
    }
}


int main()
{

    vector<int >  array;
    array = {1,1,2,2,3,4,5,5};
    int num1;
    int num2;
//    num1  =0;
//    num2 = 0;
    FindNumsAppearOnce(array,&num1,&num2);
    cout<<num1<<num2<<endl;

}
