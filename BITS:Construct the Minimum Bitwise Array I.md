# EASY
3314

So this question was tough if the constraints in the starting would have been given as very high.

But for the sake of getting it accepted i did the O(m*n) way 
i.e

# Solution 1 Brute force
```python
class Solution(object):
    def minBitwiseArray(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        ans=[]
        f=False
        for i in nums:
            f=False
            for j in range(i):
                if (j | j+1)==i:
                    ans.append(j)
                    f=True
                    break
            if not f:
                ans.append(-1)
            
        return ans
```


# Now the OPTIMIZATION

```python
class Solution(object):
    def minBitwiseArray(self, nums):
        ans = []
        for n in nums:
            if n != 2:
                ans.append(n - ((n + 1) & (-n - 1)) // 2)
            else:
                ans.append(-1)
        return ans
```

## Function Overview

```python
def minBitwiseArray(self, nums):
```

For each number `n` in `nums`, this function computes a transformed value using bitwise operations. If `n == 2`, it returns `-1` for that element.

---

## Core Formula

For `n ≠ 2`:

```
result = n - ((n + 1) & (-n - 1)) // 2
```

---

## Key Bitwise Identities Used

### 1. Two's Complement

```
-x = ~x + 1
```

So:

```
-(n + 1) = ~n
```

This means:

```
(n + 1) & (-n - 1) = (n + 1) & (~n)
```

---

### 2. Meaning of `(n + 1) & (~n)`

This expression isolates the **lowest zero bit** in the binary representation of `n`.

Example:

```
n = 10 = 1010
~n     = 0101
n + 1  = 1011

(n + 1) & (~n) = 0001
```

This gives the position of the lowest `0` bit.

---

### 3. Division by 2

Dividing by 2 shifts the isolated bit one position to the right:

```
x // 2  ≡  x >> 1
```

---

## What the Formula Does

1. Finds the lowest zero bit in `n`
2. Shifts it right by one
3. Subtracts it from `n`

This produces a smaller number with a controlled bit change.

---

## Example: n = 31

Binary form:

```
31 = 11111
```

Steps:

```
n + 1 = 32  = 100000
~n    = 00000... (relevant bits)

(n + 1) & (~n) = 100000 = 32
32 // 2 = 16

Final result = 31 - 16 = 15
```

---

## Special Case: n = 2

```
2 = 10 (binary)
```

This case is handled separately because the formula produces an invalid or undesired result based on the problem constraints.

---

## Time and Space Complexity

Let `N = len(nums)`

* Time Complexity: O(N)
* Space Complexity: O(N)

Each element is processed in constant time.
