# IMPORTANT QUESTION
ASKED IN AMAZON


```python
class Solution(object):
    def candy(self, ratings):
        """
        :type ratings: List[int]
        :rtype: int
        """
        ansl= [1 for _ in range(len(ratings))]
        ansr= [1 for _ in range(len(ratings))]
        for i in range(1,len(ratings)):
                if ratings[i-1]<ratings[i]:
                    ansl[i] = ansl[i-1] +1
        for i in range(-2,-len(ratings)-1,-1):
                if ratings[i+1]<ratings[i]:
                    ansr[i] = ansr[i+1] +1
        ans = [max(x,y) for x,y in zip(ansl,ansr)]
        fin = sum(ans)
        return fin
```


## APPROACH 2 : STAIRS APPROACH

```python
class Solution(object):
    def candy(self, ratings):
        """
        :type ratings: List[int]
        :rtype: int
        """
        k= len(ratings)
        i=1
        while i in range(len(ratings)):
            if ratings[i] == ratings[i-1]:
                i+=1
                continue
            peak = 0
            while(ratings[i]>ratings[i-1]):
                peak+=1
                k+= peak
                i+=1
                if i == len(ratings):
                    return k
            
            dip=0
            while i<len(ratings) and ratings[i]< ratings[i-1]:
                dip+=1
                k+=dip
                i+=1
                #if i== len(ratings):
                #    return k
            
            k-= min(peak,dip)
        return k
```

WILL WRITE ABOUT THIS TOMORROW ..
GOING TO SLEEP NOW

  
