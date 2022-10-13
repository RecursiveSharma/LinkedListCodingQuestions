### [Back2Home](https://github.com/RecursiveSharma/ArraysCodingQuestions/main/README.md) | [Go2Video](#)


```c++
//  Time complexity = O(n) = But destroying the linked list = Dummy Node SOLUTION 1
//---------------------------------C++ SOLUTION
bool isLoop(Node* head) 
{   Node* temp=new Node(0);
    Node *curr=head;
    while (curr != NULL) {  
        if (curr->next==NULL)
            return false;
        if(curr->next==temp)
            return true;
      //saving currNode next
      Node *curr_next=curr->next;
      //poiting next to the dummy node
        curr->next=temp;
      //replacing next of currNode
        curr=curr_next;
    } 
    return false;
}

----------------------------------
  
//-------------------------------- JAVA SOLUTION
  static boolean isLoop(Node head) 
    {   Node temp=new Node(0);
        Node curr=head;
        while (curr != null) {  
            if (curr.next==null)
                return false;
            if(curr.next==temp)
                return true;
            Node curr_next=curr.next;
            curr.next=temp;
            curr=curr_next;
        } 
        return false; 
    }


```

```java
//  Time complexity & Space Complexity = O(n) = Without destroying the linked list = Using SETS SOLUTION 2
//---------------------------------C++ SOLUTION
bool isLoop(Node* head) 
{ 
    unordered_set<Node*> s; 
    for(Node *curr=head;curr!=NULL;curr=curr->next) {  
        if (s.find(curr) != s.end()) 
            return true; 
        s.insert(curr); 
    } 
    return false; 
}


//---------------------------------jAVA SOLUTION
static boolean isLoop(Node head) 
    {   HashSet<Node> s=new HashSet<Node>(); 
        for(Node curr=head;curr!=null;curr=curr.next) {  
            if (s.contains(curr)) 
                return true; 
            s.add(curr); 
        } 
        return false;  
    }

```


```java
//  Time complexity = O(n) = Without destroying the linked list = Using Floyd's Cycle Method -> SOLUTION 3 = BEST SOLUTION
//---------------------------------C++ SOLUTION
bool isLoop(Node* head) 
{ 
    Node *slow_p = head, *fast_p = head; 
  
    while (fast_p!=NULL && fast_p->next!=NULL) { 
        slow_p = slow_p->next; 
        fast_p = fast_p->next->next; 
        if (slow_p == fast_p) { 
            return true; 
        } 
    } 
    return false; 
}


//---------------------------------jAVA SOLUTION
 static boolean isLoop(Node head) 
    {   Node slow_p = head,fast_p = head; 
      
        while (fast_p!=null && fast_p.next!=null) { 
            slow_p = slow_p.next; 
            fast_p = fast_p.next.next; 
            if (slow_p == fast_p) { 
                return true; 
            } 
        } 
        return false;   
    }
    
```
