# MEDIUM
3217

```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next


class Solution:
    def modifiedList(self, nums, head):
        st = set(nums)
        curr = head

        # Remove leading nodes that are in the set
        while curr and curr.val in st:
            head = curr.next
            curr = head

        prev = None
        curr = head

        # Traverse the list and remove nodes whose value is in the set
        while curr:
            if curr.val not in st:
                prev = curr
                curr = curr.next
            else:
                prev.next = curr.next
                curr = curr.next

        return head

```
