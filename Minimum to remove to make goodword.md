# MEDIUM
PROBLEM NO. :3085

----

The question was first quite confusing for me 
it took some time to understand the question with the 
help of examples but then it was clear

---

The first approach i made was however not correct 
bcs i thought that they were talking about the sum
of other all digits rather than the individual differences

I'll paste the code for first approach which only passed the first case
but gave me and idea about my wrong approach..
currently traveling in train


---

This was the final solution though 
```python
class Solution:
    def minimumDeletions(self, word, k):
        # Initializing a frequency array for the 26 lowercase English letters
        freq = [0] * 26
        
        # Count the frequency of each character in the word
        for ch in word:
            freq[ord(ch) - ord('a')] += 1
        
        # Initialize the result to be the length of the word (worst case)
        result = len(word)
        
        # Iterate through all possible frequencies (for each character)
        for i in range(26):
            del_count = 0
            
            # Compare the frequency of character i with other characters
            for j in range(26):
                if i == j:
                    continue
                
                if freq[j] < freq[i]:
                    del_count += freq[j]
                elif abs(freq[j] - freq[i]) > k:
                    del_count += abs(freq[j] - freq[i] - k)
            
            # Update result with the minimum deletions found
            result = min(result, del_count)
        
        return result
```

This question refined some of my concepts including syntax errors too..
will correct them once i reach home
