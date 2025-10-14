# EASY
3349

```cpp
class Solution {
public:
    bool hasIncreasingSubarrays(vector<int>& nums, int k) {
        int n = nums.size();

        int cr = 1;
        int prevRun = 0;

        for(int i = 1; i < n; i++) {
            if(nums[i] > nums[i-1]) {
                cr++;
            } else { 
                prevRun = cr;
                cr = 1;
            }

            if(cr >= 2*k) {
                return true;
            }

            if(min(cr, prevRun) >= k) {
                return true;
            }
        }

        return false;
    }
};

```
