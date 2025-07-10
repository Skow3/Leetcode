# MEDIUM

will do it on Monday ... currently in hurry of packing for travelling

```cpp
class Solution {
public:
    int maxFreeTime(int eventTime, vector<int>& startTime, vector<int>& endTime) {
        vector<int> arr; //store durations of free gaps

        // Will explain on Monday
        arr.push_back(startTime[0]);

        for(int i = 1; i < startTime.size(); i++) {
            arr.push_back(startTime[i] - endTime[i-1]);
        }

        arr.push_back(eventTime - endTime[endTime.size()-1]);

        int n = arr.size();
        vector<int> mr(n, 0);
        vector<int> ml(n, 0);
        for(int i = n-2; i >= 0; i--) {
            mr[i] = max(mr[i+1], arr[i+1]);
        }

        for(int i = 1; i < n; i++) {
            ml[i] = max(ml[i-1], arr[i-1]);
        }


        int result = 0;
        //Iterating on the arr
        for(int i = 1; i < n; i++) {
            int currEventTime = endTime[i-1] - startTime[i-1]; //duration of event = d

            //Case-1 Moving completely out
            if(currEventTime <= max(ml[i-1], mr[i])) {
                result = max(result, arr[i-1] + currEventTime + arr[i]);
            }

            //case-2 shift left or right
            result = max(result, arr[i-1] + arr[i]);
        }

        return result;


    }
};
```
