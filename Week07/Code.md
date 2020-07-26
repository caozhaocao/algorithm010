# 一、 LeetCode二个题目  

## Leetcode 22 括号生成
```js
class Solution:
    def generateParenthesis(self, n: int) -> List[str]:
        #回溯法
        if n == 0:
            return ['']
        result = []
        for c in range(n):
            for left in self.generateParenthesis(c):
                for right in self.generateParenthesis(n-1-c):
                    result.append('({}){}'.format(left, right))
        return result
```	
```js
#testcase  
在leetcode测试通过  
输入：3
输出：["()()()","()(())","(())()","(()())","((()))"]
期望结果：["()()()","()(())","(())()","(()())","((()))"]
```

## Leetcode 547 朋友圈
```js
class Solution:
    def findCircleNum(self, M: List[List[int]]) -> int:
        #DFS
        N = len(M)
        count = 0
        visited = set()
        
        def dfs(i):
            for j in range(N):
                if M[i][j] and j not in visited:
                    visited.add(j)
                    dfs(j)
        
        for i in range(N):
            if  i not in visited:
                count += 1
                visited.add(i)
                dfs(i)
        
        return count 

```
```js
#testcase  
在leetcode测试通过  
输入：[[1,1,0],[1,1,0],[0,0,1]]
输出：2
期望结果：2
```
