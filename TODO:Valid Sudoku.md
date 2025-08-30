# Valid Sudoku
36

WILL EXPLAIN IT LATER ON:
```python
class Solution:
    def isValidSudoku(self, board):
        row = [[False] * 9 for _ in range(9)]
        col = [[False] * 9 for _ in range(9)]
        box = [[False] * 9 for _ in range(9)]

        for i in range(9):
            for j in range(9):
                if board[i][j] == '.':
                    continue

                digit = int(board[i][j]) - 1  # -1 to make index 0-based
                boxIndex = (i // 3) * 3 + (j // 3)

                if row[i][digit] or col[j][digit] or box[boxIndex][digit]:
                    return False

                row[i][digit] = col[j][digit] = box[boxIndex][digit] = True

        return True

```
