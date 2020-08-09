# 一、 LeetCode三个题目  

## Leetcode 151. 翻转字符串里的单词
```js
class Solution:
    def reverseWords(self, s: str) -> str:
        return " ".join([i for i in s.strip().split(' ') if i][::-1])
```	
```js
#testcase  
在leetcode测试通过  
输入："the sky is blue"
输出："blue is sky the"
期望结果："blue is sky the"
```

## Leetcode 205. 同构字符串
```js
class Solution:
    def isIsomorphic(self, s: str, t: str) -> bool:
        return [*map(s.index, s)] == [*map(t.index, t)]
```
```js
#testcase  
在leetcode测试通过  
输入："egg"
      "add"
输出：true
期望结果：true
```

## Leetcode 5. 最长回文子串
```js
class Solution:
    def longestPalindrome(self, s: str) -> str:
        for length in range(len(s), -1, -1):
            for index in range(0, len(s) - length + 1):
                sub_string = s[index:length + index]
                if sub_string == sub_string[::-1]:
                    return sub_string
```
```js
#testcase  
在leetcode测试通过  
输入："babad"
输出："bab"
期望结果："bab"
```
