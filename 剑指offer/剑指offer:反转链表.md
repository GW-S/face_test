剑指offer:反转链表


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
    
    ListNode* ReverseList(ListNode* pHead) {
        
        // 盛国威的魔法
        if(pHead==NULL)return pHead;
        if(pHead->next==NULL)return pHead;
        ListNode* pre;
        ListNode* now;
        ListNode* next;
        
        pre  = pHead;// 前一个
        now  = pHead->next;// 现在这个
        pre->next =NULL;
        
        while(now->next!=NULL)
        {
            next = now->next;
            now->next = pre;
            pre  = now;
            now  = next;
        }
        now->next = pre;
        return now;
    }
};
```

