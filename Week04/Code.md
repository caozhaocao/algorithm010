# 一、 LeetCode三个题目  

## Leetcode 33. 搜索旋转排序数组
```js
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        if nums==[ ]:
            return -1
        else:
            left,right=0,len(nums)-1
            while left <= right:
                mid=(left+right)//2
                mid=int(mid)
                if nums[mid]== target:
                    return mid
                elif nums[left] == target:
                    return left
                elif nums[right] == target:
                    return right
                if nums[mid] < nums[right]:
                    if nums[mid]<=target and target <= nums[right]:
                        left=mid+1
                    else:
                        right=mid
                else:
                    if nums[left]<target and target <= nums[mid]:
                        right=mid
                    else:
                        left=mid+1
            return -1
```	
```js
#testcase  
在leetcode测试通过  
输入：nums=[4,5,6,7,0,1,2]
target=0
输出：4
期望结果：4
```

## Leetcode 69. x 的平方根
```js
class Solution:
    def mySqrt(self, x: int) -> int:##二分查找
        left,right=0,x+1
        while left<=right:
            mid=(left+right)/2
            mid=int(mid)
            if mid**2 == x:
                return mid
            elif mid**2 > x:
                right=mid
            else:
                left=mid+1
            if left==right:
                return left-1
```
```js
#testcase  
在leetcode测试通过  
输入：6
输出：2
期望结果：2
```

## Leetcode 74. 搜索二维矩阵
```js
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:##暴力法
        for i in matrix:
            if target  in i:
                return True
        return False
```
```js
#testcase  
在leetcode测试通过  
输入：matrix=[[1,3,5,7],[10,11,16,20],[23,30,34,50]]
target=3
输出：True
期望结果：True
```


