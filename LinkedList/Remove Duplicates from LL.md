# MEDIUM
82

* The question was again easy-med if someone has concepts of traversing LL.
* I fumbled for some test cases in the start like if head is [] or if head has only repeating digits.
* Solved those and done

# FINAL CODE:
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
        freq = {}
        if not head:
            return None
        while head:
            if head.val not in freq:
                freq[head.val] = 1
                head = head.next
                continue
            freq[head.val] += 1
            head = head.next
        ok = []
        kp = False
        for i in freq:
            if freq[i] <2 :
                kp = True
                ok.append(i)
        if not kp:
            return None
        ok.sort()
        head = ListNode(ok[0])
        ptr = head
        for i in range(1,len(ok)):
            ptr.next = ListNode(ok[i])
            ptr = ptr.next
        ptr.next = None
        return head

```
