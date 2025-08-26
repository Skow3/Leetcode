# MEDIUM
6

* The question was nice and it just needed to identify the pattern.

## PATTERN
See for a value of k ...let's the length of the linkedlist was 5[We'll calculate the length]
Now we can see if :
K= 0 - 5 - 10 - 15 .....etc i.e k%5 == 0 
  then for each value the answer will be the Original linked list

Other than this in all the answers the thing which we require is only the Last node to point to the first node and then pointing some middle node to None.
For k= 1 - 6 - 11 - 16 .... etc i.e k%5 == 1
  then for each value the answer will be achieved by pointing the 5 - k%5 Node towards Null 

  and soo on..


# FINAL CODE:
```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def rotateRight(self, head, k):
        """
        :type head: Optional[ListNode]
        :type k: int
        :rtype: Optional[ListNode]
        """
        # Calculating length first:
        ptr=head
        lt=1
        while ptr and ptr.next:
            lt+=1
            ptr=ptr.next
        print(lt)
        if k%lt == 0:
            return head
        ptr.next = head
        o = lt- k%lt
        print(o)
        ptr = head
        for i in range(o-1):
            ptr= ptr.next
        qt= ptr
        ptr= ptr.next
        qt.next = None
        head = ptr
        return head

