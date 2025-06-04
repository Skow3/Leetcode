# MEDIUM
PYTHON

```python
class Solution(object):
    def answerString(self, word, numFriends):
        """
        :type word: str
        :type numFriends: int
        :rtype: str
        """
        v= len(word) - numFriends + 1 # isse jyda nhi ho payga answer ka length
        largest =""
        if numFriends == 1: # for handling the 1 entries 
            return word
        for i in range(0,len(word)):
                    e = word[i:min(i+v,len(word))]  # using the slice operator for slicing and getting the words
                    if e > largest:
                        largest =e
        return largest
```
