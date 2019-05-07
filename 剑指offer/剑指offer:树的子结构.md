剑指offer:树的子结构

这道题主要犯下的错误是错误理解题意，以及在打代码过程中的失误。
所以，不管怎么样，疏通逻辑，检查逻辑都是应该的。

```c++
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
    bool pre_find(TreeNode* one,TreeNode* two)
    {   
        bool first,second=false;
        //左右
            // 两者为nULL
            // 两者不为NULL
                // 值是否一样
        if(two==NULL) return true;
        
        if(two!=NULL)
        {
            if(one==NULL)return false;
            
            if(one->val!=two->val){return false;}
            // 判断左右结
            if(two->right==NULL){second=true;}
            if(two->right!=NULL)
            {second = pre_find(one->right,two->right);}
            if(two->left==NULL){first=true;}
            if(two->left!=NULL)
            {first  = pre_find(one->left,two->left);}
        }
         if(first==true&&second==true)
        {
            return true;
        }
        return false;
    }
    
    
   
    bool HasSubtree(TreeNode* pRoot1, TreeNode* pRoot2)
    {
        if(pRoot2==NULL)return false;
        if(pRoot1==NULL)return false;
        
        queue<TreeNode*> q;
        q.push(pRoot1);// 省略
        
        while(!q.empty())
        {
            TreeNode* now = q.front();
            q.pop();
            if(now->left )q.push(now->left) ;
            if(now->right)q.push(now->right);
            
            TreeNode* temp = pRoot2;
            bool find = pre_find(now,temp);
            if(find==true)return true;
        }
        return false;
    }
};
```
