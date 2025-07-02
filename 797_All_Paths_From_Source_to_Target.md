```python
class Solution:
    def allPathsSourceTarget(self, graph: List[List[int]]) -> List[List[int]]:
        ans=[]
        def dfs(i,path):
            if i==len(graph)-1:
                ans.append(path)
            for j in graph[i]:
                dfs(j,path+[j])
        dfs(0,[0])
        return ans
```