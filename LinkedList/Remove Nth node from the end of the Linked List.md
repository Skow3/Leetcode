# MEDIUM
19

I'll mark the question from easy if a person has solved the other easy level questions before solving this:

Just have to handle some different cases and we're done:
TWO CASES WERE THERE:
1. n is such that it is last
2. n is such that it points to the first element

# FINAL CODE:
```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def removeNthFromEnd(self, head, n):
        """
        :type head: Optional[ListNode]
        :type n: int
        :rtype: Optional[ListNode]
        """
        if not head.next and n==1:
            return None
        ptr=head
        lt=0
        while ptr:
            ptr=ptr.next
            lt+=1
        n = lt-n-1
        if n<0:
            head=head.next
            return head
        lt=0
        ptr=head
        while ptr and lt!=n:
            ptr=ptr.next
            lt+=1
        if ptr:
            ptr.next=ptr.next.next
        return head
```
