# MEDIUM
756

* WAS ABLE TO THINK OF THE LOGIC AND WAS ABOUT TO CODE IT BUT TO CONFIRM AND TO UNDERSTAND ABOUT THE CORRECT BACKTRACKING LOGIC.
* THIS CPP CODE IS FROM MIK.

```cpp
class Solution {
public:
    unordered_map<string, bool> t;

    bool solve(string curr, unordered_map<string, vector<char>>& mp, int idx, string above) {
        if(curr.length() == 1) { //pyramid is formed and we are at the top
            return true;
        }

        string key = curr + "_" + to_string(idx) + "_" + above;

        if(t.count(key))
            return t[key];

        if(idx == curr.length()-1) { //time to move to next row i.e. abocve row
            return t[key] =  solve(above, mp, 0, "");
        }

        string pair = curr.substr(idx, 2);
        if(mp.find(pair) == mp.end()) {
            return t[key] = false;
        }

        for(char &ch : mp[pair]) {
            above.push_back(ch); //DO

            if(solve(curr, mp, idx+1, above) == true) //EXPLORE
                return t[key] = true;
            
            above.pop_back(); //UNDO
        }

        return t[key] = false;
    }

    bool pyramidTransition(string bottom, vector<string>& allowed) {
        unordered_map<string, vector<char>> mp;

        for(auto& pattern : allowed) {
            mp[pattern.substr(0, 2)].push_back(pattern[2]); //"ABC"
        }

        return solve(bottom, mp, 0, "");
    }
};

```



# Python

### SOLUTION 2
```python
class Solution(object):
    def __init__(self):
        self.memo = {}

    def solve(self, curr, mp, idx, above):
        if len(curr) == 1:
            return True

        key = (curr, idx, above)
        if key in self.memo:
            return self.memo[key]
        if idx == len(curr) - 1:
            self.memo[key] = self.solve(above, mp, 0, "")
            return self.memo[key]
        pair = curr[idx:idx + 2]
        if pair not in mp:
            self.memo[key] = False
            return False
        for ch in mp[pair]:
            if self.solve(curr, mp, idx + 1, above + ch):
                self.memo[key] = True
                return True
        self.memo[key] = False
        return False

    def pyramidTransition(self, bottom, allowed):
        """
        :type bottom: str
        :type allowed: List[str]
        :rtype: bool
        """
        mp = {}
        for pattern in allowed:
            key = pattern[:2]
            value = pattern[2]
            mp.setdefault(key, []).append(value)
        return self.solve(bottom, mp, 0, "")
```
