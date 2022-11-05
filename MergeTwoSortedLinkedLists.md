### Best Solution -> 6 Lines of CODE || Recursive Approach
```Java
public ListNode mergeTwoLists(ListNode l1, ListNode l2){
		if(l1 == null) return l2;
		if(l2 == null) return l1;
		if(l1.val < l2.val){
			l1.next = mergeTwoLists(l1.next, l2);
			return l1;
		} else{
			l2.next = mergeTwoLists(l1, l2.next);
			return l2;
		}
}
```
	// 😉If you Like the repository don't foget to star & fork the repository😉
### Java Solution without Dummy Node || ITERATIVE APPROACH
TC = O (n+m) and SC = O(1)
```java
    public ListNode mergeTwoLists(ListNode a, ListNode b) {
      //if one of the linked list is empty  (Corner Caese)
        if(a==null)return b;
        if(b==null)return a;
      
      //if both list are not null
        ListNode head=null,tail=null;
        if(a.val<=b.val){
            head=tail=a;a=a.next;
        }
        else{
            head=tail=b;b=b.next;
        }
        while(a!=null&&b!=null){
            if(a.val<=b.val){
                tail.next=a;tail=a;a=a.next;
            }
            else{
                tail.next=b;tail=b;b=b.next;
            }
        }

      //if any list having elements after merging
        if(a==null) tail.next=b;
        else tail.next=a;
       
      //return the head of the merge list
        return head;
    }
   
```

### C++ Solution without Dummy Node || ITERATIVE APPROACH
TC = O (n+m) and SC = O(1)
```C
 ListNode* mergeTwoLists(ListNode* a, ListNode* b) {
    if(a==NULL)return b;
    if(b==NULL)return a;
    ListNode *head=NULL,*tail=NULL;
    if(a->val<=b->val){
        head=tail=a;a=a->next;
    }
    else{
        head=tail=b;b=b->next;
    }
    while(a!=NULL&&b!=NULL){
        if(a->val<=b->val){
            tail->next=a;tail=a;a=a->next;
        }
        else{
            tail->next=b;tail=b;b=b->next;
        }
    }
    if(a==NULL){tail->next=b;}
    else{
        tail->next=a;
    }
    return head;
}
```
