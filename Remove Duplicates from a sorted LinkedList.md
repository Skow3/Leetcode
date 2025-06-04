# Easy

## NEW CONCEPTS:
* How to iterate in linkedlist in python
* How it works
* How to check null for linkedlist

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def deleteDuplicates(self, head):
        """
        :type head: Optional[ListNode]
        :rtype: Optional[ListNode]
        """
        if not head:
            return None
        
        current = head
        while current and current.next:
            if current.val == current.next.val:
                # Skip the next node since it's a duplicate
                current.next = current.next.next
            else:
                # Move to the next node
                current = current.next
        
        return head
```

