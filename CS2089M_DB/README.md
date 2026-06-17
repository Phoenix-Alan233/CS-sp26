# CS 2089M: 数据库系统

ZJU 大三数据库课，教材是 *Database System Concepts* 7th (Silberschatz)。上半学期讲模型和 SQL，下半学期讲 DBMS 内部实现。

## Courseware

| Lec | 内容 |
|-----|------|
| 01 | 数据库系统概述: DBMS, data abstraction, data models, DB languages, system architecture |
| 02 | 关系模型: relations, tuples, candidate keys, foreign keys, integrity constraints, relational algebra (σ, π, ⋈, ∪, −, ρ) |
| 03 | SQL: DDL, DML, SELECT, JOIN, subqueries, aggregation, GROUP BY |
| 04 | 高级 SQL: views, authorization, functions, procedures, triggers, embedded SQL |
| 05 | E-R 模型: entity, relationship, weak entity, cardinality constraints, E-R to relational schema |
| 06 | 关系数据库设计: functional dependency, closure, candidate keys, normal forms (1NF/2NF/3NF/BCNF), lossless decomposition, dependency preservation |
| 08 | 存储与文件结构: disk, pages, record organization, file organization, buffer pool |
| 09 | 索引与散列: ordered index, B+ tree, static hashing, dynamic hashing, index selection |
| 10 | 查询处理: query execution, selection algorithms, join algorithms (nested-loop, hash join, merge join), sorting, cost estimation |
| 11 | 查询优化: equivalence rules, execution plans, statistics, join ordering, cost-based optimizer |
| 12 | 事务: ACID, schedules, serializability (conflict-serializable), precedence graph |
| 13 | 并发控制: lock-based protocols, two-phase locking (2PL), deadlock, timestamp-based |
| 14 | 恢复系统: failure classification, log-based recovery, WAL, checkpoint, ARIES |

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

| Lec | 内容 |
|-----|------|
| 01 | 数据库系统概述: DBMS, data abstraction, data models, DB languages, system architecture |
| 02 | 关系模型: relations, tuples, candidate keys, foreign keys, integrity constraints, relational algebra (σ, π, ⋈, ∪, −, ρ) |
| 03 | SQL: DDL, DML, SELECT, JOIN, subqueries, aggregation, GROUP BY |

**重点**: 关系代数运算（选择和投影 vs 连接的区别）、SQL 嵌套查询和聚合的执行顺序。lec-01 快速过了解概念即可。

**练习**: 手写几道关系代数转 SQL 的题，确认 σ/π/⋈ 对应 SQL 的哪个子句。

### Day 2: 高级 SQL & 数据库设计

| Lec | 内容 |
|-----|------|
| 04 | 高级 SQL: views, authorization, functions, procedures, triggers, embedded SQL |
| 05 | E-R 模型: entity, relationship, weak entity, cardinality constraints, E-R to relational schema |
| 06 | 关系数据库设计: functional dependency, closure, candidate keys, normal forms (1NF/2NF/3NF/BCNF), lossless decomposition, dependency preservation |

**重点**: E-R 图转关系模式、函数依赖求闭包、BCNF 判定和无损分解。lec-04 理解视图和授权的概念即可。

**练习**: 给一个业务场景 → 画 E-R 图 → 转关系模式 → 检查范式。配合 hw04/05 练习。

### Day 3: 存储、索引 & 查询处理

| Lec | 内容 |
|-----|------|
| 08 | 存储与文件结构: disk, pages, record organization, file organization, buffer pool |
| 09 | 索引与散列: ordered index, B+ tree, static hashing, dynamic hashing, index selection |
| 10 | 查询处理: query execution, selection algorithms, join algorithms (nested-loop, hash join, merge join), sorting, cost estimation |

**重点**: B+ 树的结构和增删查操作、各种 join 算法的代价估算。这是从「会用 DB」到「理解 DB」的转折点。

**练习**: 手画 B+ 树的插入/删除过程，对比 nested-loop join、hash join、merge join 的 I/O 代价。

### Day 4: 查询优化 & 事务并发

| Lec | 内容 |
|-----|------|
| 11 | 查询优化: equivalence rules, execution plans, statistics, join ordering, cost-based optimizer |
| 12 | 事务: ACID, schedules, serializability (conflict-serializable), precedence graph |
| 13 | 并发控制: lock-based protocols, two-phase locking (2PL), deadlock, timestamp-based |

**重点**: 冲突可串行化判定（画优先图）、2PL 协议与死锁的关系。lec-11 理解优化器怎么做 join ordering 即可。

**练习**: 给一组事务操作 → 画 precedence graph → 判断是否 conflict-serializable。给一个调度 → 判断是否满足 2PL。

### Day 5: 恢复系统 & MiniSQL

| Lec | 内容 |
|-----|------|
| 14 | 恢复系统: failure classification, log-based recovery, WAL, checkpoint, ARIES |

**重点**: WAL 原理、checkpoint 后的恢复流程、ARIES 三阶段（analysis / redo / undo）。

**实验复盘**: 浏览 MiniSQL 各模块文档（#0 ~ #5），重点看 Buffer Pool Manager (LRU)、Index Manager (B+ Tree)、SQL Executor 这三个最核心的模块。配合 `MiniSQL 实验指导书.doc` 理解整体架构。
