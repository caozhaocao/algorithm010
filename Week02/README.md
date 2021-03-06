# 一、 LeetCode二个题目  
## Leetcode 1. 两数之和
```js
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        hashmap={}
        for ind,num in enumerate(nums):
            hashmap[num] = ind
        for i,num in enumerate(nums):
            j = hashmap.get(target - num)
            if j is not None and i!=j:
                return [i,j]
```
```js
#testcase  
在leetcode测试通过  
输入：List=[5,4,2,11,15]
target=6
输出：[1,2]
期望结果：[1,2]
```

## Leetcode 144. 二叉树的前序遍历
```js
class Solution:
    def preorderTraversal(self, root: TreeNode) -> List[int]:
        res = []
        def helper(root):
            if not root:
                return 
            res.append(root.val)
            helper(root.left)
            helper(root.right)
        helper(root)
        return res
```	
```js
#testcase  
在leetcode测试通过  
输入：[1,6,2,3]
输出：[1,6,3,2]
期望结果：[1,6,3,2]
```

# 二、第二周 2020-6-15到2020-6-21号学习笔记
>觉得学习算法，应该看二遍覃超老师的视频，获得一种感觉，然后豁然开朗的发现了哈希、二叉树、堆的设计思路和应用场景，所以目前的学习方法是：  
>1. 提问   
>2. 多看视频  

## 本周自己的想法和提问都放在小组的群里：贴出来作为自己的复盘

### 【2020.6.15】周一一问D1：
#### 提问1：
今天开始看了第二周的课程，有二个问题请教，第一个问题：发现优先队列使用堆的数据结构，那么 查询和插入、删除的时间复杂度都应该是O（lgn），看覃超老师的视频里面有说到插入的时间复杂度O（1），想问下助教优先队列的插入的时间复杂度怎么是O（1），
那不是插入的时候保持优先队列的有序性吗？如果不是插入的时候，那什么时候才做保持优先队列的有序性的操作呢，这个我有点理解不了，还有一个疑问： 优先队列通过什么来体现的，是通过数值的大小来赋予优先级别吗？比如vpi1，优先级数值是1；vpi2，优先级数值是2，
以此类推，vip越高，等级越高，优先级的数据也高，优先队列是这么应用的吗？
问题二：数据和链表不能同时顾及查找和插入、删除的时间复杂度最优，发现hash数据结构，可以满足查找、插入、删除的时间复杂度最小，是不是可以这么认为这是hash数据结构的优，还有 进行hash值计算的时间没有包含在代码的时间复杂度里面，
如果hash值计算量很小，计算时间很少，倒不影响，如果计算时间很大，代码的真正时间复杂度会不会受影响，请教bo助教和大家。

#### 解答1：
助教Bo的回复：    
问题一的解答;我的理解是基于二叉堆实现的优先队列，插入的时间复杂度是ologn的。你说的O1的可能是斐波那契堆那些比较高级实现的优先队列，具体可以看下相关的实现细节。优先队列定义的时候需要定义一个比较器，然后塞入的元素要能够使用这个比较器来进行比较，这个比较器是可以自己定义的。
优先队列只是一个概念和接口，底层有很多具体的实现的，优先队列有很多不同的底层实现，建议前期先掌握基于数组的二叉堆实现。
问题二的解答：如果hash函数复杂度很高，会影响的。但我们一般所谓的常数复杂度，是在hash已经计算好的情况下，就和链表一样，插入如果要获取到插入的位置，那也不是o1了

### 【2020.6.16】周二问D2：
#### 提问2：
助教bo，有二个问题请教：第一个问题：之前了解过goto，然而工作上没有用过，想问下，for/while循环，有没有用goto语句，如果没有，什么导致了for/while可以从头开始循环，还有为什么goto会造成程序的混乱，
只要不嵌套和叠加goto，不就不会有混乱吗？
第二个问题：为什么时间复杂度都是O（lgn），规定为2的对数，如果是三叉树（3阶b树），寻找有序的三叉树，时间复杂度不应该是O（lg3n），对数是3，为什么也可以写成2的对数呢，是因为可以把3的对数转换成2的对数吗？

#### 解答2：  
助教Bo的回复：  
1 goto在工程化代码和算法中都是不推荐使用的，会造成程序流程的混乱。所以不推荐也完全没有必要使用goto语句
2 算法复杂度分析中的logn的底数是由分治的复杂度决定的，如果是二分，底数就是2，三分底数就是3。无论底数是多少，log的渐进趋势都是一样的，即复杂度的增长趋势和数据处理的增长关系是一样的。所以一般就是用ologn代表复杂度就可以。
补充提问2：助教，助教，第一个问题的goto 里面有二个小问题的  
何嘉伟同学的回复：我记得goto这个语法 早在好几年前不就取消了吗  
再提问：是的，那么 for/while怎么做到了多次的 从上往下 遍历呢  
何嘉伟同学的回复：因为说是用goto影响到整体代码的逻辑性，会导致程序难于理解，阅读不是很友好  
助教Bo的回复：这个就有点底层了，C语言底层的for和while循环其实也是和goto类似，有跳转的逻辑，具体要看汇编层面的代码了。推荐你一篇文章，讲得比较深入，
https://www.cnblogs.com/yanlingyin/archive/2012/03/27/2419304.html   
总结：助教Bo辛苦了，文章一看就懂，高级语言把while/for封装好了，看不到细节，编译的机器代码又看不太懂。
程序一般是顺序执行，因为有了类似 goto的指令，所以代码可以做跳转，觉得其实类似加了 内存地址的标签，有了标签，怎么跳转都可以，问题又来了，加的内存地址的标签 所消耗的内存肯定不多，不然很耗内存资源。
之前听人说，电脑很笨，只能根据顺序来执行，程序有了跳转功能，灵活多了，还不需要重复写代码。

### 【2020.6.17】周三一问D3：  
#### 提问3：   
有问题找助教，请教二个问题，问题一：现在硬件性能是按照摩尔定律攀升，相对的价格还在下降，现在基本可以不用考虑 空间复杂度了，相同配置的硬件变得越来越实惠，以后硬件的性能肯定会变得更强了，所以按照长时间周期看，
学习算法降低时间复杂度和空间复杂度的必要性会越来越低，助教同意吗？我不是觉得学习算法和数据结构没用，相反这是考查程序员的功力，只是相对硬件的摩尔定律带来性能的提成，硬件成本的下降，算法相对性价比下降了。
第二个问题，以后 应该是AI的时代，发现我们算法的应用复杂性比 机器学习难很多，我想问的是，我们的算法课和机器学习的应用有重叠的地方吗？有兴趣就回答下

#### 解答3：  
助教Bo的回复：  
1 现在内存和cpu价格还是很高的，算法主要是优化内存的cpu的开销，在有限的资源里面，为啥不做得更好呢？便宜并不是不做性能优化的理由哈。  
2. 机器学习我不太懂哈，不过我的理解是机器学习更加偏统计数学的东西，工程上的使用都是封装好的算发包，比如线性回归，boosting算法等等，个人项目做下来感觉并没有什么重叠的。  

### 【2020.6.18】周四一问D4：  
#### 提问4：
今天早上和晚上，在京东和天猫上淘了好几个小时的商品，买商品 也是很辛苦的，比如 早上下单了 macbook pro，中午一看，坏了，颜色不对，想换颜色，客服让先退掉后下单，退单后，既然深圳没货；自己退单后，平台十几个小时也没给退好，
今天京东的访问量估计太大，退的单 系统一天都没完成，我觉得作为程序员，自己太笨了，都不会写个程序，自动下单，感觉自动化和AI这些代码，应该有人写好了，下次的电商活动，希望自己不用这么辛苦，还有 大伙6.18玩的开心吗？
今天 在京东 看到优惠券是有条件的，那些可以用，那些不能用， 问下 助教和 小伙伴们，这些不会是人工给每个商品加 相应优惠券的标签吧，这样每个商品和优惠券得打多少标签，怎么让这样标签不混乱，是在这些标签里再加个时间标签吗？
比如 昨天的6-18，今天只需要把昨天的6-18时间标签删除掉就可以了。

### 【2020.6.19】周五一问D5：  
#### 提问5：  
今天有二个问题是我对堆和二叉树的困惑，问题一：堆是不是可以理解为 变种的二叉树，对于堆我的理解是寻找到最大值和最小值的运用，每一次寻找最值的时间复杂度为O（lgn），除了找最值，堆这种数据结构还有其它的运用吗？问题二：
二叉树的前序、中序、后序遍历，前序遍历有dfs（深度优先搜索）的应用，中序遍历有bfs（广度优先搜索）的应用，那么后序遍历有哪些应用呢？助教和同学有兴趣的回复下。

#### 解答5：  
助教Bo的回复：  
第一个问题
堆不一定是有二叉树实现的，和二叉树比较像的是二叉堆，是一颗完全二叉树，所以可以用数组实现。堆在使用中寻找最值得复杂度是O（1）的，不然就不叫堆了。在工程中一般使用场景是优先对联以及寻找topK的值
第二个问题
前序中序后序遍历方式主要是针对DFS来说的，只是在二叉排序树中，中序遍历方式出来的串比较特殊，是一个有序队列。

### 【2020.6.20】周六一问D6：  
#### 提问6：  
今天看了 第二周的部门课程视频，感觉看每个牛人的算法思路都不一样，刚接触他们的解法是不好理解的，助教和同学有没有一种固定的模板，比如哪些题目用这个思路和数据结构，性能就比较好，不用性能最好，这样 一种思路就能解决一批题目，每个题目看牛人的思路，虽然很巧妙，下次忘记的概率也比较大，多刷几遍，会不会影响效率。
助教bo和同学们 有什么好建议。

#### 解答6：  
助教Bo的回复： 后面会有这个环节的，至于套路，其实超哥在视频中也介绍了不少了，特别是后期的递归以及动态规划，甚至都可以使用模板编程的方式来进行开发，先把套路模板写好，然后往里面填充就行了。举个例子，递归中，一般分为这几个套路1 递归终止条件 2递归传递 3 归去来兮，当前层的递归处理函数，又可以称之为清理现场。
这个可以自己在学习小结中慢慢总结。

### 【2020.6.20】周日总结D7：  
今天看老师的视频，把第二周的视频刷了二遍，有点感觉，明白了些哈希、二叉树、堆、图的底层设计思路和应用场景，以后的多看视频，温故而知新。

