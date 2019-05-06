剑指offer:删除链表中重复的节点

这道题的难度在于，链表的头节点的创建过程，以及整个的输出过程。

ListNode* deleteDuplication(ListNode* pHead)
    {
        map<int,int> m;
        ListNode* temp = pHead;
        
        while(pHead!=NULL)
        {
            if(m.find(pHead->val)!=m.end()){
                // 这就是一个n的平方的算法。
                m[pHead->val] +=1;
            }
            else{
                m[pHead->val]  =1;
            }
            pHead = pHead->next;
        }
        
        //
        ListNode zero_head = ListNode(0);
        ListNode* pre = &zero_head;        
        map<int,int>::iterator iter;
        while(temp!=NULL)
        {
            
                iter = m.find(temp->val);
                if(iter->second<2)
                {
                    pre->next = temp;
                    pre = pre->next;
                    
                }
                temp = temp->next;
        }
        pre->next = NULL;
        //
        return zero_head.next;
        
    }


