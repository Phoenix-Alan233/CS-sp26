# ISEE 2026MZ: 信息理论

ZJU 信息与电子工程学院课程，围绕 Shannon 信息论的三个核心问题：信息的度量、无损压缩、信道传输。

## Courseware

| Lec | 内容 |
|-----|------|
| 01 | 绪论: 信息论发展史、Shannon 三大定理概览 |
| 02 | 信息的度量: entropy, conditional entropy, joint entropy, mutual information, differential entropy, Markov chain, data processing inequality |
| 03 | 无损压缩: Kraft inequality, uniquely decodable codes, prefix codes, Huffman coding, Shannon coding, typical sequences, source coding theorem |
| 04 | 信息的传输: channel capacity, channel coding theorem, AWGN channel |
| 05 | 有损压缩: rate-distortion theory, quantization |

## Homework

| # | 内容 |
|---|------|
| hw01 | 熵与互信息计算 |
| hw02 | 无损压缩与 Huffman/Shannon 编码 |
| hw03 | 信道容量与率失真 |

## Exam

| 文件 | 说明 |
|------|------|
| 2023-2024 春夏.pdf | 往年试卷 |
| 模拟卷.pdf | 模拟卷 |
| 信息理论模拟考.pdf | 模拟考 |
| 答案/ | 课后习题答案 (Ch 2-8) + 模拟卷选解 |

## Papers

信息论相关论文，覆盖经典与前沿：

| 论文 | 主题 |
|------|------|
| A Method for the Construction of Minimum-Redundancy Codes | Huffman 编码原始论文 (1952) |
| Shannon Information and Kolmogorov Complexity | Shannon 熵与 Kolmogorov 复杂度 |
| Algorithmic Information Theory and Kolmogorov Complexity | 算法信息论综述 |
| Information and Computation | 信息与计算交叉 |
| Information-theoretic Limits of Learning and Estimation | 学习的信​​息论界限 |
| Information Theory and Statistical Learning | 信息论与统计学习 |
| An Information-Theoretic Criterion for Efficient Data Synthesis | 数据合成的信息论准则 |
| From Entropy to Epiplexity | 从熵到困惑度 |
| LLMs as Noisy Channels | LLM 与噪声信道 |

## 2 天速通计划

信息理论核心就三个问题：不确定性怎么量？怎么压到最短？怎么可靠传过去？考试重点在 Part 1 和 Part 2。

### Day 1: 信息的度量 + 无损压缩

| Lec | 内容 | 优先级 |
|-----|------|--------|
| 01 | 绪论 | 快速过 |
| 02 | 熵、条件熵、联合熵、互信息、连续熵、马尔可夫链 | ★★★★★ |
| 03 | Kraft、唯一可译码、Huffman、Shannon 编码、典型列 | ★★★★★ |

**重点**: 链式公式 `H(X,Y)=H(X)+H(Y|X)` 是所有证明题的核心工具。互信息 `I(X;Y)=H(X)-H(X|Y)` 的四种等价写法要烂熟。微分熵 `h(aX)=h(X)+log|a|`、高斯最大熵定理。

**练习**: hw01 + hw02 + 模拟卷判断题 + 证明题 (Z=X+Y、确定性函数)。

### Day 2: 信道容量 + 有损压缩 + 刷卷

| Lec | 内容 | 优先级 |
|-----|------|--------|
| 04 | 信道容量、信道编码定理 | ★★★ |
| 05 | 有损压缩、率失真 | ★★ |

**重点**: lec-04/05 考试占比不大，理解概念即可。剩余时间直接刷 `模拟卷.pdf` 和 `2023-2024 春夏.pdf`。

**练习**: 模拟卷 8 道大题逐题过，判断题优先用反例排除，证明题优先套链式公式。

> **考前速记**: `H(X,Y)=H(X)+H(Y|X)`, `I(X;Y)=H(X)-H(X|Y)>=0`, `Y=f(X) => H(Y|X)=0`, `h(aX)=h(X)+log|a|`, `Kraft: sum D^{-n_i}<=1`, Huffman 最优, Shannon `l_i=ceil(-log p_i)`.
