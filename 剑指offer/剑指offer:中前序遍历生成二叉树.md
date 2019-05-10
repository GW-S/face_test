剑指offer:重建二叉树
---
难点在于：python中的if一定要加两个点，而对于右节点一定要考虑溢出问题。

```python
# -*- coding:utf-8 -*-
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
class Solution:
    
    
    # 返回构造的TreeNode根节点
    
    
    def reConstructBinaryTree(self, pre, tin):
        
        
        
        def tree(pre,tin):
            if(len(pre)==0):return None
            if(len(pre)==1):return TreeNode(pre[0])
            now = pre[0]# 0 # 如果只有一个呢
            left_tin  = tin[0:tin.index(now)]
            left_pre  = pre[1:len(left_tin)+1]
            if len(tin)>tin.index(now)+1:
                right_tin = tin[tin.index(now)+1:]
                right_pre = pre[len(left_tin) +1:]
                treeNode_right = tree(right_pre,right_tin)
            else:
                treeNode_right = None
                
            treeNode_left =  tree(left_pre ,left_tin)
            

            now_node = TreeNode(now)
            now_node.left  = treeNode_left
            now_node.right = treeNode_right

            return now_node

        # write code here
        # 根据前序，进行分割，左右两部分
        return tree(pre,tin)
```   
