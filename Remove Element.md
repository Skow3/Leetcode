## This question is important as it was asked in Amazon

Now ..
First Solution
##### Python 
```python
class Solution(object):
    def removeElement(self, nums, val):
        """
        :type nums: List[int]
        :type val: int
        :rtype: int
        """
        k=0
        for i in range(0,len(nums)-1):
            if nums[i] != val:
                nums[k] = nums[i]
                k+=1
        print(nums)
        return k
```

This was the method of using two pointers both in one direction 
Tho this was perfectly working for me in Ipynb it was not being accepted in leetcode for the 38th Case 

---

Then the Solution 2nd 
##### C++
```c++
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        int i = 0, n = nums.size();

        while (i < n) {
            if (nums[i] == val) {
                nums[i] = nums[n - 1];
                n--;
            } else {
                i++;
            }
        }
        return n;
    }
};
```

Here i'm again using two pointers technique but this time both are in opposite directions
