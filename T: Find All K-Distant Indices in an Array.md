# EASY
2200

The question is marked easy but it took a lot of time for me to come to a good solution.
* 

---

# APPROACH 1:
```PYTHON
class Solution(object):
    def findKDistantIndices(self, nums, key, k):
        """
        :type nums: List[int]
        :type key: int
        :type k: int
        :rtype: List[int]
        """
        g = []
        ans = []
        for i in range(len(nums)):
            if nums[i] == key :
                g.append(i)
        g.sort()
        print(g)
        for i in range(len(nums)):
                if abs(i-g[-1]) <= k or abs(i-g[0]) <=k:
                    ans.append(i)
        print(ans)
```


# APPROACH 2:
```PYTHON
class Solution(object):
    def findKDistantIndices(self, nums, key, k):
        """
        :type nums: List[int]
        :type key: int
        :type k: int
        :rtype: List[int]
        """
        ans = []
        for i in range(len(nums)):
            if nums[i] == key:
                j=0
                while j!=k+1:
                    if (i+j) >=0 and (i+j)< len(nums):
                        print(f"{i} , {j} {i+j}")
                        ans.append(i+j)
                    if (i-j) >=0 and (i-j)< len(nums):
                        print(f"{i} , {j} {i-j}")
                        ans.append(i-j)
                    j+=1
                    print(j)
        anstt = list(set(ans))
        anstt.sort()
        print(anstt)

```

# APPROACH 3 [ FINAL SOLUTION ] 
```PYTHON
class Solution(object):
    def findKDistantIndices(self, nums, key, k):
        """
        :type nums: List[int]
        :type key: int
        :type k: int
        :rtype: List[int]
        """
        n = len(nums)
        ans = set()
        for i in range(n):
            if nums[i] == key:
                start = max(i - k, 0)
                end = min(i + k, n - 1)
                for g in range(start, end + 1):
                    ans.add(g)
        return sorted(ans)
```
TOC : 50%

WILL WRITE THE APPROACHES LATER ON

THIS IS THE CPP CODE WHICH I REFERRED AT LAST AFTER SUBMISSION 
For this ...
```CPP
class Solution {
public:
    vector<int> findKDistantIndices(vector<int>& nums, int key, int k) {
        int n = nums.size();

        vector<int> result;

        for(int j = 0; j < n; j++) {
            if(nums[j] == key) {
                int start = max(j-k, 0);
                int end   = min(j+k, n-1);

                if(result.size() > 0 && result.back() >= start) {
                    start = result.back()+1;
                }

                for(int i = start; i <= end; i++) {
                    result.push_back(i);
                }
            }
        }
        return result;
    }
};
```
TOC : 100%
