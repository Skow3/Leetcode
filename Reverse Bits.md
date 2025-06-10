# EASY 

```python
class Solution:
    # @param n, an integer
    # @return an integer
    def reverseBits(self, n):
        res = 0
        for i in range(32):
            bit = (n >> i) & 1
            res = res | (bit << (31 - i))
        return res
```

### Problem Statement

Given a 32-bit unsigned integer `n`, the task is to reverse its bits and return the resulting integer.

### Step-by-Step Explanation

1. **Initialize the result variable**:

   ```python
   res = 0
   ```

   This variable will accumulate the reversed bits.

2. **Iterate through each of the 32 bits**:

   ```python
   for i in range(32):
   ```

   The loop runs 32 times, once for each bit in the integer.

3. **Extract the `i`-th bit from `n`**:

   ```python
   bit = (n >> i) & 1
   ```

   * `n >> i`: Right shift `n` by `i` positions, moving the `i`-th bit to the least significant bit (LSB) position.
   * `& 1`: Mask all bits except the LSB. This gives the value (0 or 1) of the `i`-th bit.

4. **Set the reversed bit in the correct position**:

   ```python
   res = res | (bit << (31 - i))
   ```

   * `bit << (31 - i)`: Shift the extracted bit to its new position in the reversed integer.
   * `res | ...`: Use bitwise OR to set the bit in `res`.

5. **Return the reversed result**:

   ```python
   return res
   ```

### Example

For input `n = 43261596`, which is:

```
00000010100101000001111010011100 (binary)
```

The output would be:

```
00111001011110000010100101000000 (binary)
```

Which corresponds to `964176192` in decimal.

---

