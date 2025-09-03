# HARD
3027

---

#will do this on holiday

```python
class Solution:
    def numberOfPairs(self, points):
        n = len(points)
        
        points.sort(key=lambda p: (p[0], -p[1]))
        
        result = 0
        
        for i in range(n):
            y1 = points[i][1]
            best_y = -float('inf')
            
            for j in range(i + 1, n):
                y2 = points[j][1]
                
                if y2 <= y1 and y2 > best_y:
                    result += 1
                    best_y = y2
                    
        return result
```
