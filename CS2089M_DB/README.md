# CS 2089M: 数据库系统

ZJU 大三数据库课，教材是 *Database System Concepts* 7th (Silberschatz)。上半学期讲模型和 SQL，下半学期讲 DBMS 内部实现。

## Courseware

| Lec | 内容 | 重要度 |
|-----|------|--------|
| 01 | 数据库系统概述: DBMS, data abstraction, data models, DB languages, system architecture | ★ |
| 02 | 关系模型: relations, tuples, candidate keys, foreign keys, integrity constraints, relational algebra (σ, π, ⋈, ∪, −, ρ) | ★★★★ |
| 03 | SQL: DDL, DML, SELECT, JOIN, subqueries, aggregation, GROUP BY | ★★★★★ |
| 04 | 高级 SQL: views, authorization, functions, procedures, triggers, embedded SQL, EXISTS | ★★★ |
| 05 | E-R 模型: entity, relationship, weak entity, cardinality constraints, E-R to relational schema | ★★★★★ |
| 06 | 关系数据库设计: functional dependency, closure, candidate keys, normal forms (1NF/2NF/3NF/BCNF), lossless decomposition, dependency preservation, canonical cover | ★★★★★ |
| 07 | (缺失) | — |
| 08 | 存储与文件结构: disk, pages, record organization, slotted-page structure, buffer pool | ★★★ |
| 09 | 索引与散列: ordered index, B+ tree insert/delete/draw, height estimation, static/dynamic hashing, index selection | ★★★★★ |
| 10 | 查询处理: query execution, selection algorithms, join algorithms (nested-loop, hash join, merge join), external sorting, cost estimation (transfer/seek) | ★★★★ |
| 11 | 查询优化: equivalence rules, execution plans, selectivity estimation, statistics, join ordering, cost-based optimizer | ★★★ |
| 12 | 事务: ACID, schedules, serializability (conflict-serializable), precedence graph drawing | ★★★★ |
| 13 | 并发控制: lock-based protocols, 2PL, strict 2PL, rigorous 2PL, deadlock detection/prevention (Wait-Die, Tree Protocol) | ★★★★★ |
| 14 | 恢复系统: failure classification, log-based recovery, WAL, checkpoint, ARIES (Analysis/Redo/Undo phases, CLR, DirtyPageTable, undo-list) | ★★★★★ |

### 重要度说明

| 星级 | Lec | 说明 |
|------|-----|------|
| ★★★★★ | 03, 05, 06, 09, 13, 14 | 年年考，大题主力 |
| ★★★★ | 02, 10, 12 | 年年考，常与临近 lec 合并出题 |
| ★★★ | 04, 08, 11 | 部分年份考，出题较浅 |
| ★ | 01 | 仅 quiz 1 考概念，期末不单独出题 |

## 历年卷考点频率

基于 2017-18、2018-19、2022-23、2024-25 四套期末卷 + 5 套 quiz 的综合分析：

| 考点 | 频率 | 典型题 | 分值范围 |
|------|------|--------|----------|
| **SQL 查询** (JOIN, GROUP BY, HAVING, subquery, EXISTS, ALL, set ops) | 必考 | 写 SQL、SQL 改关系代数、True/False 判断 SQL 正误 | 9--16 |
| **关系代数** (σ, π, ⋈, ×, ∪, −, ρ) | 必考 | SQL 转关系代数、代数表达式等价判断 | 3--6 |
| **E-R 图 + 转关系模式** | 必考 | 画 E-R 图、标主键外键、弱实体标识联系 | 9--16 |
| **函数依赖 & 范式** (闭包、候选键、正则覆盖、BCNF 分解、无损/依赖保持) | 必考 | 计算题 + 判断题 | 8--12 |
| **B⁺ 树** (插入/删除/画图、高度估算、节点数、seek/transfer) | 必考 | 画图题 + 计算题 | 12 |
| **Join 算法 & 代价** (hash join, merge join, nested-loop, external sort) | 高频 | 计算 seek/transfer、选择 build relation、递归分区判定 | 4--16 |
| **优先图 & 冲突可串行化** | 必考 | 画 precedence graph、判断 conflict-serializable | 3--5 |
| **2PL & 死锁** (strict/rigorous 2PL, Tree Protocol, Wait-Die, 死锁预防) | 高频 | True/False + 简答题 | 2--6 |
| **ARIES 恢复** (Analysis/Redo/Undo, CLR, 脏页表, undo-list, 最终值) | 必考 | 填表 + 推理 + 最终值 | 10--15 |
| **查询优化** (equivalence rules, selectivity, join ordering) | 中频 | 选择题 + 计算题 + True/False | 4--6 |
| **存储结构** (record layout, slotted page, disk characteristics) | 中频 | 计算题 + True/False | 4--6 |
| **Buffer Tree** | 低频 | 插入操作 + 节点修改计数 | 12（22-23 出现） |
| **XML / DTD / XQuery** | 仅 17-18、18-19 考过 | Path expression + XQuery | 12（近年不考） |

## 历年卷高频考题速查

| 考什么 | 参考卷子 / 题号 |
|--------|-----------------|
| SQL→关系代数互转（含自然连接陷阱） | 17-18 P1; 18-19 P1; 22-23 Q1-2; 24-25 P1 |
| E-R 图（外卖/电影/旅行/足球） | 17-18 P2; 18-19 P2; 22-23 Q4; 24-25 P2 |
| 候选键 + 正则覆盖 + BCNF | 17-18 P3; 18-19 P3; 22-23 Q3-4; 24-25 P3 |
| B⁺ 树增删画图 + 高度/节点计算 | 17-18 P5; 18-19 P5; quiz 4; 24-25 P5 |
| Hash join / merge join 代价 | 17-18 P6; 22-23 Q6; quiz 5; 24-25 P6 |
| Precedence graph + serializability | 17-18 P7; 22-23 Q5; 24-25 P8 |
| ARIES 完整流程（脏页表/undo-list/CLR/最终值） | 17-18 P8; quiz 5; 22-23 Q6; 24-25 P9 |
| 2PL / strict-2PL / deadlock / tree-protocol 判断题 | 22-23 Q6; 24-25 P8 |
| 查询优化 selectivity + equivalence | 24-25 P7 |

## Lab: MiniSQL

从头实现一个简易 DBMS，共 6 个模块：

| # | 模块 | 内容 |
|---|------|------|
| 0 | Overview | 项目总览、架构介绍 |
| 1 | Disk & Buffer Pool Manager | 磁盘管理、LRU 缓冲池 |
| 2 | Record Manager | 记录/元组管理 |
| 3 | Index Manager | B+ 树索引实现 |
| 4 | Catalog Manager | 元数据管理、系统表 |
| 5 | SQL Executor | SQL 解析与执行 |

附：`MiniSQL 实验指导书.doc` 是完整实验说明，`MiniSQL设计说明书样例.pdf` / `IndexManager报告样例.pdf` 是报告参考。

## 5 天复习计划

每天 3 节左右，上半部分偏概念和 SQL，下半部分偏系统实现。

### Day 1: 关系模型 & SQL 基础

| Lec | 内容 | 重要度 |
|-----|------|--------|
| 01 | 数据库系统概述: DBMS, data abstraction, data models, DB languages, system architecture | ★ |
| 02 | 关系模型: relations, tuples, candidate keys, foreign keys, integrity constraints, relational algebra (σ, π, ⋈, ∪, −, ρ) | ★★★★ |
| 03 | SQL: DDL, DML, SELECT, JOIN, subqueries, aggregation, GROUP BY | ★★★★★ |

**重点**: 关系代数运算（选择和投影 vs 连接的区别）、SQL 嵌套查询和聚合的执行顺序、SQL 与关系代数互转（特别关注自然连接与非同名属性连接的陷阱）。lec-01 快速过了解概念即可。

**练习**: 手写关系代数转 SQL 的题，确认 σ/π/⋈ 对应 SQL 的哪个子句。做 24-25 P1 的判断题练手。

### Day 2: 高级 SQL & 数据库设计

| Lec | 内容 | 重要度 |
|-----|------|--------|
| 04 | 高级 SQL: views, authorization, functions, procedures, triggers, embedded SQL, EXISTS | ★★★ |
| 05 | E-R 模型: entity, relationship, weak entity, cardinality constraints, E-R to relational schema | ★★★★★ |
| 06 | 关系数据库设计: functional dependency, closure, candidate keys, canonical cover, normal forms (1NF/2NF/3NF/BCNF), lossless decomposition, dependency preservation | ★★★★★ |

**重点**: E-R 图转关系模式（标主键/外键）、弱实体标识联系、函数依赖求闭包和候选键、正则覆盖计算步骤、BCNF 分解（是否无损、是否依赖保持）。lec-04 重点看 EXISTS/子查询。

**练习**: 给一个业务场景 → 画 E-R 图 → 转关系模式 → 检查范式。做 17-18 P2-3、18-19 P2-3。

### Day 3: 存储、索引 & 查询处理

| Lec | 内容 | 重要度 |
|-----|------|--------|
| 08 | 存储与文件结构: disk, pages, record organization, slotted-page structure, buffer pool | ★★★ |
| 09 | 索引与散列: ordered index, B+ tree insert/delete/draw, height estimation, index selection | ★★★★★ |
| 10 | 查询处理: query execution, selection algorithms, join algorithms (nested-loop, hash join, merge join), external sorting, cost estimation (transfer/seek) | ★★★★ |

**重点**: B⁺ 树的插入删除画图、高度估算公式（$h \le \lceil \log_{\lceil n/2 \rceil}(K) \rceil$）、hash join 代价计算（transfer = $3(b_r+b_s)$，seek 取决于缓冲区）、merge join 的排序 pass 数。lec-08 了解 slotted page 结构、记录布局计算。

**练习**: 手画 B⁺ 树的插入/删除过程（各做 2 轮），对比 hash join / merge join / nested-loop 的 I/O 代价。做 24-25 P5、quiz 4、quiz 5。

### Day 4: 查询优化 & 事务并发

| Lec | 内容 | 重要度 |
|-----|------|--------|
| 11 | 查询优化: equivalence rules, execution plans, selectivity estimation, statistics, join ordering, cost-based optimizer | ★★★ |
| 12 | 事务: ACID, schedules, serializability (conflict-serializable), precedence graph drawing | ★★★★ |
| 13 | 并发控制: lock-based protocols, 2PL, strict 2PL, rigorous 2PL, deadlock detection/prevention (Wait-Die, Tree Protocol) | ★★★★★ |

**重点**: 画 precedence graph 判断 conflict-serializable、2PL/strict-2PL/rigorous-2PL 的区别和判断题（谁能保证 recoverability？谁能防死锁？）、Tree Protocol vs 2PL 生成调度互不包含。lec-11 理解 selectivity 计算和等价变换规则（选择下推、投影下推）。

**练习**: 给一组事务操作 → 画 precedence graph → 判断是否 conflict-serializable。给一个调度 → 判断是否可由 2PL 产生。做 17-18 P7、24-25 P8、22-23 Q5-6。

### Day 5: 恢复系统 & 查漏补缺

| Lec | 内容 | 重要度 |
|-----|------|--------|
| 14 | 恢复系统: failure classification, log-based recovery, WAL, checkpoint, ARIES (Analysis/Redo/Undo, CLR, DirtyPageTable) | ★★★★★ |

**重点**: ARIES 三阶段完整流程——Analysis 从最近 checkpoint 起、从 DirtyPageTable 找最小 RecLSN 作为 Redo 起点、Undo 按 LastLSN 降序撤销 loser、CLR 仅 undo 时产生（redo 不写 CLR）、commit 记录和 CLR 的 Redo 行为。

**整体复盘**:
- 重做 24-25 P9 的 ARIES 完整流程（脏页表填表 + undo-list + CLR LSN + 最终值）
- 浏览 MiniSQL 各模块（#0--#5）文档
- 刷 17-18 或 18-19 的选择/判断/ARIES 部分
