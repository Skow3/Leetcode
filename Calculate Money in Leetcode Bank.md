# EASY 
1716

## PATTERN RECOGNITION:
```TEXT
1,2,3,4,5,6,7 = 28
,2,3,4,5,6,7,8= 35 [ 28 + 7]          ======== 35+28 = 7(4+5) 9
3,4,5,6,7,8,9, = 42 [ 28 + 14 ]  ===== 7( 9+6) = 15
4,5,6,7,8,9,10 = 49 [ 28 + 21] ===== 7 (15+7) == 22
```

# SOLUTION:
```python
class Solution:
    def totalMoney(self, n: int) -> int:
        k = n//7
        sumt=0
        if k < 1:
            for i in range(n+1):
                sumt+=i
        else:
            for i in range(k):
                sumt+= 7*(4+i)
            if n%7 !=0:
                for i in range(k+1,k+1 + n%7):
                    print(i)
                    sumt+=i

        return(sumt)
```
