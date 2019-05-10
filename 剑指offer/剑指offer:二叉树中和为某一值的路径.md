剑指offer:二叉树中和为某一值的路径

---
这道题的难点，在于，vector是可以使用sort函数的，这个我没有记住，用法是sort(vector.begin(),vector.end(),cmp)
同样，这道题开始想的是用宽度有限搜索来做，但事实上，它要反应出路径的所有的长度。
综上，我认为，我应该仔细考量整个过程再写代码。

还有一个要求是，cmp,要用的是一个静态成员函数，那就加上一个static就可以了。

```C++
/*
struct TreeNode {
	int val;
	struct TreeNode *left;
	struct TreeNode *right;
	TreeNode(int x) :
			val(x), left(NULL), right(NULL) {
	}
};*/
class Solution {
public:
    
    void Find(TreeNode* node,int height,int expectNumber,vector<vector<int>> &ans,vector<int> now_path)
    {
        // 是时候学习一下java了
        if(node==NULL)        return;
        height = height + node->val;
        now_path.push_back(node->val);
        if(height == expectNumber&&node->left==NULL&&node->right==NULL)
        {
            ans.push_back(now_path);
            return;
        }
        if(node->left) Find(node->left,height,expectNumber,ans,now_path);
        if(node->right)Find(node->right,height,expectNumber,ans,now_path);
    }
    
    static bool cmp(vector<int> &a,vector<int> &b)
    {
        return a.size()>b.size();
    }
    
    
    vector<vector<int> > FindPath(TreeNode* root,int expectNumber) {
        // 输入一颗二叉树的根节点和一个整数
        // 如果expectNumber不在节点中呢？
        // 还要所有路径
        // 其实蛮简单的，就是从上到下，疯狂的输出所有能输出的单词，长度大的靠前，那就是宽度优先呗
        // 思虑贵在详实周密
        // 整个叶节点中的路径
        // 先序遍历，需要一个值作为输入，一个路径作为输入
        // A遍历完之后，再遍历B，最后遍历C
         vector<vector<int> > ans;

        if(root==NULL)return ans;
        
        int height = 0;
        
        vector<int> now_path;
        
        Find(root,height,expectNumber,ans,now_path);
        
        sort(ans.begin(),ans.end(),cmp);// 全新的开始？草

        return ans;
    }
};
```

