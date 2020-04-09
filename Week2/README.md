# Week 2

### 8) Middle of the Linked List
Given a non-empty, singly linked list with head node head, return a middle node of linked list.

If there are two middle nodes, return the second middle node.
ex1)
```
Input: [1,2,3,4,5]
Output: Node 3 from this list (Serialization: [3,4,5])
The returned node has value 3.  (The judge's serialization of this node is [3,4,5]).
Note that we returned a ListNode object ans, such that:
ans.val = 3, ans.next.val = 4, ans.next.next.val = 5, and ans.next.next.next = NULL.
```

ex2)
```
Input: [1,2,3,4,5,6]
Output: Node 4 from this list (Serialization: [4,5,6])
Since the list has two middle nodes with values 3 and 4, we return the second one.
```

solution)
```
var middleNode = function(head) {
    var length = 1;
    var index = null;
    var cur = head;
    while (cur.next){
        cur = cur.next;
        length++;
    }
    index = Math.floor(length/2);
    for (i=0; i<index; i++){
        head = head.next;
    }
    return head;
};
```