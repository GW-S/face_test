剑指offer:对称的二叉树

这道题的思路就是二叉树的层次遍历。
但问题是，在遍历的过程中，有一个步骤是判断是否是空节点。
有四种情况，左节点是空，右节点是空，等等，等等。
这会面临一个问题，那就是如果是左右左右的顺序，那么会导致右被添加在前面。
这告诉我们，针对某一个条件，最好还是ifelse,而不是分开写if。

#include<iostream>
#include<vector>
#include<stack>
#include<deque>
#include<queue>

using namespace std;

struct TreeNode {
    int val;
    struct TreeNode *left = NULL;
    struct TreeNode *right = NULL;
};


// 判断是否能够输出
bool isSymmetrical(TreeNode* pRoot)
{

    deque<int> d;

    queue<TreeNode*> q0;
    queue<TreeNode*> q1;

    if(pRoot==NULL)
    {
        return true;
    }

    int flag = 1;
    int stick = -99999999;


    q0.push(pRoot);

    while(!q0.empty()||!q1.empty())
    {
        if(flag == 1)
        {
            while(!q0.empty())
            {
                TreeNode* front  = q0.front();
                q0.pop();
                // 左右进行操作
                if(front->left==NULL)
                {
                    d.push_back(stick);
                    //cout<<d.back()<<' ';
                }

                if(front->left!=NULL)
                {
                    q1.push(front->left);
                    d.push_back(front->left->val);
                    //cout<<d.back()<<' ';
                }

                if(front->right==NULL)
                {
                    d.push_back(stick);
                    //cout<<d.back()<<' ';
                }
                if(front->right!=NULL)
                {
                    q1.push(front->right);
                    d.push_back(front->right->val);
                    //cout<<d.back()<<' ';
                }
                //cout<<d.back()<<' ';// 这是什么意思？我艹
            }
            //cout<<endl;
        }

        if(flag == 0)
        {
            while(!q1.empty())
            {
                TreeNode* front  = q1.front();
                q1.pop();
                // 左右进行操作
                if(front->left==NULL)
                {
                    d.push_back(stick);
                    //cout<<d.back()<<' ';
                }

                if(front->left!=NULL)
                {
                    q0.push(front->left);
                    d.push_back(front->left->val);
                    //cout<<d.back()<<' ';
                }


                if(front->right!=NULL)
                {
                    q0.push(front->right);
                    d.push_back(front->right->val);
                    //cout<<d.back()<<' ';
                    // 这是什么意思？
                }
                if(front->right==NULL)
                {
                    d.push_back(stick);
                    //cout<<d.back()<<' ';
                }

                //cout<<d.back()<<' ';
            }
            //cout<<d.size();
            //cout<<endl;
        }

        // 这个地方我不能理解
        while(d.size()>=2)
        {
            //cout<<"start"<<endl;
            int left  = d.front();
            d.pop_front();
            int right = d.back();
            d.pop_back();

            //cout<<left<<' '<<right<<endl;
            //cout<<"end"<<endl;

            if(left!=right)return false;
        }
        while(!d.empty())
        {
            d.pop_front();
        }
        // 更新flag
        flag  = (flag+1)%2;
    }
    return true;
}

// 层次遍历输出
void print(TreeNode* test) {
    queue<TreeNode *> q0, q1;
    q0.push(test);

    int flag = 1;
    while (!q0.empty() || !q1.empty()) {
        // 接下来该怎么办？
        if (flag == 1) {
            while (!q0.empty()) {
                TreeNode *front = q0.front();
                q0.pop();
                cout << front->val;
                if (front->left != NULL) q1.push(front->left);
                if (front->right != NULL) q1.push(front->right);
            }
            cout << endl;
        }

        if (flag == 0) {
            while (!q1.empty()) {
                TreeNode *front = q1.front();
                q1.pop();
                cout << front->val;
                if (front->left != NULL) q0.push(front->left);
                if (front->right != NULL) q0.push(front->right);
            }
            cout << endl;
        }

        flag = (flag+1) % 2;
    }
}


int main(){
    TreeNode* node = new TreeNode;
    node->val  = 5;
    node->left  = new TreeNode;node->left->val  = 3;
    node->right = new TreeNode;node->right->val = 3;

    node->left->left = new TreeNode;node->left->left->val = 4;
    //node->left->right = new TreeNode;node->left->right->val = 4;

    //node->right->left = new TreeNode;node->right->left->val = 4;
    node->right->right = new TreeNode;node->right->right->val = 4;

    node->left->left->left = new TreeNode;    node->left->left->left->val = 2;
    node->right->right->right = new TreeNode; node->right->right->right->val = 2;//这是什么操作？我不懂啊。

    //TreeNode* n  =KthNode(node,4);
    //cout<<n->val<<endl;

    //print(node);

    bool me = isSymmetrical(node);
    cout<<me<<endl;

    // {8,6,9,5,7,7,5}


    // 5,3,3,4,#,#,4,2,#,#,2,1,#,#,1



}
