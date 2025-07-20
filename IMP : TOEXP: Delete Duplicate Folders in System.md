# HARD
Important
1948

---

# THE STEPS I FOLLOWED TO SOLVE THIS PROBLEM:
1. **Understanding the Problem**: The task is to delete duplicate folders in a system, where folders are represented as lists of strings. Each folder can contain subfolders, and we need to ensure that only unique folders remain.
2. **Input Representation**: The input is a list of lists, where each inner list represents a folder path.
3. **Output Representation**: The output should be a list of unique folder paths, maintaining the order of their first appearance.
4. **Approach**:
    - Checking the subfolders of each folder.
    - Set frequency of each subfolder.
    - If a subfolder appears more than once, it is considered a duplicate.
    - parse the list to make it a trie.
    - populate the subfolder string in trie using inorder traversal.
    - Used identifier to check for the correct structure of the folder.
    - Used sorting to ensure correctness of order.
    - Then used recursion to find delete the duplicate folders.

---

### cpp solution MIK
```CPP
class Solution {
public:
    struct Node {
        string val; //name
        string subFolder; //subfolder structure
        unordered_map<string, Node*> children;
    };

    Node* getNode(string val) {
        Node* temp = new Node();
        temp->val = val;
        temp->subFolder = "";

        return temp;
    }

    void insert(Node* root, vector<string>& path) {
        for(auto& folder : path) {
            if(!root->children.count(folder)) {
                root->children[folder] = getNode(folder);
            }

            root = root->children[folder];
        }
    }

    string populateNodes(Node* root, unordered_map<string, int>& subFolderMap) {
        vector<pair<string, string>> subFolderPaths;

        for(auto &[childName, child] : root->children) {
            string subFolderResult = populateNodes(child, subFolderMap);
            subFolderPaths.push_back({childName, subFolderResult});
        }

        sort(begin(subFolderPaths), end(subFolderPaths));

        string completePath = "";//this is the subfolder of current root which we will form from children paths
        for(auto& [childName, childPath] : subFolderPaths) {
            completePath += "(" + childName + childPath + ")";
        }

        root->subFolder = completePath;

        if(!completePath.empty()) {
            subFolderMap[completePath]++;
        }

        return completePath;
    }

    void removeDuplicates(Node* root, unordered_map<string, int>& subFolderMap) {
        for(auto it = root->children.begin(); it != root->children.end(); ) {
            string childName = it->first;
            Node* child = it->second;

            if(!child->subFolder.empty() && subFolderMap[child->subFolder] > 1) {
                it = root->children.erase(it);
            } else {
                removeDuplicates(child, subFolderMap);
                it++;
            }
        }
    }

    void construstResult(Node* root, vector<string>& path, vector<vector<string>>& result) {
        for(auto& [childName, child] : root->children) {
            path.push_back(childName);
            result.push_back(path);
            construstResult(child, path, result);
            path.pop_back();
        }
    }

    vector<vector<string>> deleteDuplicateFolder(vector<vector<string>>& paths) {
        Node* root = getNode("/");

        //Construct trie
        for(auto& path : paths) {
            insert(root, path);
        }

        unordered_map<string, int> subFolderMap;
        populateNodes(root, subFolderMap);

        removeDuplicates(root, subFolderMap);

        vector<vector<string>> result;
        vector<string> path;
        construstResult(root, path, result);

        return result;


    }
};
```

# FINAL SOLUTION
```python
from collections import defaultdict
from typing import List

class Node:
    def __init__(self, val=""):
        self.val = val
        self.subFolder = ""
        self.children = {}

class Solution:
    def getNode(self, val: str) -> Node:
        return Node(val)

    def insert(self, root: Node, path: List[str]):
        for folder in path:
            if folder not in root.children:
                root.children[folder] = self.getNode(folder)
            root = root.children[folder]

    def populateNodes(self, root: Node, subFolderMap: dict) -> str:
        subFolderPaths = []

        for childName, child in root.children.items():
            subFolderResult = self.populateNodes(child, subFolderMap)
            subFolderPaths.append((childName, subFolderResult))

        subFolderPaths.sort()
        completePath = ""

        for childName, childPath in subFolderPaths:
            completePath += f"({childName}{childPath})"

        root.subFolder = completePath
        if completePath:
            subFolderMap[completePath] += 1

        return completePath

    def removeDuplicates(self, root: Node, subFolderMap: dict):
        to_delete = []
        for childName, child in root.children.items():
            if child.subFolder and subFolderMap[child.subFolder] > 1:
                to_delete.append(childName)
            else:
                self.removeDuplicates(child, subFolderMap)

        for childName in to_delete:
            del root.children[childName]

    def constructResult(self, root: Node, path: List[str], result: List[List[str]]):
        for childName, child in root.children.items():
            path.append(childName)
            result.append(path[:])
            self.constructResult(child, path, result)
            path.pop()

    def deleteDuplicateFolder(self, paths: List[List[str]]) -> List[List[str]]:
        root = self.getNode("/")

        for path in paths:
            self.insert(root, path)

        subFolderMap = defaultdict(int)
        self.populateNodes(root, subFolderMap)
        self.removeDuplicates(root, subFolderMap)

        result = []
        self.constructResult(root, [], result)
        return result
```

---

# NEW THINGS LEARNT :

#### Trie
A Trie (pronounced "try") is a special type of tree data structure used primarily to store and search strings efficiently — especially useful when you deal with prefixes.
📘 Definition:

A Trie is a prefix tree, where:
    Each node represents a character in a word.
    The root is typically empty or represents an empty string.
    Each path from the root to a node spells out a prefix or complete word.
    Words with common prefixes share the same path in the trie.

#### Auto datatype in C
In C++, the auto keyword is used for type inference, which means the compiler automatically deduces the type of a variable from its initializer.
Syntax:
```cpp
auto variable_name = value;
```
Example:
```cpp
auto x = 10;       // x is deduced to be int
auto y = 3.14;     // y is deduced to be double
auto name = "GPT"; // name is deduced to be const char*
```


