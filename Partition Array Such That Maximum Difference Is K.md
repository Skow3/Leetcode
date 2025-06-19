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

This was my first approach, though it passed only 44 /97 testcases it was failing due to :
1. In findj function when the index returned was 0 it was not functioning quite well.
2. It was a bogus first try and brute force approach.

Then what i thought of is doing the same thing but reversed kind of:
1. Right now we were getting k+i values and checking for same value indices but it was time taking and not that worthy.
2. So, Instead of that we'll calculate k+start and then check which numbers are greater than k .. and since we would have
splitted there soo.. we'll have a count variable to count that.

# FINAL APPROACH:
```python
class Solution(object):
    def partitionArray(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: int
        """
        nums.sort()
        start = nums[0]
        count=0
        for i in nums:
            if i - start > k:
                count+=1
                start = i ## since for next subsequence the i will be this number 
        return count
```


