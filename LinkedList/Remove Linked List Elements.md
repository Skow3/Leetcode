# EASY 
203
* Took all the cases and solved it

# FINAL CODE
```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def removeElements(self, head, val):
        """
        :type head: Optional[ListNode]
        :type val: int
        :rtype: Optional[ListNode]
        """
        if not head or not head.next and head.val == val:
            return None
        if head.next and head.val == val:
            while head and head.val==val:
                if head.next:
                    head = head.next
                else:
                    return None
        ptr=head
        while ptr and ptr.next:
            if ptr.next.val == val:
                if ptr.next:
                    srt = ptr.next
                    while srt and srt.val == val:
                        if srt.next:                        
                            srt = srt.next
                        else:
                            srt = None
                    ptr.next =srt
                else:
                    ptr.next = None
            ptr = ptr.next
        return head

```
