# Medium
1498

Again a question for subsequence but yes this time i got the answer and the logic.
From next time i'll try to make the logic till the end ...

What logics i made ..

1. Since we have to do the maximum and minimum logic , sorted the array .
2. Enumerated the array before sorting to have the indices there.
3. Then laid a logic to make and increase the count of the subsequences since it would be 2<sup>j-i-1</sup>

## FIRST APPROACH [Not taken the indices in role] and also the mod
```python
class Solution(object):
    def numSubseq(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        countt=0
        n = len(nums)
        for i in range(n):
            for j in range(i,n):
                if nums[i] + nums[j] <= target:
                    if i==j:
                        countt+=1
                    else:
                        countt += 2**(j-i-1)
                else:
                    break
        return countt

```

### APPROACHING TOWARDS SOLUTION 
```python
# now modifying the code for sorted 
nums = [7,10,7,3,7,5,4]
n = len(nums)
target = 12
indexed  = list(enumerate(nums))
sortp = sorted(indexed,key=lambda x: x[1])
print(sortp)
mod = pow(10,9)+7
print(indexed)
countt=0
ans = []
for i in range(n):
    for j in range(i,n):
        print(f"{sortp[i][0]},{sortp[j][0]} -- > {sortp[i][1]},{sortp[j][1]}")
        if sortp[i][1] + sortp[j][1] <= target:
            if sortp[i][0]==sortp[j][0]:
                countt+=1
            else:
                countt += 2**(abs(sortp[j][0]-sortp[i][0])-1)
        else:
            break
print(countt% mod)
print(ans)
```




# FINAL SOLUTION MODIFIED[FINAL]
```python
class Solution(object):
    def numSubseq(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        n = len(nums)
        mod = 10**9 + 7
        indexed  = list(enumerate(nums))
        sortp = sorted(indexed, key=lambda x: x[1])
        pow2 = [1] * (n+1)
        ## Pre -calculating the powers
        for i in range(1, n+1):
            pow2[i] = (pow2[i-1] * 2) % mod
        countt = 0
        i, j = 0, n - 1
        while i <= j:
            if sortp[i][1] + sortp[j][1] <= target:
                countt = (countt + pow2[j - i]) % mod
                i += 1
            else:
                j -= 1

        return countt
```
