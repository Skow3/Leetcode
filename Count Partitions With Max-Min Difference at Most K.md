# MEDIUM
3578

```cpp
class Solution {
public:
    int countPartitions(vector<int>& nums, int k) {
        const int MOD = 1'000'000'007;
        int n = nums.size();

        vector<long long> dp(n + 1, 0), pref(n + 1, 0);
        dp[0] = 1;
        pref[0] = dp[0];

        deque<int> maxq, minq;
        int left = 0;

        for (int i = 1; i <= n; ++i) {
            int idx = i - 1;
            int val = nums[idx];

            while (!maxq.empty() && nums[maxq.back()] <= val)
                maxq.pop_back();
            maxq.push_back(idx);

            while (!minq.empty() && nums[minq.back()] >= val)
                minq.pop_back();
            minq.push_back(idx);

            while (!maxq.empty() && !minq.empty() &&
                   (long long)nums[maxq.front()] - nums[minq.front()] > k) {
                if (maxq.front() == left) maxq.pop_front();
                if (minq.front() == left) minq.pop_front();
                ++left;
            }

            long long total = pref[i - 1];
            long long sub = (left > 0 ? pref[left - 1] : 0);
            dp[i] = (total - sub) % MOD;
            if (dp[i] < 0) dp[i] += MOD;

            pref[i] = (pref[i - 1] + dp[i]) % MOD;
        }

        return (int)dp[n];
    }
};
```
