# OS

在 阅读 一些资料后的 收获、碎碎的说一下、留个记录、因为现在脑子转天就容易忘、等之后再回来看、做个对比、

-----------------------------------------------
## Monolithic 

没有实际开发过OS、对结构上的优劣体会并不真切、

但从想象中 觉得 zircon的设计 更能获得接受

主流或者说、历史发展过程中、目前成熟的OS 是以 Unix/Linux Windows 为主的 Monolithic 宏内核结构、

为什么选择 这种 结构、直觉上感觉、就是当时的人们 自然而然的选择、一个native的想法、和初级抽象分为内核态和用户态、内核里放些什么、用户放些什么、初步一规划、就开始干了、

与现在的对比不同、感觉不太可能有详尽的对比分析、毕竟从0到1过程无法对比、

这种设计的产生依据、应该是当时的硬件条件、与需求、并且在当时获得了认可和成功、1出来了、并且能work、很新鲜研究分析、进行改进优化、

--------------------------------------------------
## 时代

时间发展、在不知不觉中、各行各业都在以不同速度发展、OS所依赖的事物、也在进行改变、而复杂度高的事物、就像质量大的物体一样、惯性大、难以轻易改变、因为所需能量庞大、对应到OS上、类似生态环境、会对OS的稳定、兼容、可靠等诸多方便有要求、这些都是替换的代价组成、这是面临的很客观的问题、无法由个人解决、所以陆陆续续多年来人们又从事到、linux中继续贡献优化、使其适应当时的环境、


同样也有人在对OS研究认为优化 不一定能根本解决 故有问题、该面临的迟早会到来、依据需求 吸收前人经验从结构上进行的新的尝试、对已经发现的问题 改进 呈现 比较满意的结果、


我都不太了解 但感觉是这样、每一个事物都具有其客观现实性、具体事物拥有其固有特性、只能说和不合适、不能说好不好、个人感觉需求因该是最为值得被讨论和确定的东西、定界、确定范围、范围内讨论、一一对应需求、才能对比衡量、

举个🌰🤏、就像人们常说的、[我不会为了写一个hello world 使用设计模式] 一样、

目前我认为、由人类进行创造的事物一般符合指数发展、依据是人类是可以举一反三的生物、所以大胆猜测、未来OS发展 长期来看、是朝着多极化发展去的、那么又根据需要适配需求、定制化开发OS很有前景、在之后积累经验足够、硬件大规模统一、市场OS种类繁多且老旧、又在会有人想去统一它、

未来可期

## 观念

这东西太主观、且不实用了、但作为指导思想、会从这些角度思考问题、我从阅读zircon资料中印证和迸发的一些想法、

OS 是一个系统 

依据材料构建自洽的闭环

参照 已知的 最大 的 完备 系统 ———— Universe 


面向 空间 

面向 时间 

时空具备 后 有了 稳定环境 

要面对 物质 

由物质 组成 多样性的 子系统

理论上可无限增长

在 OS 上 作类比 

对空间的抽象————可以是内存的VMO、可以是硬盘的文件、也还可以是NVMe、等各种能抽象的空间设备

对时间的抽象————时间中断提供特性、为事物提供时间属性、目前这个宇宙仅知道具有单向性、依据限度 可把事物抽象为一个过程、具有一个时间范围、大过程中套小过程、多个过程的并行、估计会在局部会形成一个树状结构、之后在并回到主线、


对物质的抽象————面向对象编成、结构化的抽象、物质的特征、状态、行为、

当一切基础条件存在后 开始交互 形成一个系统、新的情况出现

静态 存在 变成 动态交互

出现 新需求、目前觉得这些是伴随则系统出现特有出来的特征

需要有 沟通交互 、规章制度、等级权限

沟通 ———— 需要信息传递机制、使系统有机的动起来

权限 ———— 每类事运行时影响范围不同、相应的权限也不同

规则 ———— 事物运行遵行固定秩序

消息的传递 是必要的、却也涵盖太大、种类多样、比如一对一、一对多、多对多、多对一、实现方式 也多是多样、需要具体问题具体分析、比如 接口的方式、制定好协议进行沟通、可能适用 多对一、消息队列、可能适用一对一、更适用流信息传递、时间相关性、广播、观察者模式、适用于一对多、消息转发没准可能适用多对多、合理的输入、输入输出、使事务环环相扣、运行良好、  
就比如生活中的信息传递、对传递方式、对内容的有效、精确要求、

权限、应该是事物固有的特征、在于对一个事情规定职责范围的确定、赋予其对应权限、类似可读、可写、可访问、可执行、类比一个公司各个不同职业、不同人的职责权限就不一样、  
觉得关键更在于合理的设计和划分

秩序、也是系统最为显著的特性、使事物有序且稳定的进行、使用一种规则、使一类特定的事物、全部遵守、就会减小冲突、提高稳定、也不太可能全部解决冲突、所以也需要应急机制、综合的解决、程序的调度算法、中断系统、医院的排队、天体的运行、


## 设计

目前感觉 cpu 是这个世界上最复杂电子产品

而软件上 OS 则是 最复杂的 app

为什么这么认为 是 因为 这些东西的功能 设计之初的目的 是 为了 通用、

那就会可预见性的、要高度抽象、尽可能覆盖处理到所有能遇见的问题、

仅仅如此还不可以、人们还要要求 它 稳定、安全、高效等等、

所以 设计 出一个 满意的 os 非常困难、所以推测关键是因为 设计 很 困难 、每一步都很精细、也都很讲究、

那么为什么 设计  如此 困难 、 

盲猜、这需要时间的积累、对长久以来OS遇到的问题的整体的敏感性、和抽象性、需要对需求的感知的清晰性、需要对OS 固有特性的全面分析、与合理运用、需要有深度专业领域的见解、

最关键是体量庞大、即使上述能力具备、也不是当年的情况、目前也很难独立完成、要多个自己进行合作、这无疑几何倍数上升了难度、

总的说来就是 门槛高一些、变现难一些、很难在其中get到价值、除非有目的、不太会成为快节奏时代的首选.


## 实现

管中窥豹、得到的一些结论

任何一个系统是需要人为创造后存在的、那首先是个工程问题、工程的技能一个也少不了、且很重要

盖一个茅草屋 、盖一栋摩天商业大厦 和 盖一栋超现代化的别墅、对设计师、和工程师 要求都不同、

实施团队的差别在、设计和实现中还存在着或多或少的的损失、

就可以类比为 写个hello world 、写个 app 、写个OS、想象中和实现总差者一个debug


## 应该如何做呢

要具备足够 设计 能力 和 工程 能力

目前计算机的情况是 设计和施工大部分都一人作、好像还没见过、谁能设计好了、让别人去施工的、

所以要求 具备 设计 能力 和 工程 能力、二者都不可忽视、要掌握设计的所需特性和工程所需特性

初步的来说 

做一个设计 、要明确需求、清楚背景、有专业知识支撑、尤其要明确需求

工程上、对工具有足够掌握、不至于出现 、豆腐渣工程

测试验收、有高度细致的检验标准、可以满足等级的质量检验、

有幸接触过一些建筑领域内的东西、感觉确实可以类比作参考、建筑上的施工、标准确实及其细致、有清晰的步骤和规范、检验同样如此、工种区分、职责划分、可见一斑


## 得

注重 需求分析
 
提高 编成技能

如老师所说、要能坚持长期系统性的学习和成长、

暂把兴趣定为、实现一个、可定制化的OS为目标

在一定时间内、能 、解构分析 OS、对各个部件、有认知、超过玩具水平、触及的到工业水平、

----------------------------------------------------------------------
v.0.0.1 结稿、等待回来在看
