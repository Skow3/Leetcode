# HARD

* This question will do in python later.

# SOLUTION 
```cpp
class Solution {
public:
    long long minimumDifference(vector<int>& nums) {
        int N = nums.size(); //since it is given 3*n
        int n = N/3;

        vector<long long> lmins(N, 0);  // Left minimum sum
        vector<long long> rmins(N, 0); // right minimum sum

        priority_queue<int> maxHeap;
        long long leftSum = 0;
        for(int i = 0; i < 2*n; i++) {
            maxHeap.push(nums[i]);
            leftSum += nums[i];

            if(maxHeap.size() > n) {
                leftSum -= maxHeap.top();
                maxHeap.pop();
            }

            lmins[i] = leftSum;
        }


        priority_queue<int, vector<int>, greater<int>> minHeap;
        long long rightSum = 0;
        for(int i = N-1; i >= n; i--) {
            minHeap.push(nums[i]);
            rightSum += nums[i];

            if(minHeap.size() > n) {
                rightSum -= minHeap.top();
                minHeap.pop();
            }

            rmins[i] = rightSum;
        }


        long long result = LLONG_MAX; // Alotting a very high number

        for(int i = n-1; i <= 2*n-1; i++) {
            result = min(result, lmins[i] - rmins[i+1]);
        }

        return result;


    }
};
```


### What is LLONG_MAX?
* LLONG_MAX is a macro defined in the <climits> header (or <limits.h> in C).
* It represents the maximum possible value that a long long (i.e., long long int) variable can hold.

```cpp
LLONG_MAX = 9223372036854775807  // 2^63 - 1
```
