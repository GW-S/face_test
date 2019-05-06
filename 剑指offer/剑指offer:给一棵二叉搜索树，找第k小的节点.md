// 在这个过程中，我们发现，整个过程发生段错误，也就是说，我的node无法push上去。

/*
struct TreeNode {
    int val;
    struct TreeNode *left;
    struct TreeNode *right;
    TreeNode(int x) :
            val(x), left(NULL), right(NULL) {
    }
};
*/
class Solution {
public:
    TreeNode* KthNode(TreeNode* pRoot, int k)
{
    if(pRoot==NULL||k==0)return NULL;
    stack<TreeNode*> s;
    s.push(pRoot);// 我该怎么办？
 
    while(pRoot->left!=NULL)
    {
        pRoot = pRoot->left;
        s.push(pRoot);
    }
     
    while(!s.empty())
    {
        TreeNode* node = s.top();
        k--;// 最后的k--，作为最终的输出
        if(k==0)return node;
        s.pop();
 
        if(node->right!=NULL)
        {
            node = node->right;
            s.push(node);
            while(node->left!=NULL)
            {
                node = node->left;
                s.push(node);
            }
        }
    }
    return NULL;
}   
};
