# MEDIUM 
865

I Liked this question... not that tough but i got to revise my depth finding recursive algorithm and also about LCA
i.e Least Common Ancestar

# SOLUTION
```python
# Definition for a binary tree node. # class TreeNode(object): # def __init__(self, val=0, left=None, right=None): # self.val = val # self.left = left # self.right = right
class Solution(object):
    def subtreeWithAllDeepest(self, root):
        """ :type root: Optional[TreeNode] 
                :rtype: Optional[TreeNode] 
        """
        s = {}
        self.maxd = 0

        def depth(curr, d):
            if not curr:
                return
            self.maxd = max(self.maxd, d)
            s[curr] = d
            depth(curr.left, d + 1)
            depth(curr.right, d + 1)

        depth(root, 0)

        def LCA(curr):
            if not curr:
                return None

            if s[curr] == self.maxd:
                return curr

            left = LCA(curr.left)
            right = LCA(curr.right)

            if left and right:
                return curr
            return left if left else right

        return LCA(root)

```
