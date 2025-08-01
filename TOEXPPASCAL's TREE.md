# EASY

# FINAL SOLUTION
class Solution(object):
    def generate(self, numRows):
        """
        :type numRows: int
        :rtype: List[List[int]]
        """
        triangle = []

        for row_num in range(numRows):
            # Start each row with 1
            row = [1] * (row_num + 1)

            # Each element (except the first and last of the row) is the sum of the two elements above it
            for j in range(1, row_num):
                row[j] = triangle[row_num - 1][j - 1] + triangle[row_num - 1][j]

            triangle.append(row)

        return triangle
```
