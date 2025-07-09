# MEDIUM
3439

---

Very tight schedule rn bcs of travelling to college again
Doing the temp solution using sliding window in cpp 
will do the python version on sunday 13th July
```cpp
class Solution {
public:
    int maxFreeTime(int eventTime, int k, vector<int>& startTime, vector<int>& endTime) {
        vector<int> arr; //store durations of free gaps

        // doing the cpp code rn will do the python one later on aftr travel
        arr.push_back(startTime[0]);

        for(int i = 1; i < startTime.size(); i++) {
            arr.push_back(startTime[i] - endTime[i-1]);
        }

        arr.push_back(eventTime - endTime[endTime.size()-1]);

        //Khandani sliding window
        int i = 0;
        int j = 0;
        int mas = 0;
        int currSum = 0;

        int n = arr.size();
        while(j < n) {
            currSum += arr[j];

            if(i < n && j-i+1 > k+1) {
                currSum -= arr[i];
                i++;
            }

            mas = max(mas, currSum);
```
            j++;
        }

        return mas;
    }
};
