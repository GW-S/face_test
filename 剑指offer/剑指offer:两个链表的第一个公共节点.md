剑指offer:两个链表的第一个公共节点

```C++
/*
struct ListNode {
	int val;
	struct ListNode *next;
	ListNode(int x) :
			val(x), next(NULL) {
	}
};*/
class Solution {
public:
    ListNode* FindFirstCommonNode( ListNode* pHead1, ListNode* pHead2) {
        // 找出第一个公共结点
        // 两者都反转，找结点
        // 记录两个链表
        if(pHead1==NULL)return NULL;
        if(pHead2==NULL)return NULL;
        
        map<ListNode*,int> m;
        
        ListNode* point1;
        ListNode* point2;
        
        point1 = pHead1;
        point2 = pHead2;
        
        while(point1!=NULL)
        {
            if(m.find(point1)== m.end())
            {
                m[point1] = 1;
            }
            point1 = point1->next;
        }
              
        while(point2!=NULL)
        {
            if(m.find(point2)!=m.end())
            {
                return point2;
            }
            point2 = point2->next;
        }
        return NULL;
}
};
```

