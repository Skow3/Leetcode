# NEW CONCEPT
PYTHON
EASY

---

```python
class Solution(object):
    def addBinary(self, a, b):
        """
        :type a: str
        :type b: str
        :rtype: str
        """
        return bin(int(a,2) + int(b,2))[2:]
```

here bin is used to convert a number [ integer ] into binary number string
Since it is in the form of 0b<binary> So i just sliced it from 2nd index of the string 

---
# New Concepts :
bin function

#### revised concepts:
Slicing 
Converting Binary number string to Decimal using int(variable,2)

##
