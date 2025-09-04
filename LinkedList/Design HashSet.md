# EASY 
705

---

# First I went through the LL way of solving this :
But: right now, This MyHashSet is essentially just a linked list that supports add/remove/search in O(n) time. A true hash set usually uses hash buckets to get expected O(1) operations.
```python
class Node:
    def __init__(self, key):
        self.key = key
        self.next = None

class MyHashSet(object):

    def __init__(self):
        self.head = Node(-1)

    def add(self, key):
        """
        :type key: int
        :rtype: None
        """
        if not self.contains(key):
            newNode = Node(key)
            newNode.next = self.head.next
            self.head.next = newNode

    def remove(self, key):
        """
        :type key: int
        :rtype: None
        """
        prev,curr = self.head, self.head.next
        while curr:
            if curr.key ==key:
                prev.next = curr.next
                break
            curr= curr.next
            prev=prev.next

    def contains(self, key):
        """
        :type key: int
        :rtype: bool
        """
        curr = self.head.next
        while curr:
            if curr.key == key:
                return True
            curr= curr.next
        return False
        


# Your MyHashSet object will be instantiated and called as such:
# obj = MyHashSet()
# obj.add(key)
# obj.remove(key)
# param_3 = obj.contains(key)
```



But this only passed 26/33 test cases TLE
Because it was getting an O(n) time and i think they wanted Lesser.


# OPTIMISED VERSION
```python
class MyHashSet(object):

    def __init__(self):
        self.size = 1000  # number of buckets
        self.buckets = [[] for _ in range(self.size)]

    def _hash(self, key):
        return key % self.size

    def add(self, key):
        """
        :type key: int
        :rtype: None
        """
        bucket = self.buckets[self._hash(key)]
        if key not in bucket:
            bucket.append(key)

    def remove(self, key):
        """
        :type key: int
        :rtype: None
        """
        bucket = self.buckets[self._hash(key)]
        if key in bucket:
            bucket.remove(key)

    def contains(self, key):
        """
        :type key: int
        :rtype: bool
        """
        bucket = self.buckets[self._hash(key)]
        return key in bucket
```


# EXPLANATION [ GEMINI ] [ REAL-LIFE ]
This code implements a **hash set** data structure. A hash set is a collection of unique items that provides fast access, insertion, and deletion. The code works by using an array (or list in Python) of "buckets" and a hash function to determine which bucket a given key belongs to.

The code uses a technique called **separate chaining** to handle collisions, which occur when two different keys hash to the same bucket index. Instead of storing just one element per bucket, each bucket is a list that can hold multiple elements.

***

### 🏠 How it Works: A Library Analogy

Imagine you're managing a library with 1,000 shelves. You want to quickly find any book. Instead of a random mess, you organize books by their titles. Here's how this relates to the code:

* **`self.size` (1000 buckets):** This is your **1,000 shelves**. Each shelf is a bucket. 📚
* **`self.buckets` (the list of lists):** This is the **collection of all your shelves**. Each element in this list is another list, representing a single shelf that can hold many books.
* **`_hash(self, key)` (the hash function):** This is your **library's rule for where to put a book**. The rule is "take the book's title number and divide it by 1,000, then the remainder tells you the shelf number." For example, a book with the title number `1234` would go on shelf `1234 % 1000 = 234`.
* **`add(self, key)`:** When a new book arrives (`key`), you first apply your rule (`_hash`) to find the correct shelf (`bucket`). Then, you check if the book is already on that shelf (`if key not in bucket`). If it's not, you place it there (`bucket.append(key)`).
* **`remove(self, key)`:** To remove a book, you again use your rule (`_hash`) to find its shelf. Once you're on the right shelf, you look for the book (`if key in bucket`) and take it out (`bucket.remove(key)`).
* **`contains(self, key)`:** To check if a book is in the library, you follow the same process: use your rule (`_hash`) to find the shelf and then simply check if the book is on that shelf (`return key in bucket`).



This system is efficient because instead of searching through all 1,000 shelves, you only need to check one specific shelf, which will likely only contain a few books.
