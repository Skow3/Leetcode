# Hard
2561

---

* The question was quite on a tougher side.
* The main part of the question was to think about finding the min Score by sorting and checking for both selections.

# THINKING ROUTE
> CASES POSSIBLE:
1. Impossible case
2. Possible Case

#### Impossible Case:
  * For this we can go for calculating a map for the frequencies of the Fruits in different tables like this :
      1. WE'll take basket 1 entries as +ve and basket 2 as -ve.
      2. And will start adding to the frequencies table.
         Then the impossible cases will be those where:
         * The Final frequency of any digit will be Odd.
         * The addition of +ve Final Frequencies and -ve ones is not 0
        
## Possible cases:
After finding that final hash table we know that for every 2 values [freq] 1 swap will be done.
For example if the +ve frequencies are: 5,5,6,6,2,2
and -ve are : 1,1,4,4,9,9

I.e each is 2 /-2

Now we'll differentiate basket 1 cases and sort them in ascending order
and for basket 2 in descending order
i.e [ 2,2,5,5,6,6]
    [9,9,4,4,1,1]

---

Now we'll check for the swapping 
For swapping we'll swap(6,1) + swap(5,4)+ swap(2,9) = 1+4+2
# IMPORTANT
But since we have to find minimum swaps therefore : we'll do like this 
* Swap the maximum element of the basket 1 with min element of basket 2
* Then use the min element of basket 2[copy] and swap with the second largest element of basket 1.
* So that we can decrease swap() min value.
* Therefore we can have it like this score += min(cost,2*minc) [ where cost = min(normal swapping)]

---

# CODE 
```cpp
class Solution {
public:
    long long minCost(vector<int>& basket1, vector<int>& basket2) {
        unordered_map<int, int> mp;
        int minEl = INT_MAX;

        for(int &x : basket1) {
            mp[x]++;
            minEl = min(minEl, x);
        }

        for(int &x : basket2) {
            mp[x]--;
            minEl = min(minEl, x);
        }

        vector<int> finalList;
        for(auto &it : mp) {
            int cost  = it.first;
            int count = it.second;

            if(count == 0) {
                continue;
            }

            if(count % 2 != 0) {
                return -1;
            }

            for(int c = 1; c <= abs(count)/2; c++) {
                finalList.push_back(cost);
            }
        }

        nth_element(begin(finalList), begin(finalList)+finalList.size()/2, end(finalList));

        long long result = 0;
        for(int i = 0; i < finalList.size()/2; i++) {
            result += min(finalList[i], minEl*2);
        }

        return result;

    }
};
```
TOC : O(n)
ET= 64ms


### Python
```python
import heapq

class Solution:
    def minCost(self, basket1, basket2):
        mp = {}
        minc = float('inf')
        for x in basket1:
            mp[x] = mp.get(x, 0) + 1
            minc = min(minc, x)
        for x in basket2:
            mp[x] = mp.get(x, 0) - 1
            minc = min(minc, x)
        final_list = []
        for cost, count in mp.items():
            if count % 2 != 0:
                return -1
            final_list.extend([cost] * (abs(count) // 2))
        k = len(final_list) // 2
        smallest_half = heapq.nsmallest(k, final_list)
        result = 0
        for cost in smallest_half:
            result += min(cost, 2 * minc)

        return result
```


---

