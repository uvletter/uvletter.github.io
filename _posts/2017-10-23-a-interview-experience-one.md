---
layout: post
title: 一次面试经历（上）
excerpt: "正好在回上海的高铁上，就将这几个星期的面试经历总结一下吧，也许以后哪天就会看到。"
modified: 2017-10-23 00:10:00 +08:00
categories: articles
tags: [面试, 随笔]
comments: true
share: true
---

正好在回上海的高铁上，就将这几个星期的面试经历总结一下吧，也许以后哪天就会看到。

实话说我的简历通过率有点低，好多公司没投上，甚至在BOSS直聘上连投简历的机会都没有，投过的公司大概有爱奇艺，豆瓣，饿了么，贝米钱包，坚果云，知乎，今日头条，最后只通过了3个，所以当初接到今日头条HR小姐姐的邀约还是有点小激动的，声音也很甜美，她一定不知道因为某个机缘巧合她已经成为某人的女神了。

下面聊一下面试的详细经过吧，可能记忆有偏差很多东西记不清了。

面的第一个公司是坚果云，在上海张江的一家做云存储的公司。规模不是很大，租了一栋写字楼的两间。面试我的是一个个子高大，光头，戴个帽子的人，感觉有一点腼腆，开始在外面撞见时他有意避开了我的目光，那时我正在找门牌。后来我回去百度了下，如果没猜错的话面试官应该就是坚果云CEO韩竹（哇还是第一次被CEO亲自面试，荣幸）。

面试的问题主要是就我的第一个项目TinyS，首先问了个select和epoll的区别，我答了文件描述符个数的限制和用户态内核态的内存拷贝两点，不过在最关键的工作模式上答的有点问题，我说epoll是在描述符上注册回调事件，这个没问题，但我说select是做轮询，依次遍历所有描述符，找出准备好的描述符。然后面试官诘问，你意思是select的时候系统一直在轮询描述符所以CPU会跑满？当时我顿住了，也没想出个所以然来，然后面试官说据我了解不是这样。回去查了下轮询是没问题的，但不会一直CPU轮询，轮询后没发现准备好的描述符会sleep，直到一个硬件中断唤醒才继续轮询。

然后还问了epoll的水平触发和边缘触发的区别（基本每场面试都会问到这一类的问题），事件驱动的服务器是水平触发还是边缘触发（我心里想的是这没关系吧，不过答了个更像的边缘触发，面试官好像点了点头表示满意），问了悲观锁和乐观锁的区别，还让我现场写一个CAS，不过我表示这代码是我几个月前写的记不清具体写法了（回去果断把代码又重新看了一遍！！），然后面试官表达了这个项目是不是我自己写的怀疑（汗-_-）。面试官还提了一个很重要的问题，关闭TCP连接的TIME_WAIT阶段代表什么。我之前只是知道TCP四次挥手，并没有深入了解这四次挥手背后的具体过程。然后面试官表示我的这个服务器肯定没投入到生产环境下使用（确实是，服务器的健壮性要打很大问号），也释疑了我为什么用ab测试服务器并发最多只能到1000。

接下来考了三道算法题，第一个问题是从一个序列中，找出和最大的连续子序列。当时一头钻进动态规划中，因为这确实是动态规划的应用场景，一直在想状态转移方程该如何表达，然后就没想到点子上。

第二个问题是从m个无序数组中，找出最大的k个数。我开始想了用快排mlogm复杂度，选择排序mk时间复杂度，如果数组范围很小且不重复，用位图m的时间复杂度，不过这些都不是面试官想要的答案。然后面试官提示我知道什么排序算法，我列举了一堆，然后面试官说你试着用堆排序，然后我开始想出把这m个元素创建一个最大堆，用m+klogm的时间复杂度可以找出最大k个数。面试官接着问有没有更好的方法，用一个更小的堆。然后我想了会儿，觉得可以用k个数建最小堆，让m个数入堆出堆，最后堆里留下的就是最大的k个数了，面试官这才满意地点点头。期间面试官还问我是不是计算机专业的（我不确定他这个问题的意图，是觉得我的能力应该是计算机专业的，还是单纯想求证我的专业）。

最后一个问题是手写一个二分查找，找到则返回索引，没找到返回-1。我写了个迭代的二分查找，写了几个测试用例，然后就通过了。

后面就大致问了下薪资期待，平时用不用Linux，工作地点啥的，就让我回去等结果了。

这次面试整体来说很偏底层，甚至和自己申请的python后端工程师关系不大，更像Linux开发工程师，回去后对这次面试结果还是很期待的，感觉自己算法答得还不错，但结果迟迟没收到邀约，嗯，有点小沮丧，对自信心影响很大，不过想了想可能前面的基础理论题答得比较差。

知道这些面试题是有套路的后，国庆回去怒刷了波面试题。

去知乎的面试是在国庆完后第一天，当天面了两轮，第一轮的面试官比较年轻，戴着个眼镜，看着就像大自己几届的学长。他主要问了一些基础知识（不得不说知乎每一轮面试目的很明确的，第一轮基础知识，第二轮系统设计，第三轮hr），开始问了我知道几种排序算法，快排时间复杂度多少，最坏时间复杂度多少，什么时候会退化成最坏情况，然后让我手写个一个算法将两个有序数组合并成一个有序数组，这个问题很简单，可以看作归并排序的一部分，我很快就写出了一个版本，面试官看了后表示程序跑起来没问题，但有个小问题，看我想不出来，他解释我在没明确提示的情况下改变了输入数组，这在函数调用时可能会有隐患（很细节）。然后面试官问了我哈希表的原理，以及处理哈希碰撞的拉链法是怎么回事。在纸上写了个列表表达式和生成器表达式，问我分别代表什么，什么场景下用前者什么场景下用后者，又让我手写一个装饰器在函数执行前后输出函数名。还有进程与线程的区别，python什么情况下用线程什么情况下用进程，协程又是什么，协程和线程的区别，为什么用协程，B+树索引的原理。最后问了我了不了解redis，知不知道redis的字典底层是怎么实现的，我说只是用过redis，底层具体实现细节还没有作探究，然后面试就结束了。在提问环节面试官也很有趣，在看我憋了半天蹦出句那我开门见山问了，他立马抢过话，让我别问薪资问题，问了我也不知道，还一边笑。可以知道的情况是知乎面试大概会面三轮，这和我网上了解到的情况一样，他不清楚我以后的岗位要做什么，因为第一轮面试不分部门。面试官本来是要我回去等结果的，我说明了自己是上海来的情况，他很爽快地表示现在去喊二面面试官，悬着的心一下放下来了。

总的来说，这次的面试经历很赞，面试官人长得帅，很好沟通，而且中间有互动，不像有的面试官，摆着副扑克脸，面试过程也是单向的，感觉自己像被审讯的犯人一样。

本文原作于2017年10月15号头条面试完回上海的高铁上。