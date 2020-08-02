# 一、 LeetCode二个题目  

## Leetcode 146 LRU缓存机制
```js
class LRUCache:
    def __init__(self, capacity: int):
        self.dic={}
        self.head=Node(None,None)
        self.tail=Node(None,None)
        self.head.next=self.tail
        self.tail.prev=self.head
        self.capacity=capacity

    def get(self, key: int) -> int:
        if not key in self.dic:
            return -1
        node=self.dic[key]
        self.delete(node)
        self.insert(node)
        return node.val      

    def put(self, key: int, value: int) -> None:
        if key in self.dic:
            node=self.dic[key]
            node.val=value
            self.delete(node)
            self.insert(node)
            return        
        if len(self.dic)==self.capacity:
            node=self.tail.prev
            self.delete(node)
            del self.dic[node.key]
        node=Node(key,value)
        self.dic[key]=node
        self.insert(node)
    
    def insert(self,node):
        node.next,node.prev=self.head.next,self.head
        temp=self.head.next
        self.head.next=node
        temp.prev=node

    def delete(self,node):
        node.prev.next,node.next.prev=node.next,node.prev
class Node:
    def __init__(self,key,val):
        self.key=key
        self.val=val
        self.next=None
        self.prev=None
```	
```js
#testcase  
在leetcode测试通过  
输入：["LRUCache","put","put","get","put","get","put","get","get","get"]
[[2],[1,1],[2,2],[1],[3,3],[2],[4,4],[1],[3],[4]]
输出：[null,null,null,1,null,-1,null,-1,3,4]
期望结果：[null,null,null,1,null,-1,null,-1,3,4]
```

## Leetcode 51 N皇后
```js
class Solution:
    def solveNQueens(self, n: int) -> List[List[str]]:
        res = []
        s = "." * n
        def backtrack(i, tmp,col,z_diagonal,f_diagonal):
            if i == n:
                res.append(tmp)
                return 
            for j in range(n):
                if j not in col and i + j not in  z_diagonal and i - j not in f_diagonal:
                    backtrack(i+1,tmp + [s[:j] + "Q" + s[j+1:]], col | {j}, z_diagonal |{i + j} , f_diagonal |{i - j}  ) 
            
        backtrack(0,[],set(),set(),set())    
        return res

```
```js
#testcase  
在leetcode测试通过  
输入：6
输出：
[[".Q....","...Q..",".....Q","Q.....","..Q...","....Q."],["..Q...",".....Q",".Q....","....Q.","Q.....","...Q.."],["...Q..","Q.....","....Q.",".Q....",".....Q","..Q..."],["....Q.","..Q...","Q.....",".....Q","...Q..",".Q...."]]
期望结果：
[[".Q....","...Q..",".....Q","Q.....","..Q...","....Q."],["..Q...",".....Q",".Q....","....Q.","Q.....","...Q.."],["...Q..","Q.....","....Q.",".Q....",".....Q","..Q..."],["....Q.","..Q...","Q.....",".....Q","...Q..",".Q...."]]
```
