剑指offer顺时针打印矩阵

---
在修改的时候用时30分钟，我艹，打代码太累了。

这道题的关键是，1.在写orient的时候，k是新定义的，容易有错
		2.在判断新节点的时候，直接在新节点上进行了赋值，导致以后会出现死循环
		3.在判断数组大小的时候，只对二维的情况进行了判断

```C++
static const int flag = -10000000;

pair<int,int>  next_step(int i,int j,int row,int col,int &now_orient_i,int &now_orient_j,vector<vector<int> >&matrix)
{
    const int flag = -10000000;
    
    i = i + now_orient_i;
    j = j + now_orient_j;

    if(i<row&&j<col&&i>=0&&j>=0)
    {
        if(matrix[i][j]!=flag)
        {
            pair<int,int> giveback(i,j);
            return giveback;
        }
    }

    i = i - now_orient_i;
    j = j - now_orient_j;// 相减的过程中

    int orient[] = {1,0,-1,0,0,-1,0,1};
    for(int k=0;k<8;k+=2)
    {
        int new_i = i + orient[k];
        int new_j = j + orient[k+1];

        if(new_i<row&&new_j<col&&new_i>=0&&new_j>=0)
        {
            if(matrix[new_i][new_j]!=flag)
            {
                // 返回值
                now_orient_i = orient[k];
                now_orient_j = orient[k+1];
                pair<int,int> v(new_i,new_j);
                return v;
            }
        }
    }
    pair<int,int> v(flag,flag);
    return  v;
}

vector<int> printMatrix(vector<vector<int> > matrix) {
    /*
     1   2   3  4
     5   6   7  8
     9  10  11 12
     13 14  15 16
    */
    // 用循环的方法去做
    vector<int> ans;
    if(matrix.size()<=0)   return ans;
    if(matrix[0].size()<=0)return ans;
    //
    int i = 0;int j = 0;
    int row = matrix.size();
    int col = matrix[0].size();
    int now_orient_i = 0;int now_orient_j = 1;

    pair<int,int> next(0,0);
    while(next.first!=flag&&next.second!=flag)
    {
        i  =next.first;
        j  =next.second;
        ans.push_back(matrix[i][j]);
        matrix[i][j]=flag;
        next = next_step(i,j,row,col,now_orient_i,now_orient_j,matrix);
    }
    return ans;
}
```
