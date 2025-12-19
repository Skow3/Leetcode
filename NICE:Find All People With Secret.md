# 2092
HARD

This question's solution striked my mind in the start 5 mins after submitting my solution i got that there is some major thing to be handled


## Solution 1 :
```PYTHON
class Solution(object):
    def findAllPeople(self, n, meetings, firstPerson):
        """
        :type n: int
        :type meetings: List[List[int]]
        :type firstPerson: int
        :rtype: List[int]
        """
        for i in meetings:
            a=i[0]
            i[0]=i[2]
            i[2]=a
        meetings.sort()
        t= [-1]*n
        t[0]=0
        t[firstPerson]=0
        for i in meetings:
            a = i[2]
            b= i[1]
            current_t = i[0]
            if t[a]==-1 and t[b]==-1:
                continue
            if t[a]!=-1 and t[b]!=-1:
                continue
            else:
                if t[a]!=-1 and t[a]<=current_t:
                    t[b]= current_t
                elif t[b]!=-1 and t[b]<=current_t:
                    t[a]= current_t
        ans=[]
        for i in range(len(t)):
            if t[i]!=-1:
                ans.append(i)
        return ans
```

THIS PASSED 47/57 Testcases
i.e those testcases which didn't had any colliding Timestamp and simulatenous sharing


SO
# FINAL SOLUTION 
```PYTHON
class Solution(object):
    def findAllPeople(self, n, meetings, firstPerson):
        for i in meetings:
            a = i[0]
            i[0] = i[2]
            i[2] = a
        meetings.sort()
        t = [-1] * n
        t[0] = 0
        t[firstPerson] = 0
        i = 0
        while i < len(meetings):
            current_t = meetings[i][0]
            temp = {}
            while i < len(meetings) and meetings[i][0] == current_t:
                a = meetings[i][2]
                b = meetings[i][1]
                temp.setdefault(a, []).append(b)
                temp.setdefault(b, []).append(a)
                i += 1
            stack = []
            visited = set()
            for p in temp:
                if t[p] != -1 and t[p] <= current_t:
                    stack.append(p)
                    visited.add(p)
            while stack:
                x = stack.pop()
                for y in temp[x]:
                    if y not in visited:
                        visited.add(y)
                        stack.append(y)
            for p in visited:
                t[p] = current_t

        ans = []
        for i in range(len(t)):
            if t[i] != -1:
                ans.append(i)

        return ans
```

### How i solved it :
* Meetings are now processed grouped by time. For each time group:
* All connections are built first.
* Secret propagation is performed using DFS/BFS only within that time group.
The knowledge array (t) is updated after finishing the group, preventing premature spread.


It was having a TOC mlogm
IT BEATED 64% .. TIME AND 86% SPACE
