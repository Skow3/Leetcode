# MEDIUM
24

* The question was nice.
* Was going on the right solution but missed one corner case touch.
* I.e i was not able to solve the indexing issue at last in 15 mins.

```PYTHON
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def swapPairs(self, head):
        """
        :type head: Optional[ListNode]
        :rtype: Optional[ListNode]
        """
        ptr1=head
        if not head or not head.next:
            return head
        ptr2=ptr1.next
        head = ptr2
        while ptr1 and ptr1.next and ptr1.next.next:
            ptr1.next=ptr2.next
            ptr2.next=ptr1
            st = ptr1
            ptr1=ptr1.next
            ptr2=ptr1.next
            st.next = ptr2
        return head
```

This was my first code ... the logic i built was correct but there was just one thing which was making it not work perfectly.

So now instead of just setting ptr2 = ptr1.next i.e the second node we will start and make it easier bu assuming and attaching a demo node to the head.

# FINAL CODE
```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

class Solution(object):
    def swapPairs(self, head):
        """
        :type head: Optional[ListNode]
        :rtype: Optional[ListNode]
        """
        if not head or not head.next:
            return head
        dummy = ListNode(0)
        dummy.next = head
        prev = dummy
        ptr1 = head
        
        while ptr1 and ptr1.next:
            ptr2 = ptr1.next
            prev.next = ptr2
            ptr1.next = ptr2.next
            ptr2.next = ptr1
            prev = ptr1
            ptr1 = ptr1.next
        
        return dummy.next
```

#DONE
