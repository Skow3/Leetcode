# HARD 
2106

---

# WILL DO IT AFTER EXAMS JUST SUBMITTING IT RN FOR STREAK

```PYTHON
class Solution:
    def maxTotalFruits(self, fruits, startPos, k):
        n = len(fruits)
        indices = [fruit[0] for fruit in fruits]
        prefixSum = [0] * n

        # Build prefix sum
        for i in range(n):
            prefixSum[i] = fruits[i][1] + (prefixSum[i - 1] if i > 0 else 0)

        def lower_bound(arr, target):
            left, right = 0, len(arr)
            while left < right:
                mid = (left + right) // 2
                if arr[mid] < target:
                    left = mid + 1
                else:
                    right = mid
            return left

        def upper_bound(arr, target):
            left, right = 0, len(arr)
            while left < right:
                mid = (left + right) // 2
                if arr[mid] <= target:
                    left = mid + 1
                else:
                    right = mid
            return left

        maxFruits = 0

        for d in range(k // 2 + 1):
            # Case 1: left d, right (k - 2d)
            remain = k - 2 * d
            i = startPos - d
            j = startPos + remain

            left = lower_bound(indices, i)
            right = upper_bound(indices, j) - 1

            if left <= right:
                total = prefixSum[right] - (prefixSum[left - 1] if left > 0 else 0)
                maxFruits = max(maxFruits, total)

            # Case 2: right d, left (k - 2d)
            i = startPos - remain
            j = startPos + d

            left = lower_bound(indices, i)
            right = upper_bound(indices, j) - 1

            if left <= right:
                total = prefixSum[right] - (prefixSum[left - 1] if left > 0 else 0)
                maxFruits = max(maxFruits, total)

        return maxFruits

```





# CPP [MIK]

```cpp
class Solution {
public:
    int maxTotalFruits(vector<vector<int>>& fruits, int startPos, int k) {
        int n = fruits.size();
        vector<int> prefixSum(n);
        vector<int> indices(n);
// CREDITS MIK
        // Build prefix sum and extract indices
        for (int i = 0; i < n; i++) {
            indices[i]   = fruits[i][0];
            prefixSum[i] = fruits[i][1] + (i > 0 ? prefixSum[i - 1] : 0);
        }

        int maxFrutis = 0;

        for (int d = 0; d <= k / 2; d++) {
            // Move
            int remain = k - 2 * d;
            int i   = startPos - d;
            int j  = startPos + remain;

            int left  = lower_bound(indices.begin(), indices.end(), i) - indices.begin();
            int right = upper_bound(indices.begin(), indices.end(), j) - indices.begin() - 1;

            if(left <= right) {
                int total = prefixSum[right] - (left > 0 ? prefixSum[left - 1] : 0);
                maxFrutis = max(maxFrutis, total);
            }

            // Second case: move right x, then left (k - 2x)
            i  = startPos - remain;
            j  = startPos + d;
            
            left  = lower_bound(indices.begin(), indices.end(), i) - indices.begin();
            right = upper_bound(indices.begin(), indices.end(), j) - indices.begin() - 1;

            if(left <= right) {
                int total = prefixSum[right] - (left > 0 ? prefixSum[left - 1] : 0);
                maxFrutis = max(maxFrutis, total);
            }
        }

        return maxFrutis;
    }
};
```
