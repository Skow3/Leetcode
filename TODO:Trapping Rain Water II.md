# HARD
407

# FIRST SOLUTION:
```python
class Solution:
    def trapRainWater(self, heightMap):
        if not heightMap or not heightMap[0]:
            return 0

        m, n = len(heightMap), len(heightMap[0])

        # I'm doing min-heap implementation (priority queue)
        class MinHeap:
            def __init__(self):
                self.data = []

            def push(self, item):
                self.data.append(item)
                self._sift_up(len(self.data) - 1)

            def pop(self):
                if not self.data:
                    return None
                self._swap(0, len(self.data) - 1)
                item = self.data.pop()
                self._sift_down(0)
                return item

            def empty(self):
                return len(self.data) == 0

            def _sift_up(self, idx):
                parent = (idx - 1) // 2
                while idx > 0 and self.data[idx][0] < self.data[parent][0]:
                    self._swap(idx, parent)
                    idx = parent
                    parent = (idx - 1) // 2

            def _sift_down(self, idx):
                n = len(self.data)
                while True:
                    left = 2 * idx + 1
                    right = 2 * idx + 2
                    smallest = idx
                    if left < n and self.data[left][0] < self.data[smallest][0]:
                        smallest = left
                    if right < n and self.data[right][0] < self.data[smallest][0]:
                        smallest = right
                    if smallest == idx:
                        break
                    self._swap(idx, smallest)
                    idx = smallest

            def _swap(self, i, j):
                self.data[i], self.data[j] = self.data[j], self.data[i]

        directions = [(0,1), (1,0), (0,-1), (-1,0)]
        visited = [[False] * n for _ in range(m)]
        heap = MinHeap()

        for r in range(m):
            for c in [0, n - 1]:
                heap.push((heightMap[r][c], (r, c)))
                visited[r][c] = True

        for c in range(n):
            for r in [0, m - 1]:
                if not visited[r][c]:
                    heap.push((heightMap[r][c], (r, c)))
                    visited[r][c] = True

        trappedWater = 0

        while not heap.empty():
            height, (i, j) = heap.pop()

            for dr, dc in directions:
                i_, j_ = i + dr, j + dc
                if 0 <= i_ < m and 0 <= j_ < n and not visited[i_][j_]:
                    trappedWater += max(0, height - heightMap[i_][j_])
                    heap.push((max(height, heightMap[i_][j_]), (i_, j_)))
                    visited[i_][j_] = True

        return trappedWater

```


# WILL DO AND EXPLAIN THE MORE OPTIMIZE VERSIONS LATER
