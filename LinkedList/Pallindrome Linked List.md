# EASY
234

---

The first approach got my mind as i saw the word pallindrome.
So i made the approach using Slicing operator[::]

# FIRST APPROACH
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def isPalindrome(self, head: Optional[ListNode]) -> bool:
        if not head:
            return False
        if not head.next:
            return True
        sto=f"{head.val}"
        while head.next:
            head=head.next
            sto+= f"{head.val}"
        if sto == sto[::-1]:
            return True
        return False
```




* AS I learnt last semester while playing with DFA-NFA And different turing machines

For Pallindrome we can use a Stack
```python
class Solution:
    def isPalindrome(self, head: Optional[ListNode]) -> bool:
        list_vals = []
        stack = []
        curr = head
        while curr:
            stack.append(curr.val)
            curr = curr.next
        curr = head
        while curr and curr.val == stack.pop():
            curr = curr.next
        return curr is None
```
