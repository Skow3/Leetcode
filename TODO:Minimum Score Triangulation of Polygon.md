# MEDIUM
1039

```CPP
class Solution {
public:
    int minScoreTriangulation(vector<int>& values) {
        int n = values.size();
        vector<vector<int>> triangle(n, vector<int>(n, 0));
        
        for (int len = 2; len < n; len++) {
            for (int row = 0; row + len < n; row++) {
                int col = row + len;
                triangle[row][col] = INT_MAX;
                
                for (int k = row + 1; k < col; k++) {
                    int prev_left  = triangle[row][k];
                    int prev_right = triangle[k][col];
                    int cost = values[row] * values[col] * values[k] + prev_left + prev_right;
                    
                    triangle[row][col] = min(triangle[row][col], cost);
                }
            }
        }
        
        return triangle[0][n - 1];
    }
};

```
