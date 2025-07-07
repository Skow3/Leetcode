1353
# MEDIUM
I'll rate this question from easy--> medium .

* Thing was as i went through the examples and tested with just return len(events) to check for more examples.
As soon as i understood the examples and i simply went to solve the question in my notebook.
I got that i'll append the events[i][1] in an array and then sort it every time.
But this would have taken a lot of time [I thought]

So i went on searching for how to use MIN-HEAP in python and c++.

In python we can use min-heap by :
```python
import heapq
testheap = []
# TO PUSH
heapq.heappush(testheap,1)
# TO POP
heapq.heappop(testheap,2)
etc..
```

How to use it in cpp:
```cpp
priority_queue<int, vector<int>,greater<int>>pq;
// TO PUSH
pq.push(events[i][1])
// to pop
pq.pop
```

# SOLUTION
```python
import heapq
class Solution(object):
    def maxEvents(self, events):
        """
        :type events: List[List[int]]
        :rtype: int
        """
        events.sort()
        d = events[0][0]
        i=0
        count = 0 
        # Initialising the min-heap
        min_heap = []

        n = len(events)
        while min_heap or i < n:
            if not min_heap:
                d = events[i][0]
            while i<n  and events[i][0] == d :
                heapq.heappush(min_heap,events[i][1])
                i+=1
        
            if min_heap:
                heapq.heappop(min_heap)
                count+=1
            d+=1

            while min_heap and min_heap[0] < d:
                heapq.heappop(min_heap)
        return count
```



----


# SOLUTION IN CPP JUST FOR REFERENCE:
```CPP
class Solution {
public:
    int maxEvents(vector<vector<int>>& events) {
        int n = events.size();

        sort(begin(events), end(events));

        priority_queue<int, vector<int>, greater<int>> pq; //min-heap
        int day = events[0][0]; //5
        int i   = 0;
        int count = 0; //result number of events attended

        while(!pq.empty() || i < n) {
            
            if(pq.empty()) {
                day = events[i][0];
            }

            while(i < n && events[i][0] == day) {
                pq.push(events[i][1]);
                i++;
            }

            if(!pq.empty()) {
                pq.pop(); //1 event attended on this day
                count++; //counting the result
            }

            day++;

            //skip those events whose endDay < day
            while(!pq.empty() && pq.top() < day) {
                pq.pop();
            }
        }

        return count;
    }
};
```


---

# THINGS LEARNT / REVISED:
### 1. HEAPQ ---  MIN_HEAP
### 2. REMEMBER THIS 
