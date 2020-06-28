# 一、 LeetCode二个题目  
## Leetcode 105. 从前序与中序遍历序列构造二叉树
```js
class Solution:
    def buildTree(self, preorder: List[int], inorder: List[int]) -> TreeNode:
        if not preorder or not inorder:  # 递归终止条件
            return
        root = TreeNode(preorder[0])  # 先序为“根左右”，所以根据preorder可以确定root
        idx = inorder.index(preorder[0])  # 中序为“左根右”，根据root可以划分出左右子树
        # 下面递归对root的左右子树求解
        root.left = self.buildTree(preorder[1:1 + idx], inorder[:idx])
        root.right = self.buildTree(preorder[1 + idx:], inorder[idx + 1:])
        return root
```
```js
#testcase  
在leetcode测试通过  
输入：前序二叉树[3,9,20,15,7]
中序二叉树[9,3,15,20,7]
输出：[3,9,20,null,null,15,7]
期望结果：[3,9,20,null,null,15,7]
```

## Leetcode 46. 全排列
```js
class Solution:
    def permute(self, nums: List[int]) -> List[List[int]]:
        if len(nums) <= 1:
            return [nums]
        visited = [False for _ in range(len(nums))]  # 记录那些元素已经访问
        res = []

        def dfs(numbers, result, cur, visit):
            if len(cur) == len(numbers):
                result.append(cur[:])  # 这里记得用cur[:]或拷贝
                return
            for i in range(len(numbers)):
                if visit[i]:  # 如果已经访问过某元素，直接跳过进下一个元素
                    continue
                cur.append(numbers[i])
                visit[i] = True  # 将访问过的元素标记
                dfs(numbers, result, cur, visit)
                cur.pop()  # 恢复到之前状态
                visit[i] = False  # 恢复到之前状态

        dfs(nums, res, [], visited)
        return res
```	
```js
#testcase  
在leetcode测试通过  
输入：[1,2,3]
输出：[[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
期望结果：[[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
```
