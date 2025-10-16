# MEDIUM
2598

```cpp
class Solution {
public:
    int findSmallestInteger(vector<int>& nums, int value) {
        unordered_map<int, int> mp;

        for(int &num : nums) {
            int r = ((num % value) + value) % value;

            mp[r]++;
        }

        int Maxp = 0;

        while(mp[(Maxp % value)] > 0) {
            mp[(Maxp % value)]--;

            Maxp++;
        }

        return Maxp;
    }
};
```
