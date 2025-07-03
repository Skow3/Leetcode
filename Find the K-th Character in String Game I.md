# EASY

* Was easy currently able to do the easy quesions in 5-20 mins [It should not be the subsequnce question]

  # SOLUTION
  ```python
  class Solution(object):
    def kthCharacter(self, k):
        """
        :type k: int
        :rtype: str
        """
        word = 'a'
        while len(word) < k:
            lis=''
            for i in word:
                lis+= chr(ord(i)+1)
            word+= lis
        print(word)
        return word[k-1]
  ```


  # THINGS REVISED:
  * I have earlier worked with obs() function but i somewhat not able to remember it.
  * A new function revised i.e chr() `to convert int to ASCII based character`.
 
* 
