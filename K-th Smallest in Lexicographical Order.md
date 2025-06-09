# HARD QUESTION 
##### 440

Solution 1 : Using simple array allocation and string conversion
```python
class Solution(object):
    def findKthNumber(self, n, k):
        """
        :type n: int
        :type k: int
        :rtype: int
        """
        s = []
        for i in range(n):
            s.append(i+1)
        for i in range(n):
            s[i] = str(s[i])
        s = sorted(s)
        for i in range(n):
            s[i] = int(s[i])
        
        return s[k-1]
```

But here the constraints are very large i.e 10<sup>9</sup>

Here we will visualize the code as in a tree format of these numbers 
![image](https://github.com/user-attachments/assets/e82bd70f-bf65-4941-b339-edb63dbffc04)
Now here as we can see in this tree that the count of the numbers which starts with 1 is in the subtree of 1 and similarly for 2 and so on...

In each level for each tree the number of nodes is equal to the leftmost node of parent tree - leftmost node of left parent tree
for example in level 1 :  2-1 = 1 node
               level 2 :  20-10 = 10 node

### WHAT WAS NOT GOOD IN THE ABOVE SOLUTIONS AND WHAT FIXES CAN BE DONE

In the above solution because of the High Constraints i.e 10<sup>9</sup> we can't even have simple search and return or storing it in an array and then simply returning
that index element

So now the questioner wants us to do make some changes like :
1. If we can find out some pattern to skip numbers while checking
2. If we can reduce the TIME COMPLEXITY < O(n)

So let's go for it

```cpp
class Solution {
public:

    int Count(long curr, long next, int n) {
        int countNum = 0;

        while(curr <= n) {
            countNum += (next - curr);

            curr *= 10;
            next *= 10;

            next = min(next, long(n+1));
        }

        return countNum;
    }

    int findKthNumber(int n, int k) {
        int curr = 1;
        k -= 1; //Since we start from the first number (1), we need k-1 more numbers

        while(k > 0) {
            int count = Count(curr, curr+1, n);
            if(count  <= k) {
                curr++;
                k -= count; //skipping the elements under curr prefix tree
            } else {
                curr *= 10;
                k -= 1;
            }
        }

        return curr;

    }
};
```

Now my python solution :
```python
class Solution(object):
    def countt(self, curr, nextt, n): # counts the number of digits in the subtree of the curr node [TRAVERSES UNTIL curr <=n]
        countn = 0
        while curr <= n:
            countn += min(n + 1, nextt) - curr
            curr *= 10
            nextt *= 10
        return countn

    def findKthNumber(self, n, k):  ## Original function
        curr = 1
        k -= 1  # Decreased k by one bcs we have counted 1 
        while k > 0:
            count = self.countt(curr, curr + 1, n)
            if count <= k:
                curr += 1
                k -= count
            else:
                curr *= 10
                k -= 1
        return curr
```



---

# NEW THINGS LEARNT 
1. Always try to make problem simpler and simpler not just go with quick one-go answers.
2. Try to improve thinking process
3. How to call another function in class [revised] don't forget to use self in the function.

---

Thanks 
