# IMPORTANT
#### HARD

> Python

### We'll do it using DFS :
  We can visualize it by drawing a tree like structure for this question 

``` python
class Solution(object):
    def maxCandies(self, status, candies, keys, containedBoxes, initialBoxes):
        """
        :type status: List[int]
        :type candies: List[int]
        :type keys: List[List[int]]
        :type containedBoxes: List[List[int]]
        :type initialBoxes: List[int]
        :rtype: int
        """
        visited = set()    # USING SET FOR UNIQUE ENTRIES
        foundbox = set()
        def dfs(i):
            candy =0 
            if i in visited:
                return 0
            if status[i] == 0:
                foundbox.add(i)
                return 0
            visited.add(i)
            candy+= candies[i]
            for inside in containedBoxes[i]:
                candy+= dfs(inside)
            for Keybox in keys[i]:
                status[Keybox] = 1 # NOW I CAN OPEN IT
                if Keybox in foundbox:
                    candy+= dfs(Keybox)

            return candy
        c=0
        for i in initialBoxes:
            c+= dfs(i)
        return c
```


---

> C++

### USING BFS

```Cpp
class Solution {
public:
    int maxCandies(vector<int>& status, vector<int>& candies, vector<vector<int>>& keys, vector<vector<int>>& containedBoxes, vector<int>& initialBoxes) {
        
        int candiesCollected = 0;
        unordered_set<int> visited;
        unordered_set<int> foundBoxes;
        //T.C : O(n) visiting all box only once , n = number of boxes
        //S.C : O(n)

        queue<int> que; //insert those which you have now and you can open it
        for(int &box : initialBoxes) {
            foundBoxes.insert(box);
            if(status[box] == 1) {
                que.push(box);
                visited.insert(box);
                candiesCollected += candies[box];
            }
        }

        while(!que.empty()) {
            int box = que.front();
            que.pop();

            for(int &insideBox : containedBoxes[box]) {
                foundBoxes.insert(insideBox);
                if(status[insideBox] == 1 && !visited.count(insideBox)) {
                    que.push(insideBox);
                    visited.insert(insideBox);
                    candiesCollected += candies[insideBox];
                }
            }

            for(int &boxKey : keys[box]) {
                status[boxKey] = 1; //can be opened in future if we reach this box
                if(foundBoxes.count(boxKey) && !visited.count(boxKey)) {
                    que.push(boxKey);
                    visited.insert(boxKey);
                    candiesCollected += candies[boxKey];
                }
            }
        }

        return candiesCollected;
    }
};
```


