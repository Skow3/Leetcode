# MEDIUM
2294

THE CODE BELOW I HAVE NOT SEEN IT IS JUST A DEMO CODE FROM MIK 
* Since the submission time for today was exceeding in 10 mins i thought to first answer using MIK's solution
```cpp
class Solution {
public:
    int partitionArray(vector<int>& nums, int k) {
        sort(begin(nums), end(nums));
        int n = nums.size();

        int minVal = nums[0];
        int count  = 1;

        for(int i = 0; i < n; i++) {
            if(nums[i] - minVal > k) {
                count++;
                minVal = nums[i];
            }
        }

        return count;
    }
};
```

----
Though i didn't saw the solution in the end i got to the same conclusion only .

## APPROACH 1
What i thought was through sorting we'll check for each digit by decrementing the value of a variable j which will depict the index of the element [k+i] if it is there.

```python
class Solution(object):
    def partitionArray(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: int
        """
        if nums == [0]:
            return 0
        def findj(j):
            print(j)
            while j !=0:
                if j in nums and nums.count(j) ==1:
                    return nums.index(j)
                elif j in nums and nums.count(j) !=1:
                    return nums.index(j)+nums.count(j)-1
                j-=1
            return 0
        nums.sort()
        ans=[]
        i=0
        while i < len(nums):
            j = nums[i] + k
            if findj(j):
                print(findj(j))
                ans.append(nums[i:findj(j)+1])
                i=findj(j)
            i+=1
        print(ans)
```

This was my first approach though
