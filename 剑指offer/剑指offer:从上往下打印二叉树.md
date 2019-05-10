剑指offer:从上往下打印二叉树
---
恕我直言，这道题对我来说，已经毫无难度。

```C++
/*javascript:void(0);
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
    vector<int> PrintFromTopToBottom(TreeNode* root) {
        // 这是一个很简单的题。
        // 从上往下打印二叉树的每个节点
        vector<int> ans;
        if(root==NULL)return ans;
        queue<TreeNode*> q0;
        queue<TreeNode*> q1;
        int flag = 0;
        
        q0.push(root);
        
        while(!q0.empty()||!q1.empty())
        {
            if(flag==0){
                while(!q0.empty())
                {
                    TreeNode* now = q0.front();
                    q0.pop();
                    ans.push_back(now->val);
                    if(now->left)q1.push(now->left);
                    if(now->right)q1.push(now->right);
                }
            }
            // 
            if(flag==1){
                while(!q1.empty())
                {
                    TreeNode* now = q1.front();
                    q1.pop();
                    ans.push_back(now->val);
                    if(now->left)q0.push(now->left);
                    if(now->right)q0.push(now->right);
                }
            }
            
            flag = (flag+1)%2;
                
        }
        
        return ans;
        
    }      
};
```

