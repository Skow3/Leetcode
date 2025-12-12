# MEDIUM
3433

# PYTHON 
### 1 st Solution 
```python
class Solution(object):
    def countMentions(self, numberOfUsers, events):
        """
        :type numberOfUsers: int
        :type events: List[List[str]]
        :rtype: List[int]
        """
        c=0
        for i in events:
            if i[0]=="MESSAGE":
                if i[2]=="ALL":
                    c+=1
        print(c)
        x = [2]*numberOfUsers
        print(x)
        for i in events:
            if i[0]=="MESSAGE":
                if i[2]!="HERE" and i[2]!="ALL":
                    s=(i[2])
                    t= s.replace("id","")
                    f= t.split(" ")
                    for i in t:
                        if i!=" ":
                            i=int(i)
                            x[i]+=1
        return x

```


# SOLUTION 2
After few submissions in leetcode i rectfied some changes.
```python
class Solution(object):
    def countMentions(self, numberOfUsers, events):
        """
        :type numberOfUsers: int
        :type events: List[List[str]]
        :rtype: List[int]
        """
        #TIMELINE 
        Timeline = [0]*numberOfUsers
        for j in range(numberOfUsers):
            if events[j][0]=="OFFLINE":
                l = int(events[j][2])
                Timeline[l]= int(events[j][1]) + 60
        # for handling ALL:
        c=0
        for i in events:
            if i[0]=="MESSAGE":
                if i[2]=="ALL":
                    c+=1
        x = [c]*numberOfUsers
        for i in events:
            if i[0]=="MESSAGE":
                if i[2]=="HERE":
                    for k in range(numberOfUsers):
                        if Timeline[k]<= int(i[1]) or Timeline[k]-60 > int(i[1]):
                            x[k]+=1
        for i in events:
            if i[0]=="MESSAGE":
                if i[2]!="HERE" and i[2]!="ALL":
                    s=(i[2])
                    t= s.replace("id","")
                    f= t.split(" ")
                    for i in t:
                        if i!=" ":
                            i=int(i)
                            x[i]+=1
        return x
```


# FINAL SOLUTION:
Now the final rectified version which has 55% win on TC
The only thing i was missing was the sorting based on the timings and then doing it linearly.

```python
class Solution(object):
    def countMentions(self, numberOfUsers, events):
        """
        :type numberOfUsers: int
        :type events: List[List[str]]
        :rtype: List[int]
        """
        # CRITICAL FIX: Sort events by time. 
        # If times are equal, process "OFFLINE" (priority 0) before "MESSAGE" (priority 1)
        events.sort(key=lambda e: (int(e[1]), 0 if e[0] == "OFFLINE" else 1))

        # TIMELINE: Stores the time when a user comes back online. 
        # Initially 0 (everyone is online).
        Timeline = [0] * numberOfUsers
        
        # x: Stores the count of mentions
        x = [0] * numberOfUsers

        # Process events linearly
        for i in events:
            time = int(i[1])
            
            if i[0] == "OFFLINE":
                user_id = int(i[2])
                # Store the time they come back (current time + 60)
                Timeline[user_id] = time + 60
                
            elif i[0] == "MESSAGE":
                if i[2] == "ALL":
                    for k in range(numberOfUsers):
                        x[k] += 1
                        
                elif i[2] == "HERE":
                    for k in range(numberOfUsers):
                        # User is online if current time >= the time they come back
                        if time >= Timeline[k]:
                            x[k] += 1
                            
                else:
                    # Specific IDs logic
                    # Your original logic adjusted to work correctly:
                    s = i[2]
                    t = s.replace("id", "") # removes "id", leaves "0 1 2"
                    f = t.split(" ")        # splits into list ['0', '1', '2']
                    
                    for val in f:
                        if val: # safety check for empty strings
                            uid = int(val)
                            x[uid] += 1
                            
        return x
