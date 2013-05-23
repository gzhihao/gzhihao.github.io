---
layout: post
title: "看板(Kanban)简记"
date: 2012-06-04 18:05
comments: true
categories: 
- Kanban
- Agile
---

读过《看板和Scrum—相得益彰》([中文版](http://www.infoq.com/cn/minibooks/kanban-scrum-minibook-cn) [英文版](http://www.infoq.com/cn/minibooks/kanban-scrum-minibook-cn))，简单记录一下

# 什么是看板
看板最早起源于丰田，是其推动精益和持续改善的有效工具。

一般而言，想提高做事效率，最有效的方式是让工作的各个环节流动平滑起来，消除瓶颈和减少等待时间。基于这个出发点，看板只规定两件事：1) 工作流必须可见，2) 控制"在制品"(Work In Progress) 上限，并在此基础上 3) 优化流程，缩短生产周期并使其可预测。以上三点是看板的精髓。

## 1)工作流可见
任务拆分：将项目拆分成一系列小而具体的可交付的任务。

标识工作流程：在白板（看板图）上画出任务从开始到完成需要经历的阶段。

用卡片表示任务：随着工作的开展，卡片会从左至右流动，直至完成。

![kanban](http://ww3.sinaimg.cn/mw600/6d54b5a8jw1dthene9pcvj.jpg)

看板图直观地反映了工作的进度。当进度出现问题的时候，很容易暴露出来。

## 2） 控制"在制品"
在看板列中设置卡片数量上限（上图红色数字），当卡片数达到了列设置上限就不能再为该列添加新的卡片。如果这时有人手头上没有任务，他/她可以

- 领取下游没有到达上限的列的任务。例如上图的Dev列的限制是3，而这时只有两个任务正处开发状态，可以领取Todo列的任务进行开发
- 帮助其他人解决问题。例如Test列已达到上限，如果不尽快完成Test任务，会导致Dev任务排队等待测试，造成瓶颈，阻塞整体进度。
列中设置的上限就是限制“在制品"，由于引入了这个限制，迫使大家优先解决阻塞和瓶颈问题，减少等待的时间。

## 3) 优化流程和缩短生产周期
看板每列（最后一列除外）都可以设置上限。“上限该设多少”在一开始并不重要，随着团队的运作，可以根据实际的运作情况进行调整优化。
通过一些指标（如生产周期，不同工作类型的生产率等）和图可以发现瓶颈，分析不均衡生产，超负荷问题。

# 看板与Scrum的比较
书中对看板与Scrum做了非常详细的对比

- 看板没有规定任何角色；而Scrum规定了三种角色（Product owner，Scrum master，team）
- 看板没有固定迭代周期，生产周期是事后度量出来的；Scrum有固定迭代周期，而且迭代内有非常明确的节奏：计划，过程，发布。
- 看板通过流程状态来限制在制品；Scrum通过固定时长（Timebox）来限制在制品，即一个迭代内能做多少是有限制的。
- 看板图对应的是流程，不一定对应一个团队；Scrum则只属于某个团队（当然其他人也可见）。
- 看板对工作估算没有明确规定；Scrum规定了任务估算和生产率（Velocity)。
- 看板没有要求图表（但也可以使用，如累积流图）；Scrum会使用燃尽图跟踪迭代进度。

另外Scrum中要求的计划会议，站立会议，回顾会议，在看板中都没有定义。总体来看，看板相比Scrum，约束更小。

# 总结
就开发而言，看板适合于周期不确定，或者同时管理周期不一致的任务，例如Bug fixing，Customer support，Operation support 等等；而Scrum更适合于有固定周期的工作，例如产品开发
看板非常灵活，在不同的应用场景下可以有不同的配置，实践中可以参考[10 kanban boards and their context](http://dl.dropbox.com/u/1638038/publikationer/10%20kanban%20boards%20and%20their%20context/10%20different%20kanban%20boards%20and%20their%20context%20-%20mskarin.pdf)

另外，也可以考虑在Scrum中加入看板元素，最直接的就是为状态列设置上限。例如，迭代初期团队往往只关注开发，到后期可能由于环境和人手的问题无法顺利进行测试，所有功能都在等待排队测试。这时候如果在测试列和Checkout列设置上限，问题就会很容易被发现，团队也会自发地优先解决阻塞问题。

除了用在团队开发，也有研究将它应用在个人任务管理，如[Personal Kaban](http://www.personalkanban.com/pk/personal-kanban-101/)。我们可以试试给自己个人“在制品”也设置一个上限。

如果对看板感兴趣，可以试试这两个工具：

* [KanbanFlow](http://kanbanflow.com/)：简单易用，我之前简单介绍过，目前只有web版
* [Trello](https://trello.com/)： @LeoLiang_艳阳天 推荐，Fog Creek出品，功能强大，定制灵活。有Web版和iOS客户端

# 参考链接
* 电子书下载 [中文版](http://www.infoq.com/cn/minibooks/kanban-scrum-minibook-cn) [英文版](http://www.infoq.com/cn/minibooks/kanban-scrum-minibook-cn)
* [Crisp (一间看板咨询公司)](http://www.crisp.se/kanban)
* [10 kanban boards and their context](http://dl.dropbox.com/u/1638038/publikationer/10%20kanban%20boards%20and%20their%20context/10%20different%20kanban%20boards%20and%20their%20context%20-%20mskarin.pdf)
* [Personal Kaban](http://www.personalkanban.com/pk/personal-kanban-101/)