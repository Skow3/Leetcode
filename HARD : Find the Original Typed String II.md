# HARD
This question was on tougher side for me.

Though today i was not able to give it a lot of time bcs of some work but got nothing

* I was trying to find out a nice solution rather than just going through it.
* Also the recursion method came in my mind but yet i didn't implemented because i'm not currently able to code recursions. Will work on that

* After recursion i went to get a clean understanding of the solution.
* Where i got this Bottom-up approach

```cpp
class Solution {
public:
    int M = 1e9+7;

    int possibleStringCount(string word, int k) {
        if(k > word.length())
            return 0;
        
        vector<int> freq;
        int count = 1;
        for(int i = 1; i < word.length(); i++) {
            if(word[i] == word[i-1]) {
                count++;
            } else {
                freq.push_back(count);
                count = 1;
            }
        }
        freq.push_back(count);

        long long P = 1; //total possible strings
        for(int &f : freq) {
            P = (P * f) % M;
        }
        
        if(freq.size() >= k) {
            return P;
        }
        int n = freq.size();
        
        vector<vector<int>> t(n+1, vector<int>(k+1, 0));

        for(int count = k-1; count >= 0; count--) {
            t[n][count] = 1;
        }

        for(int i = n-1; i >= 0; i--) {

            vector<int> prefix(k+1, 0);
            for(int h = 1; h <= k; h++) {
                prefix[h] = (prefix[h-1] + t[i+1][h-1]) % M;
            }

            for(int count = k-1; count >= 0; count--) {
                
                int l = count + 1;
                int r = count + freq[i];

                if(r+1 > k) {
                    r = k-1;
                }

                if(l <= r) {
                    t[i][count] = (prefix[r+1] - prefix[l] + M) % M;
                }
                
            }
        }

        long long invalidCount = t[0][0];

        return (P - invalidCount + M) % M;
    }
};
```

# FIRST SOLUTION
```python
class Solution(object):
    def possibleStringCount(self, word, k):
        """
        :type word: str
        :type k: intclass Solution(object):
        """
        M = int(1e9 + 7)
        freq = []
        count = 1  # initialize with 1 for the first character

        for i in range(1, len(word)):
            if word[i - 1] == word[i]:
                count += 1
            else:
                freq.append(count)
                count = 1
        freq.append(count)  # append the last group count

        P = 1
        for i in freq:
            P = (P * i) % M  # take mod M to avoid overflow

        n = len(freq)
        if n >= k:
            return P

        # Initialize the 2D DP table
        t = [[0] * (k + 1) for _ in range(n + 1)]

        # Base case
        for count in range(k - 1, -1, -1):
            t[n][count] = 1

        # DP filling
        for i in range(n - 1, -1, -1):
            prefix = [0] * (k + 2)  # k+2 to safely access prefix[r+1]
            for h in range(1, k + 1):
                prefix[h] = (prefix[h - 1] + t[i + 1][h - 1]) % M

            for count in range(k - 1, -1, -1):
                l = count + 1
                r = count + freq[i]

                if r + 1 > k:
                    r = k - 1

                if l <= r:
                    t[i][count] = (prefix[r + 1] - prefix[l] + M) % M

        invalid_count = t[0][0]

        return (P - invalid_count + M) % M
```


---

# MORE OPTIMISED VERSION USING THE GIVEN MAX LENGTH
```python
class Solution(object):
    def possibleStringCount(self, word, k):
        """
        :type word: str
        :type k: int
        :rtype: int
        """
        mod = int(1e9 + 7)
        n = len(word)

        if n < k:
            return 0
        if n == k:
            return 1

        # Segmentation of consecutive same letters
        seg = [1]
        for i in range(1, n):
            if word[i] == word[i - 1]:
                seg[-1] += 1
            else:
                seg.append(1)
        m = len(seg)

        total = 1
        takeMod = False
        for x in seg:
            total *= x
            if total >= mod:
                total %= mod
                takeMod = True

        if total == 1 and not takeMod:
            return 1

        if k <= m:
            return total

        # Since the maximum length we're given to be 2000
        max_size = 2000
        dp = [[0] * max_size for _ in range(2)]
        prefix = [0] * (max_size + 1)

        maxT = k - m - 1
        dp[0][0] = 1

        for j in range(m):
            s = seg[j]
            prefix[0] = 0
            for i in range(maxT + 1):
                prefix[i + 1] = (prefix[i] + dp[j % 2][i]) % mod

            for i in range(maxT + 1):
                L = max(0, i - (s - 1))
                R = i
                dp[(j + 1) % 2][i] = (prefix[R + 1] - prefix[L] + mod) % mod

        lessK = sum(dp[m % 2][:maxT + 1]) % mod

        return (total - lessK + mod) % mod
```


# Things i learnt revised !
* Used bottom up with some more optimization.
* FOr using bottom-up we should always think for Recursion first.
* We'll do the topic-wise problems soon.
