# EASY 
160
Finding the intersection of Two LL

# First Code:
```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def getIntersectionNode(self, headA, headB):
        """
        :type head1, head1: ListNode
        :rtype: ListNode
        """
        lentA=1
        lentB=1
        ptrA = headA
        ptrB = headB
        while ptrA.next:
            ptrA = ptrA.next
            lentA+=1
        while ptrB.next:
            ptrB = ptrB.next
            lentB+=1
        if lentA > lentB:
            newA = lentA-lentB
            while headA.next and newA!=0:
                headA=headA.next
                newA-=1
        if lentB>lentA:
            newB = lentB-lentA
            while headB.next and newB!=0:
                headB=headB.next
                newB-=1
        while headA.next:
            while headB.next:
                if headB.next== headA.next:
                    value = headB.next.val                        
                    return headB.next
                headB=headB.next
            headA=headA.next
        return None

```


# 2ND CODE
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None


class Solution(object):
    def getIntersectionNode(self, headA, headB):
        """
        :type headA: ListNode
        :type headB: ListNode
        :rtype: ListNode
        """
        if not headA or not headB:
            return None

        lentA = 0
        lentB = 0
        ptrA = headA
        ptrB = headB

        # compute lengths
        while ptrA:
            lentA += 1
            ptrA = ptrA.next
        while ptrB:
            lentB += 1
            ptrB = ptrB.next

        # align starts
        if lentA > lentB:
            newA = lentA - lentB
            while headA and newA:
                headA = headA.next
                newA -= 1
        elif lentB > lentA:
            newB = lentB - lentA
            while headB and newB:
                headB = headB.next
                newB -= 1

        # move together to find intersection
        while headA and headB:
            if headA is headB:
                return headA
            headA = headA.next
            headB = headB.next

        return None
```




# MORE OPTIMIZED CODE
```PYTHON
class Solution(object):
    def getIntersectionNode(self, headA, headB):
        """
        :type headA: ListNode
        :type headB: ListNode
        :rtype: ListNode
        """
        if not headA or not headB:
            return None

        pa, pb = headA, headB
        while pa is not pb:
            pa = pa.next if pa else headB
            pb = pb.next if pb else headA

        return pa  # Intersection node or None
```
