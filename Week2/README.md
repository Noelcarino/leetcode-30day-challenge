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

### 9) Backspace String Compare

Given two strings S and T, return if they are equal when both are typed into empty text editors. # means a backspace character.

ex1)
```
Input: S = "ab#c", T = "ad#c"
Output: true
Explanation: Both S and T become "ac".
```

ex2)
```
Input: S = "ab##", T = "c#d#"
Output: true
Explanation: Both S and T become "".
```

ex3)
```
Input: S = "a##c", T = "#a#c"
Output: true
Explanation: Both S and T become "c".
```

ex4)
```
Input: S = "a#c", T = "b"
Output: false
Explanation: S becomes "c" while T becomes "b".
```

solution)
```
function backspaceCompare(a,b){
  // base case
  if (!a.includes("#") && !b.includes("#")){
    if (a === b) return true;
    else return false;
  }
  
  let arrA = a.split('');
  let arrB = b.split('');
  
  let r1 = [];
  let r2 = [];
  for (var i = 0; i < arrA.length; i++) {
    if (arrA[i] !== "#") r1.push(arrA[i]);
    if (arrA[i] === "#") r1.pop(r1[r1.length-1]);
  }
  for (var j = 0; j < arrB.length; j++){
    if (arrB[j] !== "#") r2.push(arrB[j]);
    if (arrB[j] === "#") r2.pop(r2[r2.length-1])
  } 
  
  return r1.join('') === r2.join('');
}
```