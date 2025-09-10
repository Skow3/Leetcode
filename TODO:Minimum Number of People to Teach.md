# MEDIUM
1733

WILL EXPLAIN IT LATER THIS WEEK
```python
class Solution:
    def minimumTeachings(self, n, languages, friendships):
        """
        :type n: int
        :type languages: List[List[int]]
        :type friendships: List[List[int]]
        :rtype: int
        """
        sadUsers = set()

        for u, v in friendships:
            u -= 1  # converting to 0 based indexing 
            v -= 1

            langSet = set(languages[u])
            canTalk = False
            for lang in languages[v]:
                if lang in langSet:
                    canTalk = True
                    break

            if not canTalk:
                sadUsers.add(u)
                sadUsers.add(v)
        language = [0] * (n + 1)
        mostKnownLang = 0

        for user in sadUsers:
            for lang in languages[user]:
                language[lang] += 1
                if language[lang] > mostKnownLang:
                    mostKnownLang = language[lang]

        return len(sadUsers) - mostKnownLang


```
