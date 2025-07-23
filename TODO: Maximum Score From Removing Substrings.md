# MEDIUM 
1717

---

# SOLUTION
```cpp
class Solution {
public:
    int maximumGain(string s, int x, int y) {
        int n     = s.length();
        int score = 0;

        string maxStr = (x > y) ? "ab" : "ba";
        string minStr = (maxStr == "ab") ? "ba" : "ab"; //This is updated after the video was made as a new test case was added in Leetcode

        //First Pass
        string temp_first     = removeSubstring(s, maxStr);
        int L                 = temp_first.length();
        int removedPairsCount = (n - L) / 2;
        score                += removedPairsCount * max(x, y);


        //Second Pass
        string temp_second = removeSubstring(temp_first, minStr);
        removedPairsCount  = (L - temp_second.length()) / 2;
        score             += removedPairsCount * min(x, y);

        return score;
    }

    string removeSubstring(string& inputString, string& matchStr) {
        int j = 0;

        for (int i = 0; i < inputString.size(); i++) {
            inputString[j++] = inputString[i];

            if (j > 1 &&
                inputString[j - 2] == matchStr[0] &&
                inputString[j - 1] == matchStr[1]) {
                j -= 2;
            }
        }

        inputString.erase(inputString.begin() + j, inputString.end());

        return inputString;
    }
};
```


---

# PYTHON 

```python
class Solution:
    def maximumGain(self, s: str, x: int, y: int) -> int:
        def remove_substring(s: str, match: str) -> (str, int):
            stack = []
            count = 0
            for ch in s:
                stack.append(ch)
                if len(stack) >= 2 and stack[-2] == match[0] and stack[-1] == match[1]:
                    stack.pop()
                    stack.pop()
                    count += 1
            return "".join(stack), count

        maxStr = "ab" if x > y else "ba"
        minStr = "ba" if maxStr == "ab" else "ab"

        # First pass - remove more valuable pairs first
        temp, max_count = remove_substring(s, maxStr)

        # Second pass - remove the other pair
        temp, min_count = remove_substring(temp, minStr)

        return max_count * max(x, y) + min_count * min(x, y)
```
