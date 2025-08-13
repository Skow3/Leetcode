# EASY 
141

Here we have to see wether the given linkedlist has cycle or not.
So imagining my old childhood days in park 
On the footpath in park if me[fast] and my friend[slow] had a continous race the track is same and has cycles than there is 100% possiblity that we'll meet again.
So using that :
```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def hasCycle(self, head):
        """
        :type head: ListNode
        :rtype: bool
        """
        slow = head
        fast = head
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next

            if slow == fast:
                return True
        return False
```


