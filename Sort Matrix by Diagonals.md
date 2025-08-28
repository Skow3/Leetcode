# MEDIUM
3446

* Thought of a approach on reading the question itself but didn't have enough time today to code it by myself.
* So doing the normal traverse and sort approach

# FIRST SOLUTION: CPP
```cpp
class Solution {
public:
    int n;
    
    void customsort(int r, int c, vector<vector<int>>& grid, bool asc) {
        vector<int> vec; //diagonal elements starting from [r][c]

        int i = r;
        int j = c;

        while(i < n && j < n) {
            vec.push_back(grid[i][j]);
            i++;
            j++;
        }

        if(asc) {
            sort(begin(vec), end(vec));
        } else {
            sort(rbegin(vec), rend(vec));
        }

        i = r;
        j = c;
        for(int &val : vec) {
            grid[i][j] = val;
            i++;
            j++;
        }
    }

    vector<vector<int>> sortMatrix(vector<vector<int>>& grid) {
        n = grid.size();

        //Bottom Left - Non-Increasing Order
        for(int row = 0; row < n; row++) {
            customsort(row, 0, grid, false);
        }


        //Top Right - Non-Decreasing Order
        for(int col = 1; col < n; col++) {
            customsort(0, col, grid, true);
        }

        return grid;
    }
};
```

# THINGS I LEARNT FROM THE ABOVE CODE:
  1. For selecting the order of sorting of the vector elements it is not required that we have to always do like this :
```cpp
sort(begin(vec),end(vec),greater<int>);

// WE CAN DO IT BY [ IF WE HAVE TO SORT IN DESCENDING ORDER ]
i.e by adding r
sort(rbegin(vec),rend(vec));
```




# PYTHON SOLUTION: [THIS WILL TAKE A LOT OF MEMORY I.E 12MB]
```python
class Solution(object):
    def customsort(self, r, c, grid, asc):
        n = len(grid)
        vec = []

        i, j = r, c
        while i < n and j < n:
            vec.append(grid[i][j])
            i += 1
            j += 1

        vec.sort(reverse=not asc)

        i, j = r, c
        for val in vec:
            grid[i][j] = val
            i += 1
            j += 1

    def sortMatrix(self, grid):
        """
        :type grid: List[List[int]]
        :rtype: List[List[int]]
        """
        n = len(grid)

        # for 0,0 and downward diagonals (descending)
        for row in range(n):
            self.customsort(row, 0, grid, asc=False)

        # for diagonals above [0][0] (ascending)
        for col in range(1, n):
            self.customsort(0, col, grid, asc=True)

        return grid
```
