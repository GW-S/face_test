剑指offer_序列化二叉树:
    这道题的难点是，一个数字有可能是两位数，或者是三位数。
    另一个难点是，C++的一个局部变量，如果不创建空间而返回的话，很可能返回的是乱码。简直丧心病狂。
    最关键的是，在构建树的过程中，是一定要有返回值的。

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
    char* Serialize(TreeNode *root) {

        string a;
        if(root==NULL)
        {
            a = "#";

            char* b = (char*)a.c_str();


            char* result = new char[strlen(b)];
            stpcpy(result,b);
            return result;
        }
        char* left  = Serialize(root->left);
        char* right = Serialize(root->right);


        a = to_string(root->val);
        a.push_back(',');

        char* now  = (char*)a.c_str();
        char* result = new char[strlen(left)+strlen(right)+strlen(now)];

        strcpy(result,now);
        strcat(result,left);
        strcat(result,right);
        //cout<<"@"<<result<<endl;
        return result;
    }

    TreeNode* decode(char* str,int &i,int size)
    {
        //cout<<i<<"_";
        if(i>=size)    return NULL;
        if(str[i]=='#'){i++;return NULL;}

        int j = i;
        int v = 0;

        int num = 1;


        while(str[j]!=',')
        {
            j++;
        }
        int t = j-1;
        while(t>=i)
        {
            v = (str[t]-'0') * num +v;
            num *= 10;
            t--;
        }

        //cout<<v<<" ";
        TreeNode* node = new TreeNode(v);

        i = j + 1;

        node->left  = decode(str,i,size);//decode里面很可能什么也没有
        node->right = decode(str,i,size);

        return node;
    }


    TreeNode* Deserialize(char *str) {

        int i = 0;
        TreeNode* ans  = decode(str,i,strlen(str));
        return ans;

    }
};
:wq /Users/sheng/Desktop/剑指offer_序列化二叉树.md
:wq /Users/sheng/Desktop/剑指offer_序列化二叉树.md
