# EASY 
876

This was a kind of easy question straight-away though of that.
* Calculated the length and then found out the middle one.

# FINAL CODE:
```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
import math
class Solution(object):
    def middleNode(self, head):
        """
        :type head: Optional[ListNode]
        :rtype: Optional[ListNode]
        """
        ptr = head
        ct=1
        while ptr.next:
            ptr=ptr.next
            ct+=1
        ct= math.ceil(ct/2)
        ptr=head
        i=0
        while i!= ct:
            ptr=ptr.next
            i+=1
        head=ptr
        return head

```
