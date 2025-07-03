# EASY 

Cleaning a string and then checking for pallindrome.

---

* I was trying to figure it out that how many different ways or functions i can use to clear up the punctuation marks from the sentence.
### THEY ARE:

1. Using replace() function
```python
sentence = "Hello, world! How are you?"
# List of punctuation and space to remove
to_remove = [' ', '!', ',', '.', '?']
for ch in to_remove:
    sentence = sentence.replace(ch, '')
print(sentence)  # Output: HelloworldHowareyou
```

2. Using re [regex]  library:
```python
import re
sentence = "Hello, world! How are you?"
result = re.sub(r"[^\w]", "", sentence)
print(result)  # Output: HelloworldHowareyou
```

3. Using string.punctuation library:
```python
import string
sentence = "Hello, world! How are you?"
result = ''.join([ch for ch in sentence if ch not in string.punctuation and ch != ' '])
print(result)  # Output: HelloworldHowareyou
```

4. Without using any functions:
```python
sentence = "Hello, world! How are you?"
punctuation = "!\"#$%&'()*+,-./:;<=>?@[\\]^_`{|}~"
result = ""

for ch in sentence:
    if ch not in punctuation and ch != " ":
        result += ch

print(result)  # Output: HelloworldHowareyou
```
---

I used the 4th one ... so 
After that we already know how to check the pallindrome [::]

# SOLUTION
```PYTHON
class Solution(object):
    def isPalindrome(self, s):
        """
        :type s: str
        :rtype: bool
        """
        punctuation = "!\"#$%&'()*+,-./:;<=>?@[\\]^_`{|}~"
        ## Getting the string without punctuation
        result = ""
        for ch in s:
            if ch not in punctuation and ch != " ":
                result += ch
        # Check the pallindrome
        result = result.lower()
        return result == result[::-1]
```
