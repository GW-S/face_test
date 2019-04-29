剑指offer:二叉搜索树转化为双向链表问题
class TreeNode:
    def __init__(self, x):
        self.val = x
        self.left = None
        self.right = None

def Convert(pRootOfTree):
        # write code here
            def trans(pRootOfTree):

        # 不可能出现当前为NULL
        # 当左右为空

                if (pRootOfTree.left == None and pRootOfTree.right == None):
                    head = pRootOfTree
                    return head, head

                if (pRootOfTree.left != None and pRootOfTree.right == None):
                    head_l, tail_l = trans(pRootOfTree.left)
                    tail_l.right = pRootOfTree
                    pRootOfTree.left = tail_l
                    return head_l, pRootOfTree

                if (pRootOfTree.left == None and pRootOfTree.right != None):
                    head_r, tail_r = trans(pRootOfTree.right)
                    pRootOfTree.right = head_r
                    head_r.left = pRootOfTree

                    return pRootOfTree, tail_r

                if (pRootOfTree.left != None and pRootOfTree.right != None):
                    head_l, tail_l = trans(pRootOfTree.left)
                    head_r, tail_r = trans(pRootOfTree.right)

                    tail_l.right = pRootOfTree
                    pRootOfTree.right = head_r
                    pRootOfTree.left = tail_l
                    head_r.left = pRootOfTree
                    return head_l, tail_r

            if pRootOfTree == None:
                return pRootOfTree
            head,tail = trans(pRootOfTree)
            return head

test = [1,2,3,4,5,6,7,8,9]

#       5
#    4      7
#   2       6   8
pRootOfTree = TreeNode(5)
pRootOfTree.left  = TreeNode(4)
pRootOfTree.right = TreeNode(7)
pRootOfTree.left.left = TreeNode(2)
pRootOfTree.right.left = TreeNode(6)
pRootOfTree.right.right= TreeNode(8)

head = Convert(pRootOfTree)

while(head.right!=None):
    print(head.val)
    head = head.right

