# CS 2053M: 计算机系统 III

## Courseware

| Chapter | Lec | 内容 |
|---------|-----|------|
| Ch 1. Introduction | 00 | 课程介绍: instructor, grading, syllabus |
| | 01 | 核心概念概览: Memory, I/O, OS concepts |
| Ch 2. ILP | 02 | 指令级并行: pipelining, ILP basics |
| | 03 | 动态调度: Tomasulo's algorithm, hardware-based speculation |
| Ch 3. Memory Hierarchy | 04 | 内存层次结构: technology trends, four questions for cache designers |
| | 05 | Cache 设计: block placement, identification, replacement, write policy |
| | 06 | CPU 漏洞: Meltdown & Spectre (cache side-channel attacks) |
| | 07 | 内存系统性能: CPI, miss rate, miss penalty |
| Ch 4. Main Memory | 08 | 分段: logical address space, control flow protection |
| | 09 | 分页: hierarchical, hashed, inverted page tables; frame allocation |
| | 10 | 虚拟内存: page replacement algorithms, page table walk, multi-level page tables |
| | 11 | Linux 虚拟内存: flat memory, memory mapping |
| Ch 5. Mass Storage & IO | 12 | 大容量存储: disk structure, disk scheduling, I/O buses, performance |
| | 13 | IO 系统: FCFS, SSTF, SCAN, C-SCAN, LOOK; I/O hardware, kernel I/O subsystem |
| Ch 6. File System | 14 | 文件系统接口: file concept, access methods, protection |
| | 15 | 文件系统实现: FS layers, on-disk / in-memory structures, file operations |
| | 16 | 文件系统实践: pathnames, inodes, file descriptors, directories |
| Ch 7. OS Security | 17 | 安全与保护: evaluation criteria, access control, network security |
| Ch 8. DLP & TLP | 18 | DLP & TLP (上): SIMD, vector processors, Flynn's taxonomy |
| | 19 | DLP & TLP (下): MIMD, thread-level parallelism, from ILP to TLP |

## Lab

| Lab | 内容 |
|-----|------|
| Overview | TA 实验总体介绍 |
| 01 | 动态分支预测 |
| 02 | Cache 设计与实现 |
| 03 | (暂无) |
| 04 | 用户模式 (User Mode) |
| 05 | 缺页异常处理 & fork 机制 |

## 24-25 春夏期末卷分析

题型：15 选择 + 4 大题（共 70'）

### 选择题考点覆盖

| 考点 | 相关 Lec |
|------|----------|
| 流水线 Hazard (RAW / control) | lec-02 |
| 动态调度硬件: Reservation Station, ROB, Register Rename Table | lec-03 |
| Scoreboard vs Tomasulo 区别 | lec-03 |
| Cache 参数计算: 16KB, 64B block, 4-way SA 求 set 数 | lec-04, lec-05 |
| 直接映射 / 全相联 / 组相联 Miss Rate 比较 | lec-04, lec-05 |
| Cache 模拟: 写回+写分配, LRU 替换, Miss 计数 | lec-04, lec-05 |
| Vector Processors 概念判断 | lec-18 |
| CPI + Miss Rate + Miss Penalty 加速比计算 | lec-07 |
| SCAN 磁盘调度 | lec-13 |
| 页表 / 虚拟内存基本概念 | lec-09, lec-10 |
| RISC-V PTE 字段组成 | lec-09, lec-11 |
| LRU 页替换, Page Fault 计数 | lec-10 |

### 大题

| 题号 | 分值 | 考点 | 涉及 Lec |
|------|------|------|----------|
| 1 | 15' | Hardware-based Speculation: ROB 表格填写 (div/mul/add 三条指令的 issue/execute/WB/commit) | lec-03 |
| 2 | 15' | MSI Cache Coherence Protocol: write-back, snooping | ⚠️ 课件中未找到 |
| 3 | 20' | RISC-V Sv39 虚拟内存: page fault 触发时机与次数、三级页表 walk、地址翻译 0xc0000000→0xb000、segmentation vs paging 优劣 | lec-08, lec-09, lec-10, lec-11 |
| 4 | 20' | 文件系统: indexed allocation block 计算、最大文件 size、directory vs inode 存储内容、contiguous blocks I/O 性能 | lec-14, lec-15, lec-16 |

### 各 Lec 重要度

| Lec | 重要度 | 说明 |
|-----|--------|------|
| 00-01 | ★ | 不考 |
| 02 | ★★★ | 流水线 Hazard 概念 |
| 03 | ★★★★★ | Tomasulo, HW Speculation — 选择 2 道 + 大题 15' |
| 04 | ★★★★ | Cache 设计四问、映射方式 — 选择高频 |
| 05 | ★★★★ | Cache 替换/写策略 — 同上 |
| 06 | ★ | 不考 |
| 07 | ★★★ | CPI/Miss Rate/Miss Penalty 计算 |
| 08 | ★★ | 分段概念, 大题有一问涉及 |
| 09 | ★★★★★ | 页表、PTE、三级页表 — 选择 + 大题 20' |
| 10 | ★★★★★ | 页替换 (LRU)、Page Fault、虚拟内存 — 选择 + 大题 20' |
| 11 | ★★★ | Sv39 地址翻译 — 大题 |
| 12 | ★★ | 磁盘基础 |
| 13 | ★★★ | SCAN 磁盘调度 |
| 14 | ★★★ | 文件系统接口概念 |
| 15 | ★★★★★ | Indexed allocation, inode — 大题 20' |
| 16 | ★★★★ | Inode vs directory, 路径名 |
| 17 | ★ | 不考 |
| 18 | ★★★ | Vector Processors 概念; 可能与 MSI 有关联 |
| 19 | ★★ | 几乎未直接考到 |

> ⚠️ **注意**: MSI Cache Coherence Protocol (15') 在课件中未找到对应内容，实际课堂大概率讲了但课件没收录，需要自行补充。

## 5 天复习计划

每天约 4 节 lec，按主题分组，难度均匀分布。

### Day 1: ILP — 指令级并行

| Lec | 内容 | 重要度 |
|-----|------|--------|
| 00 | 课程介绍 | ★ |
| 01 | 核心概念概览 | ★ |
| 02 | 流水线, ILP 基础, Hazard | ★★★ |
| 03 | Tomasulo, Hardware-Based Speculation | ★★★★★ |

**重点**: Tomasulo 算法流程、ROB 表格的 issue/execute/WB/commit 时序。lec-00/01 快速过一遍就行。

**练习**: 画一遍 Tomasulo 的 reservation station + ROB 结构，模拟 2-3 条指令的流水。

### Day 2: Memory Hierarchy & Cache

| Lec | 内容 | 重要度 |
|-----|------|--------|
| 04 | 内存层次, Cache 设计四问 | ★★★★ |
| 05 | 映射方式、替换策略、写策略 | ★★★★ |
| 06 | Meltdown & Spectre | ★ |
| 07 | CPI, Miss Rate, Miss Penalty 计算 | ★★★ |

**重点**: 三种映射方式（DM/FA/SA）的 Miss Rate 比较、Cache 参数计算（set 数、tag/index/offset 划分）、LRU 模拟、加速比公式。

**练习**: 拿 16KB / 64B / 4-way SA 自己手算一遍，再用不同访问序列模拟 LRU 替换。

### Day 3: Main Memory & Virtual Memory（最硬核）

| Lec | 内容 | 重要度 |
|-----|------|--------|
| 08 | 分段, 逻辑地址空间 | ★★ |
| 09 | 分页, 页表结构 (分级/哈希/倒排) | ★★★★★ |
| 10 | 虚拟内存, 页替换, Page Fault | ★★★★★ |
| 11 | Linux 虚拟内存, Sv39 地址翻译 | ★★★ |

**重点**: 分级页表遍历、LRU 页替换 Page Fault 计数、RISC-V Sv39 三级页表 walk（虚拟地址 → 物理地址全过程）、segmentation vs paging 优劣比较。

8 **练习**: 用 0xc0000000 → 0xb000 类似的地址，手写完整的三级页表翻译过程。用题目中的引用串 (2,3,2,1,5,...) 练 LRU Page Fault 计数。

### Day 4: Mass Storage & File System

| Lec | 内容 | 重要度 |
|-----|------|--------|
| 12 | 磁盘结构, 磁盘调度 | ★★ |
| 13 | IO 系统, SCAN/C-SCAN/LOOK | ★★★ |
| 14 | 文件系统接口, 访问方法 | ★★★ |
| 15 | FS 实现, Inode, Indexed Allocation | ★★★★★ |

**重点**: 磁盘调度算法（SCAN 系列计算路程）、inode 结构、indexed allocation（给定字节数算需要几个 block）。

**练习**: 手算 indexed allocation 的 block 数量（70B / 2^20+2044B 等），画 inode 的直接/间接指针层级。

### Day 5: FS 实践 + DLP & TLP + 查漏补缺

| Lec | 内容 | 重要度 |
|-----|------|--------|
| 16 | Inode vs Directory, 路径名 | ★★★★ |
| 17 | OS Security | ★ |
| 18 | SIMD, Vector Processors, Flynn 分类 | ★★★ |
| 19 | MIMD, Thread-Level Parallelism | ★★ |

**重点**: directory 和 inode 分别存什么、Vector Processors 概念判断。lec-17 快速过。

**补漏**: MSI Cache Coherence Protocol（snooping + write-back），这部分课件里没有，需要自己找资料（搜 "MSI protocol cache coherence" 看一篇博客就够了）。

**总复习**: 回顾 Day 3 的 Sv39 页表 walk 和 Day 4 的 indexed allocation，这两道大题确保能独立做出来。

