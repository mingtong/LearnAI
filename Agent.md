# Agent

**Agent** 是任何通过**sensor**感知其环境并通过**actuators**在此环境中作出行动的事物。
- 比如人agent：sensor 是眼睛，耳朵，以及其他器官，actuators 是手，腿，声道等。
- 比如机器人agent：sensor 是摄像头，红外线，actuators 是各种马达。

- 术语 **percept** 表示 agent 在任何时候感知到的输入信息。
- 术语 **percept sequence** 是 agent 的感知到的所有内容的完整历史。

#### Agent Function
总的来说，agent 行动的依据是到目前为止感知到的完整的感知序列，而不是任何没有感知到的东西。
agent 的行为 是通过**agent function** 描述的，而 agent function 将感知序列映射到行动上。
我们可以把描述任何一个 agent 的 agent function 想象成一张表，一列表示 agent 的感知序列，另一列表示做出的相应的行动，如果我们不定义边界，这张表是可以无限大，因为 agent 可以感知的东西有太多可在能性。
而如果 agent 对感知序列的行动是随机性的，那么我们可以对需要对每个感知序列实验多次，来查看每一种行动的概率，随机行动看起来很蠢，但实际上是可以做到很智能。

在内部，用于某个 agent 的 agent function 是用 **agent program** 实现的。
要区分这两个概念，agent function 是抽象的数学描述，而 agent program 是具体实现。

#### rational agent** 指的是做正确的事的 agent，但是，怎么确定是否“正确”？
我们用 agent 的行为“产生的后果”衡量是否“正确”。
当 agent 进入环境后，会根据接收到的感知序列作出一序列行动，这些行动会让环境的状态发生变化，如果变化是我们想要的，则表示 agent 的行动挺好，“我们想要的”的概念由 **performance measure** 来获取，performance measure 评估 环境状态的变化序列。
注意我们说的是环境的状态，而不是 agent 的状态，如果我们以 agent 的行动来定义成功，那么 agent 只需要简单地自欺欺人，agent 就可以做到完美地  rational。人类 agent 实际上是臭名昭著的“酸葡萄”，在得不到某个东西之后认为他们不需要这个东西（比如诺贝尔奖）。
这里有一个通用的规则，最好根据我们在环境中真正想要的东西来设计 performance measures，而不是根据我们认为 agent 应该如何行动。

任何时候的 **rational** 取决于 4 件事:
• 定义成功的关键因素的 performance measure。
• agent 对于环境的预先了解。
• agent 可以执行的行动。
• agent 到目前为止的感知序列。

定义一个 rational agent：
对于每个可能感知序列，根据感知序列提供的证据以及agent 已知的信息，rational agent 应当选择可以最大化 performance measure 的行动。

注意区分 rationality 和 **omniscience**，一个“无所不知”的 agent 知道它的行动的实际后果，并相应地做出行动，但实际上“无所不知”在现实中是不可能的。
比如：我正准备过街去见一个朋友，几百米内都没有车，但当我过街时，一个飞机舱门从天而降，我还没来得及躲开的时候已经变成肉饼了，我过街的行为不合理吗？而我的墓碑上可能写着：“尝试过街的白痴”。

这说明 "rational" 与“完美”是不同的，"rational" 最大化期待的结果，而“完美“最大化实际的结果。
我们对"rational" 的定义不需要无所不知，因为"rational" 依赖于目前为止的感知序列。

为了修正之后的感知而做出的行动叫做 **information gathering**，比如过做出马路的 action 之前要先查看路况。
rational agent 不仅需要 information gathering，还需要尽可能地从感知中 **learn** 经验，以便修正其未来的感知。
依赖于之前的知识，而不是它的感知的 agent，我们称之缺少 **autonomy**，rational agent 应当是有自主能力的，通过学习来补偿不正确的之前的知识。比如扫地机器人应当在学习后能够预知哪里可能会是脏的，针对性地做出行动，而在没有经验之前，它的行为就是随机的，当学习了足够的经验后，agent 的行为就会变得有效，且不依赖于之前的知识。所以，具有学习能力的 agent 才能够应付复杂的场景。

了解了 rational 之后，我们就可以设计 agent 了。
设计一个 agent 之前，我们要先指定好 4大项 PEAS (Performance, Environment, Actuators, Sensors)。
比如一个自动驾驶出租车的 agent，我们的 PEAS 是这样的：

![这里写图片描述](http://img.blog.csdn.net/20170301105203741?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvY3VpdA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

 - Performance 的衡量包括：能够到达正确的目的地、最小化油耗和磨损、最小化时间或成本，最小化违章和对其他司机的干扰、最大化安全和对乘客的舒适度、最大化利润。很显然，这些目标是有冲突的，所以需要权衡。
 - Environment：各种路况，从农村小路到城市道路再到12车道高速，路上会有行人、动物，警车，路障，泥水，路陷。还要与潜在的和现有的乘客交互。另外还有雨雪天气，以及左舵右舵的可能性。显然，环境限制的越严格，则越简单。
 - Actuators：加速，转向，刹车，与乘客聊天（语言识别和发音），或者与其他车辆交流（打喇叭）。
 - Sensors：摄像头看路，红外或声纳判断与他车或障碍物的距离，计速器防止超速罚单以及弯道减速，探测车部的引擎表油表电表，GPS导航，键盘或麦克风让用户输入目的地。

下面是环境的各种属性：

**Fully observable** vs. **partially observable** vs **unobservable**：当 agent 可以感知所有环境时我们称这为完全可见。而有些 Sensors 可能不准确或者不可用时，我们称之为部分可见，当所有sensor都不可用时，我们称之为 完全不可见。

**Single agent** vs. **multiagent**：比如，自己解题的 agent 是 Single agent 环境，而两个下象棋的 agent 是 multiagent 环境，在象棋的两个对手agent中，他们是 **竞争** 的环境，而开车的多个 agent 则是 **合作** 的环境，在竞争环境中，随机行为是合理的，因为可以避免可预测性的陷阱（pitfalls of predictability）。

**Deterministic** vs. **stochastic**：当环境的下一个状态是由当前的状态以及 agent 要执行的 action 决定的，我们说它是 Deterministic，否则，说它是 stochastic。在一个“完全可见的”，且“Deterministic”环境中，agent 不需要担心不确定的东西。比如在游戏中，agent 是 Deterministic，即使它不能预测其他玩家的行动。而在现实中，形势太复杂，我们必须得看作是 stochastic，因为我们不可能知道所有不可见的因素。，如果一个环境不是完全可见的，或者不是 确定性的，我们说它是 uncertain。 “stochastic”一般来说意味着后果的不确定性在概率上是可以量化的。**nondeterministic**的环境是指 action 以它们可能的后果为特点，但是没有概率属性。nondeterministic 的环境通常用于描述衡量 	performace 时 agent 达到 action 的所有可能的后果。

**Episodic**（偶发的） vs. **sequential**（串行的，与parallel相反）：在偶发的环境中，agent 的经验被划分成原子事件，在每个事件中，agent 接收到感知，而后执行一个单独的 action，关键的是，下一个事件不依赖于上一个事件的 action。很多类别的任务都是偶发的。比如一个 agent 的决定是要找出组装流水线上有问题的部件，而不考虑前一个部件，也不影响下一个部件。在连续的环境中，当前的决定可能影响所有未来的决定，比如下象棋时的步骤决定。偶发的要简单的多，因为不需要考虑之前。

**Static** vs. **dynamic**：如果一个环境会在 agent 正在考虑时变化，我们称之为 动态的，否则是 静态的。静态的环境很容易处理，因为 agent 做决定时不需要持续观察整个世界，也不需要考虑时间的推移。而动态的环境会持续询问 agent 想要做什么，如果此时还没有决定，则认为决定什么都不做。如果环境不随着时间变化，但是agent 的 performance（目标） 随着时间变化，我们说它是 **semidynamic**。自动驾驶的agent是动态的，因为其他车和自己都一直在移动，而驾驶算法决定下一步要做什么。限时的象棋agent是半自动的。而不限时的解题agent是静态的。

**Discrete**（离散的） vs. **continuous**（连续的）：离散/连续 的区别适用于环境的状态、处理时间的方式、以及agent 的感知和行动。比如，象棋的环境有一个有限数量的不同状态，象棋还有一个离散的感知和行动。自动驾驶是一个“连续状态”、“连续时间”的问题：车的速度和位置的值的变化是平滑的，而驾驶行动也是连续的，比如转向多少度。

**Known** vs. **unknown**：严格来说，这个区别不适用于环境本身，而用于 agent 的关于环境的“物理定律”的知识的状态。在已知的环境中，所有 action 的后果（或者随机环境下后果的概率）都给出了。显然，如果环境是未知的，agent 需要学习如何制定好的决策。注意 Known 与 unknown 的区别与 可见/部分可见 是不同的，因为已知的环境也可能是部分可见的，比如纸牌游戏，agent 知道规则，但是看不见下一张是什么牌。而未知的环境可以是完全可见的，新的电视游戏中，屏幕上显示整个游戏但是不知道按下按钮会发生什么。

所以，最麻烦的就是 **partially observable**, **multiagent**, **stochastic**, **sequential**, **dynamic**, **continuous**, 以及 **unknown**，自动驾驶全属于这些情况。


AI 的任务是设计一个实现了 “agent 功能”的 “agent 程序”，它的目的是做“感知”到“行动”的映射关系。假设这个程序运行在某些具有物理感应器和行动器的计算设备上，我们称之为 **architecture**：
**agent = architecture + program**

显然，我们选择的 program 要适合这个 architecture ，如果 program 的行动是行走，那么 architecture 得有腿。architecture 可以是普通PC，或者一个有计算功能、感应器，摄像头的机器车。一般来说，architecture 让感应器的感知对 program 可用，然后运行 program，然后取出 program 的 action 到 actuators。

agent programs 的骨架基本相同：从sensor取得当前感知作为输入，返回 action 到 actuator。
还有**coroutines**的agent program，在环境中异步运行，每个coroutine都有一个输入和输出端口和一个循环，这个循环从输入端口读取感知然后向输出端口写入action。

“agent program”与“agent function”的不同是“agent program”只取当前的感知，而“agent function”取得整个感知历史。“agent program”只取当前的感知作为输入的原因是当前环境中也没有更多了。如果”agent function”需要依赖于整个感知序列，则需要记录感知。

这里有4种基本的agent program种类，体现了几乎所有智能系统的底层原理：

 - 简单的反射agent
 - 基于模型的 反射agent
 - 基于目标的agent
 - 基于实用性的质量的agent

**简单的反射agent**
![这里写图片描述](https://upload.wikimedia.org/wikipedia/commons/thumb/9/91/Simple_reflex_agent.png/408px-Simple_reflex_agent.png)
基于当前的感知选择action，而无所谓其余的感知历史。比如前面的车停了，我也停车，这种叫做 **condition–action rule**或者说 **if–then rules**，写作 **if** car-in-front-is-braking **then** initiate-braking。
这种agent只有在环境是完全可见的情况下才能成功。
在部分可见的环境中，无限循环通常是不可避免的，如果可以随机化agent的action，则可以跳出无限循环。

**基于模型的 反射agent**
![这里写图片描述](https://upload.wikimedia.org/wikipedia/commons/thumb/8/8d/Model_based_reflex_agent.png/408px-Model_based_reflex_agent.png)
可以用model-based reflex agent处理部分可见的环境。
agent应该维护一些**内部模型**，这些内部模型依赖于感知历史，以及当前状态的不可见方面的一些反映。感知历史与action在环境上的影响可以由内部模型决定，而后像简单反射agent那样选择一个action。

把问题打碎，内部状态并不需要是多方面的，只需要摄像头的上一帧画面，让agent可以探测什么时候车边上的两个红灯持续亮或同时熄灭。对于其他的驾驶任务，比如改变航道，agent需要持续关注其他车辆在哪。还有，agent需要持续关注车钥匙在哪，以便能把车启动。

随着时间变化更新内部状态的信息需要在agent program中有两种知识：1，需要有关环境如何独立于agent变化的信息。2，需要agent自己的行动如何影响环境的信息。

这种关于“世界如何运转”的信息叫做“这个世界的**model**”。使用这个model的agent叫做**model-based agent**。

**基于目标的agent** 
![这里写图片描述](https://upload.wikimedia.org/wikipedia/commons/thumb/4/4f/Model_based_goal_based_agent.png/408px-Model_based_goal_based_agent.png)
goal-based agent扩展了model-based agent的功能，goal信息描述了可取的情形，让agent在多个可能性中做出选择，选出那个能够到达目标状态的。涉及到AI的子领域：**搜索**和**规划**，以找到一个达到目标的action序列。

这种agent更灵活，因为支持其决定的知识是显式表示的，而且是可以修改的。

有时候知道当前的环境的状态也不能够决定要做什么，比如堵车时，车可以左转或右转，或直行，正确的决策取决于车要去哪里。换句话说，像当前的状态描述一样，agent需要一些**goal**信息，用于描述可取的情况，比如到乘客的终点。agent program 可以把它与model-based 反射agent组合起来选择action以完成目标。


**基于实用性的质量的agent**（utility based agent） utility == quality of useful 
![这里写图片描述](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d8/Model_based_utility_based.png/408px-Model_based_utility_based.png)
goal-based agent 只区分了 目标状态 和 非目标状态，其实可以定义某个特殊状态有多么可取的程度。这个程度可以通过utility function获取，而这个utility function将一个状态映射到状态的utility的程度上。

在大多数环境中，goal不能够生成高质量的行为。比如，很多个action序列可以到达目的地，但是有些更快，更安全，更便宜。goal只是单纯地划分“happy”或“unhappy”，而“happy”是不科学的，经济学家和计算机科学家使用**utility**代替。utility的意思是“实用性的质量”。

当goal有冲突时，只有部分可以达到（比如速度和安全），agent 的 utility function 会做权衡。
当所有goal都达不到时，agent 的 utility function 提供一种方式衡量goal成功的可能性，而不是goal的重要性。

一个 rational utility based agent 会选择能够最大化所期待的好的结果的action，也就是说，agent会根据每个结果的概率和utility权衡选择。utility based agent需要model并跟踪其环境，要做的足够好，涉及到perception, representation, reasoning, 和 learning。

**learning agent**

![这里写图片描述](http://img.blog.csdn.net/20170301180804895?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvY3VpdA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

learning agent 可以让agent在未知环境中运行，而且可以变得更有能力。

learning agent 可以分成4块：**learning element**，负责改进。**performance element**，负责选择外部的action。learning element 从 **critic** 获取action的反馈以便决定如何改进。**problem generator** 负责建议能够带来新的且有信息量的经验的action。

