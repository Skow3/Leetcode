# MEDIUM
2787

* I was on the verge of solving this question but since this is my project week and i'm gonna make some projects in this week. So was not able to give that much time to this :

* # FIRST APPROACH [vague]
* ```python
    class Solution(object):
    def numberOfWays(self, n, x):
        """
        :type n: int
        :type x: int
        :rtype: int
        """
        ultim =n
        count=0
        while n!=0:
            rem=n
            sumt=0
            while rem!=0:
                root = int(rem**(1/x))
                if root==1 and rem!=1 :
                    break
                sumt+=rem
                rem = rem-root**x
                if sumt == ultim:
                    count+=1
            n-=1
        return count
  ```
  Forgot to add that modulo in return soo..

  then

  # 2nd Approach
  ```python
  class Solution(object):
    def numberOfWays(self, n, x):
        # SOLVING USING DP
        MOD = 10**9 + 7
        powers = []
        i = 1
        while True:
            val = i ** x
            if val > n:
                break
            powers.append(val)
            i += 1

        dp = [0] * (n + 1)
        dp[0] = 1

        for p in powers:
            for s in range(n, p - 1, -1):
                dp[s] = (dp[s] + dp[s - p]) % MOD

        return dp[n]
``

This was using DP and will explain it later

WILL TRY TO SOLVE WITH THE VAGUE AAPROACH ALSO...


