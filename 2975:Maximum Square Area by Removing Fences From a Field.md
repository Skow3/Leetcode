# MEDIUM 
2975

# This question was also nice did this type of question yesterday but this had completely different approach.
Here the first code i made was giving TLE on 400 cases

# CODE 1
```python
class Solution(object):
    def maximizeSquareArea(self, m, n, hFences, vFences):
        """
        :type m: int
        :type n: int
        :type hFences: List[int]
        :type vFences: List[int]
        :rtype: int
        """
        hFences= [1]+hFences+[m]
        vFences= [1]+vFences+[n]
        #print(f"hFences= {hFences}")
        #print(f"vFences={vFences}")
        def calc(k):
            ans=0
            for i in vFences:
                #print(k,i)
                wid = i-k
                for g in hFences:
                    for j in hFences:
                        if j-g== wid:
                            #print(f"MAIN  : {k},{i},{j},{wid}")
                            ans = max(wid,ans)
            return ans
        maxans=0
        for k in vFences:
            #print("k")
            maxans= max(calc(k),maxans)
        if maxans==0:
            return -1
        return maxans*maxans

```


# CODE 2
```PYTHON
class solution(object):
    def maximizeSquareArea(self, m, n, hFences, vFences):
        """
        :type m: int
        :type n: int
        :type hFences: List[int]
        :type vFences: List[int]
        :rtype: int
        """
        ans=-1
        hFences= [1]+hFences+[m]
        vFences= [1]+vFences+[n]
        WIDTHH = set()
        for i in hFences:
            for j in hFences:
                diff=j-i
                WIDTHH.add(diff)
        for i in vFences:
            for j in vFences:
                diff=j-i
                if diff in WIDTHH:
                    ans=max(ans,diff)
        if ans==-1 or ans==0:
            return -1
        return ans*ans
```

This time i forgot Modulo

# FINAL SUBMISSION
```python
class Solution(object):
    def maximizeSquareArea(self, m, n, hFences, vFences):
        """
        :type m: int
        :type n: int
        :type hFences: List[int]
        :type vFences: List[int]
        :rtype: int
        """
        ans=-1
        hFences= [1]+hFences+[m]
        vFences= [1]+vFences+[n]
        WIDTHH = set()
        for i in hFences:
            for j in hFences:
                diff=j-i
                WIDTHH.add(diff)
        for i in vFences:
            for j in vFences:
                diff=j-i
                if diff in WIDTHH:
                    ans=max(ans,diff)
        if ans==-1 or ans==0:
            return -1
        return (ans*ans) % (10**9 + 7)

```


---


# OPTMIZATION OF CODE 
```PYTHON
class Solution:
    def maximizeSquareArea(self, m: int, n: int, hFences: List[int], vFences: List[int]) -> int:
        maxL=0
        seen=set()
        def findLen(fences, calM):
            nonlocal maxL
            fences.sort() # not necessary but much faster
            for x, y in combinations(fences, 2):
                # the combinations have always x<=y 
                # for a sorted list, no need for abs
                # abs makes the code slower
                # but not true for a unsorted list
                Len=y-x
                if calM: 
                    if Len>maxL and Len in seen:
                        maxL=Len
                else:
                    seen.add(Len) 
        hz, vz=len(hFences)+2, len(vFences)+2
        if hz>vz:
            return self.maximizeSquareArea(n, m, vFences, hFences)
        hFences+=[1, m]
        vFences+=[1, n]
        findLen(hFences, False)
        findLen(vFences, True)
        return -1 if maxL==0 else maxL*maxL%(10**9+7)

```


Here is a concise point-wise summary of why that code is better:

1. It never generates invalid distances
   * Uses combinations(x, 2) so x < y always
   * No negative values
   * No zero values

2. It avoids unnecessary absolute value calls
   * Sorts the list first
   * Uses y - x directly
   * This is faster than abs(j - i)

3. It uses a two-phase strategy
   * First stores all distances from one direction
   * Then checks distances from the other direction on the fly
   * Avoids building two full sets

4. It processes the smaller fence list first
   * This keeps the set smaller
   * Improves lookup speed
   * Reduces overall work

5. It avoids duplicate and useless comparisons
   * combinations() only gives unique pairs
   * No self-pairs
   * No mirrored pairs

6. It updates the maximum only when necessary
   * Checks if the value is greater before updating
   * Avoids useless assignments

7. It uses the correct modulo expression
   * Uses 10**9 + 7
   * Avoids XOR mistake

8. Overall, it is more correct, cleaner, and faster
   * Fewer invalid values
   * Less wasted work
   * Better structure
