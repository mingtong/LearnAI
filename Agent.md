## Agent

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

**rational agent** 指的是做正确的事的 agent，但是，怎么确定是否“正确”？
我们用 agent 的行为“产生的后果”衡量是否“正确”。
当 agent 进入环境后，会根据接收到的感知序列作出一序列行动，这些行动会让环境的状态发生变化，如果变化是我们想要的，则表示 agent 的行动挺好，“我们想要的”的概念由 **performance measure** 来获取，performance measure 评估 环境状态的变化序列。
注意我们说的是环境的状态，而不是 agent 的状态，如果我们以 agent 的行动来定义成功，那么 agent 只需要简单地自欺欺人，agent 就可以做到完美地  rational。人类 agent 实际上是臭名昭著的“酸葡萄”，在得不到某个东西之后认为他们不需要这个东西（比如诺贝尔奖）。
这里有一个通用的规则，最好根据我们在环境中真正想要的东西来设计 performance measures，而不是根据我们认为 agent 应该如何行动。

