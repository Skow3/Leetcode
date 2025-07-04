# HARD
The questioned seemed easy to me as i did some same kind  [PART 1]  yesterday 

---

### TOPICS :
1. Recursion
2. Char to int
3. int to Char

---

So ,
* Now i started solving the question with the same logic but with some conditions... I didn't saw the constraints at first 
* Yes , Ik that was a huge mistake.
* As the value of k was < 10<sup>14</sup>

and because of that thing my TOC WAS 2<sup>n</sup>

# FIRST APPROACH [721/900 CASES]
```PYTHON
class Solution(object):
    def kthCharacter(self, k, operations):
        """
        :type k: int
        :type operations: List[int]
        :rtype: str
        """
        word = "a"
        count = 0
        while count < len(operations):
            if operations[count] == 0:
                word+=word
            else:
                res = ''
                for i in word:
                    res+= chr(ord(i)+1)
                word+=res
            count+=1
        return word[k-1]
```

Then i thought at first that the maximum time is being used for the searching of kth index so later on i came on this solution

```python
class Solution(object):
    def kthCharacter(self, k, operations):
        """
        :type k: int
        :type operations: List[int]
        :rtype: str
        """
        word = "a"
        count = 0
        pot = k -pow(2,len(operations)-1)-1
        while count < len(operations):
            if operations[count] == 0:
                word+=word
                if count == len(operations)-1:
                    return(word[pot])
            else:
                res = ''
                for i in word:
                    res+= chr(ord(i)+1)
                word+=res
                if count == len(operations)-1:
                    return (res[pot])
            count+=1
```


---

After trying several more things and trying to try doing it reversaly still i was not able to figure out.
Then i went for the recursion method

And this is the final Solution

---

# FINAL SOLUTION
```python
class Solution:
    def kthCharacter(self, k, operations):
        """
        :type k: int
        :type operations: List[int]
        :rtype: str
        """

        # Base case
        if k == 1:
            return 'a'

        n = len(operations)
        length = 1

        for i in range(n):
            length *= 2
            if length >= k:
                op_type = operations[i]
                new_k = k - length // 2
                break

        # Recursive call
        res = self.kthCharacter(new_k, operations[:i])  # pass only operations up to i

        if op_type == 0:
            return res
        else:
            if res == 'z':
                return 'a'
            return chr(ord(res) + 1)
```


---

RECURSION IS NOT ALWAYS BAD



