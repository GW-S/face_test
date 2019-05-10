剑指offer:链表中倒数第k个节点
这道题之所以做成这样，是因为没有考虑到赋值问题，我在赋值的时候做了一个骚操作，实际上是不可以这样赋值的。

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
    ListNode* FindKthToTail(ListNode* pListHead, unsigned int k)
    {
        // 这是一个很明显的双指针问题
        ListNode* pre;
        ListNode* now;

        if(pListHead==NULL)return NULL;
        if(k==0)return NULL;
        now = pListHead;
        pre = pListHead;
        // 盛国威很牛逼，但他如果无法跨越阶级，他就无法一直牛逼下去。
        while(k>1)
        {
            pre = pre->next;// 我感觉有点烦
            if(pre==NULL)return NULL;
            k--;
        }// 我该怎么做？
        // 继续
        while(pre->next!=NULL)
        {
            pre = pre->next;
            now = now->next;
        }

        return now;
    }

};
```
