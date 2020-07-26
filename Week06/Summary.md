# 第六周 2020-7-13到2020-7-19号周总结：
>本周学习了动态规划，它是一种状态转移的过程(自底向上的递推公式) 
>1. 最优子结构opt[n]=best[opt[n-1],opt[n-2]...] 
>2. 存储中间状态opt[n] 
>3. 递推公式(状态转移方程)

>本周觉得学习--，所以目前的学习方法依然是：  
>1. 提问   
>2. 多看视频  

## 本周自己的想法和提问都放在小组的群里：贴出来作为自己的复盘

### 【2020.7.13】周一一问D26：
### 第五周考试的反思：
#### 【反思】
觉得 考试成绩很符合我真实的水平，除了最后一题编程题提交失败，还错了二题选择题，编程题提交失败是我写的速度和质量都不太好，后面还得勤多练习。
#### 【安慰】
考试成绩只能说明前段时间的努力成果，不能代表很多，只有自己才可以说明一切。

### 【2020.7.14】周二一问D27：
### 提问：
今天在看高清视频的时候，在想为什么在学校用2M的宽带可以看标清720p（分辨率1280*720）的电影，看1080p（分辨率1920*1080）的电影有些卡，
720p的每张图片的有720*1080*4B，大约3.5M的容量，3.5M大于2M，应该仅加载图片都是不能的，更别说还有音频和其他的广告弹框，视频的播放是怎么做到的，
这是第一个问题，这个与BitTorrent下载有关吗？BT里面是不是有复杂的算法，这是第二个问题，请教 助教和同学。
### 助教Bo的回复：
bt下载用的是p2p的传输协议，用类似于分布式传销的思想。每个电脑下载自己一部分的下载任务，具体的知识属于分布式架构的领域。

### 助教给互动题目：
leetcode 641:设计循环双端队列
### 思路：
助教 和 大家 ，觉得如果要设计循环双端队列：应该是循环的双端队列 可以用 数组+链表 实现，也可以用链表实现；但是题目中 循环双端队列的功能，
好像没有体现 循环的特点，用数组或者链表都可以实现 这些功能，助教和大伙是否同意

### 【2020.7.15】周三一问D28：
### 提问：
消息队列的应用数据结构是队列，消息队列应对的是高并发的情形，所以消息队列是中间层，缓存（cache）、索引也是中间层，对吗？它不属于操作系统和应用层，可以理解为操作系统和应用层的过渡层。
RLE算法与 最小二叉生成树都是压缩算法，它们的使用场景是什么？各自的优势在哪里？助教和大伙帮忙来解惑
### 助教Bo的回复：
并不完全对。消息队列工程里面远比普通的队列要复杂，比如kafka之类的，还需要考虑分布式的场景，分为不同的分区，主题以及消费组等等分布式的场景。中间层这个定义虽然不是完全准确，不过可以暂时这么理解，
是底层和上层的一层解耦和消峰的方案。
rle算法之前没接触过，查了一下，用一个表示块数的属性加上一个数据块代表原来连续的若干块数据，从而达到节省存储空间的目的。而生成树是通过二叉树和编码将字符串转换成二进制数串，
感觉压缩算法都是对原始字符串进行一定的规则编排，从而达到存储上面的节省空间的效果。
### 待探索：
还是没太懂 消息队列和RLE算法，后面找些资料，再来跟助教和同学 谈论
### 【2020.7.16】周四一问D29：
### 待完成的互动题目：
leetcode 641：设计循环双端队列
### 回复：
实现队列的功能，我仅用了python的list就可以实现，在调试时还有一个小问题，助教和同学 能帮我指出来吗？
python代码如下：
```js
class MyCircularDeque:

    def __init__(self, k: int):
        """
        Initialize your data structure here. Set the size of the deque to be k.
        """
        self.one_list=[ ]
        self.max=k
        

    def insertFront(self, value: int) -> bool:
        """
        Adds an item at the front of Deque. Return true if the operation is successful.
        """
        self.one_list.insert(0,value)
        if self.one_list[0]==value:
            print (self.one_list[0])
            return True

    def insertLast(self, value: int) -> bool:
        """
        Adds an item at the rear of Deque. Return true if the operation is successful.
        """
        self.one_list.append(value)
        if self.one_list[len(self.one_list)-1]==value:
            return True
    
    def deleteFront(self) -> bool:
        """
        Deletes an item from the front of Deque. Return true if the operation is successful.
        """
        #value=self.one_list[0]
        value=self.one_list.pop([0])
        if self.one_list[0]!=value:
            return True

    def deleteLast(self) -> bool:
        """
        Deletes an item from the rear of Deque. Return true if the operation is successful.
        """
        value=self.one_list.pop()
        if self.one_list[-1]!=value:
            return True
        
    def getFront(self) -> int:
        """
        Get the front item from the deque.
        """
        return self.one_list[0]

    def getRear(self) -> int:
        """
        Get the last item from the deque.
        """
        return self.one_list[-1]

    def isEmpty(self) -> bool:
        """
        Checks whether the circular deque is empty or not.
        """
        if len(self.one_list)==0:
            return True

    def isFull(self) -> bool:
        """
        Checks whether the circular deque is full or not.
        """
        if len(self.one_list)<=self.max:
            return True
```

### 【2020.7.17】周五一问D30：
### 提问：
盲目搜索算法包括 广度搜索算法 和 深度搜索算法，它们需要额外的空间 和 容易陷入局部循环影响效率，所以数据量很大时，会使用 启发式搜索算法，它具有智能型（添加额外信息），
这个跟机器学习具有智能型类似吗？

### 【2020.7.18】周六一问D31：
### 提问：
棋类中用到搜索算法，助教和同学，有谁研究过博弈树在象棋和围棋中的用法

### 总结 【2020.7.19】周日D32：
对本周学习的动态规划的总结，它是一种状态转移方程(自底向上的递推公式)，它具有 1.最优子结构opt[n]=best[opt[n-1],opt[n-2]...] 2.存储中间状态opt[n] 3.递推公式(状态转移方程),
它与递归,分治，贪心都是寻找重复性的子问题，动态规划具有最优子结构和保存中间状态的特征。
