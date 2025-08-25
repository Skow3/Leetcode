# MEDIUM
2

It was easy-medium question just we needed some knowledge of handling digits.
# FIRST DRAFT :
```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: Optional[ListNode]
        :type l2: Optional[ListNode]
        :rtype: Optional[ListNode]
        """
        # ADDING THE NUMBERS
        ptr1= l1
        ptr2= l2
        num1= 0
        num2 =0
        f = True
        i=1
        while ptr1:
            num1+= ptr1.val*i
            ptr1= ptr1.next
            i*=10
        i=1
        while ptr2:
            num2+= ptr2.val*i
            ptr2= ptr2.next
            i*=10
        num1 = num1+num2
        head= ListNode(num1%10)
        num1//= 10
        ptr = head
        while num1!=0:
            ptr.next = ListNode(num1%10)
            num1//= 10
        ptr.next = None
        return head
```




# FINAL CODE:
```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: Optional[ListNode]
        :type l2: Optional[ListNode]
        :rtype: Optional[ListNode]
        """
        ptr1, ptr2 = l1, l2
        num1, num2 = 0, 0
        i = 1
        while ptr1:
            num1 += ptr1.val * i
            ptr1 = ptr1.next
            i *= 10
        i = 1
        while ptr2:
            num2 += ptr2.val * i
            ptr2 = ptr2.next
            i *= 10

        # Add numbers
        total = num1 + num2

        # Convert back to linked list
        head = ListNode(total % 10)
        total //= 10
        ptr = head

        while total != 0:
            ptr.next = ListNode(total % 10)
            ptr = ptr.next
            total //= 10

        return head
```

