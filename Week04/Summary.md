# 第四周 2020-6-29到2020-7-5号学习笔记
>本周觉得学习贪心，DFS，BFS，二分查找算法，各自的实用场景不同，1.贪心算法适合用在最小生成树和哈夫曼编码，以及不是最优和最精确的应用场景下；暴力算法和回溯，递归原理是不同的，暴力算法是当下最优，回溯可以回退，递归是最优且可以回退 2.DFS和BFS，DFS深度优先搜索，BFS广度优先搜索，二种算法可以同时应用在相同的问题中，那种算法最优呢，这应该是不同的问题需要使用不同的算法，可能DFS更好一点，可能DFS和BFS一样好 3.二分查找 它是有条件的，需要在部分有序的数组，才可以使用该算法，熟悉算法的相应问题以及算法的模板。
超哥的视频看一遍过几天会忘记的，需要多看视频深入理解三种算法的模板以及应用场景，所以目前的学习方法依然是：  
>1. 提问   
>2. 多看视频  

## 本周自己的想法和提问都放在小组的群里：贴出来作为自己的复盘

### 【2020.6.29】周一一问D16：
### 提问：
今天 再做leetcode22题 括号生成，可以参照答案写递归，自己用for循环 写，遍历3对括号，觉得至少要3个for循环，n对括号，n个for循环，这个时间复杂度太高了吧！助教Bo和同学有没有更好的循环方法
### 助教Bo的回复：
这道题并不推荐使用循环，因为是“所有情况”，循环是不太好处理的。
### 追问：  
好吧，觉得这道题for不好写， 得去看看牛人的方法，除了递归和for循环，助教有什么好想法 教教我呀
### 助教Bo的回复：
这类题型一般就是使用递归的，记住模板


### 【2020.6.30】周二一问D17：
### 提问：
问题一：今天 再做了leetcode70
方法三 斐波那契数列的通项公式Fn=...，这公式怎么得到了，谁能教我下怎么推导。
问题二：今天晚上后半段看了覃超老师的直播，在关于java hashmap中，有个选项是这样子的，如果超过了负载因子（默认0.75），则会重新resize一个原来长度二倍的hashmap，并且重新调用hash方法，里面有二个小问题，1.用到75%就要扩大容量，剩下的25%不用多浪费 2.如果经常扩容，复制hashmap的值到另一个hashmap中，不如改用其他的链表的数据结构再加一层hash，是不是可以解决扩容时，复制整个hashmap值的问题，助教和同学对此有什么看法
### 何嘉伟同学的回复问题一：  
https://baike.baidu.com/item/%E6%96%90%E6%B3%A2%E9%82%A3%E5%A5%91%E6%95%B0%E5%88%97/99145?fr=aladdin  
斐波那契数列 就是 后一项 是前两项之和，上面的链接有 斐波那契数列递推
### 追问： 
谢谢何同学，我数学基础不太好，还是没太看懂里面 通项公式的推导过程，比如里面有假设的条件，这些假设的条件是怎么来的，天上掉下来的，还是不太懂
你说的是对的，Fn是 斐波那契数列之和，这个公式怎么推到的，我搞不定
### 何嘉伟同学的回复问题二：
https://yikun.github.io/2015/04/01/Java-HashMap%E5%B7%A5%E4%BD%9C%E5%8E%9F%E7%90%86%E5%8F%8A%E5%AE%9E%E7%8E%B0/  
里面有解释
### 再追问：  
谢谢 何嘉伟，里面只回答了负载因子0.75，hashmap超过了0.75，扩展，第二个小问题，扩展的时候经常复制hashmap的数据，很费时间，怎么破
### 何嘉伟同学的回复问题二：
https://yikun.github.io/2015/04/01/Java-HashMap%E5%B7%A5%E4%BD%9C%E5%8E%9F%E7%90%86%E5%8F%8A%E5%AE%9E%E7%8E%B0/  
里面的第6点RESIZE的有具体的解释
### 助教Bo的回复：
rehash是很耗时间的，所以实际工程里面就是要尽量减少rehash的次数


### 【2020.7.1】周三一问D18：
### 提问：
问题一：昨天后半段看覃超老师直播，记得有个题是判断linked list是否有环，可以用快慢指针，也可以用hashmap遍历整个链表，是不是所花费的空间和时间复杂度都会很大，这个用hashmap方法是不是不够理想，助教和大家有什么看法
### 助教Bo的回复：
是的，就空间复杂度来说，快慢指针好很多

### 【2020.7.2】周四一问D19：
### dididada提问：
寻找旋转排序数组中的最小值与使用二分查找，寻找一半有序数组[4,5,6,7,0,1,2]中间无序的地方有什么不一样？
### 回复：
觉得 本质上没区别，有二个地方需要做下调整，1.一个是输出值，另一个是输出值对应的索引地址index；2.找最小值需要比较二次，第一个值、最后一个值、中间旋转地方的值，三个值需要比较二次寻找最小值；下面一个找旋转地址的地方，不需要比较，只要跟前面排序不一样就找到相应的位置


### 【2020.7.3】周五一问D20：
### 提问：
有二个问题请教助教和同学，问题一：牛顿迭代法里面有个常数，比如 leetcode 69题里的常数是le-6，这个常数哪里来的？
问题二：牛顿迭代法的时间复杂度是多少，怎么算呢 比如leetcode 69题
### 何嘉伟同学的回复问题一： 
牛顿迭代法里面有个常数，超哥课程有获得该常数的链接
### 助教Bo的回复问题二：
这个系数超哥视频里面有介绍，是一群大牛哥们做了很多实验得出来的。至于牛顿迭代法的复杂度是O(logx)，具体计算方式不用深入了解，有很多数学的原理在里面
### 疑问：
时间复杂度为什么是O（lgn），记忆觉得不太可靠，这个时间复杂度跟常数关联，如果常数不同，时间复杂度不是有变化吗？觉得时间复杂度是变量，比较难给一个具体的数值，只能判定变化的趋势
### 助教Bo的回复：  
牛顿法的时间复杂度严格数学推导十分复杂，一般面试不会涉及的，感兴趣可以网上google一下严格的复杂度数学推导公式


### 总结 【2020.7.5】周日D21：
本周觉得学习贪心，DFS，BFS，二分查找算法，各自的实用场景不同，1.贪心算法适合用在最小生成树和哈夫曼编码，以及不是最优和最精确的应用场景下；暴力算法和回溯，递归原理是不同的，暴力算法是当下最优，回溯可以回退，递归是最优且可以回退 2.DFS和BFS，DFS深度优先搜索，BFS广度优先搜索，二种算法可以同时应用在相同的问题中，比如：在我们的生活场景（家）中，寻找一个物件，深度优先搜索是在我们对物件有印象（大概知道物件在哪里），假如物体在某个抽屉中，从而先从房间的桌子开始寻找，然后到桌子的抽屉的寻找过程；广度有优先搜索是在不知道物件在哪里的情况下，先搜索各个房间，然后在各个房间的每个桌子中寻找，最后去每个桌子的抽屉中寻找，那DFS和BFS，那种算法最有呢，这应该是不同的问题需要使用不同的算法，可能DFS更好一点，可能DFS和BFS一样好 3.二分查找 它是有条件的，需要在部分有序的数组，才可以使用该算法。