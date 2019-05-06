剑指offer:二叉树的下一个节点
问题在于，比较运算符的==忘记写。
考虑问题不够全面。

```c++
TreeLinkNode* GetNext(TreeLinkNode* pNode)
    {
        // 我真的不知道该怎么搞。
        // 树的节点不仅包含左右节点，同时包含指向父节点的指针
        // pNode是什么东西啊，窝草；
        // 假设是从右节点回去了，那该怎么办？我母鸡啊。
        // 看你是不是在左节点上，如果是左节点，又是一个轮回
        
        if(pNode==NULL)return NULL;
        if(pNode->right!=NULL){
            pNode = pNode->right;
            while(pNode->left!=NULL)
            {
                pNode = pNode->left;
            }
            return pNode;
        }
        else{
            while(pNode->next!=NULL)//有前节点
            {
                if(pNode->next->left==pNode)
                {      
                    return pNode->next;
                }
                // 如果是右节点，怎么办？找到下一个做节点
                pNode = pNode->next;
                // 左右，左右，左右
            }
            return NULL;
        }
        return NULL;
    }
```
