# MEDIUM
2048

* Very easy in python if the person has the knowledge of typeconversion in python :
```python
class Solution:
    def finddic(self,s: str) -> dict:
        p = {}
        for i in s:
            if i in p:
                p[i]+=1
            else:
                p[i]=1
        return p

    def equate(self,d : dict)-> bool:
        for i in d:
            if int(i) != d[i]:
                return False
        return True

    def nextBeautifulNumber(self, n: int) -> int:
        p= n+1
        while True:
            if self.equate(self.finddic(str(p))):
                return p
            p+=1

```


# Now in C++ [ IMP ] 

```c++
class Solution {
public:
    unordered_map<char, int> finddic(const string &s) {
        unordered_map<char, int> freq;
        for (char c : s) {
            freq[c]++;
        }
        return freq;
    }

    bool equate(const unordered_map<char, int> &d) {
        for (auto &pair : d) {
            int digit = pair.first - '0';  // convert char to int
            int count = pair.second;
            if (digit != count)
                return false;
        }
        return true;
    }

    int nextBeautifulNumber(int n) {
        int num = n + 1;
        while (true) {
            string s = to_string(num);
            auto freq = finddic(s);
            if (equate(freq))
                return num;
            num++;
        }
    }
};
