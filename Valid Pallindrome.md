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


# LOOKING AT SOME MORE OPTIMIZED VERSIONS ON LEETCODE:
```python
class Solution:
    def isPalindrome(self, s):
        left, right = 0, len(s) - 1
## CHECKING THE OUPUT 
        while left < right:
            while left < right and not s[left].isalnum():
                left += 1
            while left < right and not s[right].isalnum():
                right -= 1

            if s[left].lower() != s[right].lower():
                return False

            left += 1
            right -= 1

        return True
```

Let's try to understand:
So let's see what is this str.isalnum() function
```text
Help on method_descriptor:

isalnum(self, /) unbound builtins.str method
    Return True if the string is an alpha-numeric string, False otherwise.

    A string is alpha-numeric if all characters in the string are alpha-numeric and
    there is at least one character in the string.
```

So here if the s[index] is space/punctuation marks then we are increasing the status until a character is reached.
