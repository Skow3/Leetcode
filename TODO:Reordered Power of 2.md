# MEDIUM
869

# WILL EXPLAIN IT SOON : [ WILL DO PROJECTS THIS WEEK ]

```PYTHON
class Solution:
    def getSortedStr(self, n):
        s = str(n)
        s_list = list(s)
        
        # doing manual sorting using bubble sort 
        for i in range(len(s_list)):
            for j in range(i + 1, len(s_list)):
                if s_list[i] > s_list[j]:
                    s_list[i], s_list[j] = s_list[j], s_list[i]
        
        return "".join(s_list)

    def reorderedPowerOf2(self, n):
        s = self.getSortedStr(n)

        # check all powers of 2 up to 2^29
        for p in range(30):
            power_of_two = 1 << p
            if s == self.getSortedStr(power_of_two):
                return True
        
        return False
```
