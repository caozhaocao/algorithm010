# 一、 LeetCode三个题目  

## Leetcode 70 爬楼梯
```js
class Solution: #优化的内存空间的版本
    def climbStairs(self, n: int) -> int:
        if n<3:
            return n
        dp=[0]*n
        num1 = 1
        num2 = 2
        for i  in  range(2,n):
           dp[i]=num1+num2
           num1,num2=num2,dp[i] 
        return dp[n-1]
```	
```js
#testcase  
在leetcode测试通过  
输入：5
输出：8
期望结果：8
```

## Leetcode 120 三角形最小路径和
```js
class Solution:
    def minimumTotal(self, triangle: List[List[int]]) -> int:
        #print(len(triangle))

        for row in range(len(triangle)-2,-1,-1):
            for col in range(len(triangle[row])):
                triangle[row][col]+=min(triangle[row+1][col:col+2])
        return triangle[0][0]
```
```js
#testcase  
在leetcode测试通过  
输入：[[7],[3,4],[6,5,7],[4,1,8,3]]
输出：16
期望结果：16
```

## Leetcode 53 最大子序和
```js
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        middle_value=nums[0]
        max_value=nums[0]
        for i in range(1, len(nums)):
            middle_value = max(middle_value + nums[i], nums[i])
            max_value = max(middle_value, max_value)
        return max_value
```
```js
#testcase  
在leetcode测试通过  
输入：[-2,1,-3,4,-1,2,1,-5,4]
输出：6
期望结果：6
```


