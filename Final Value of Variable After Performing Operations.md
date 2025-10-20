# EASY 

TODAY IS DIWALI AND 2 MONTHS LEFT FOR THIS YEAR ... I'LL TRY TO LEARN AND MAKE MORE AND MORE LIKE AS MUCH AS I CAN

* This question was easy-peasy i think lt gave it as an diwali question

# Approach 1:
```python
class Solution(object):
    def finalValueAfterOperations(self, operations):
        """
        :type operations: List[str]
        :rtype: int
        """
        x=0
        for i in operations:
            if i =="++X" or i=="X++":
                x+=1

            else:
                x-=1
        return x
```
But that gave just top 5%

Now 
# Approach 2:
```python
class Solution(object):
    def finalValueAfterOperations(self, operations):
        return sum(1 if '+' in op else -1 for op in operations)

```

The lower bound for this ps will be O(n) because we need to iterate to the each element to make this.
