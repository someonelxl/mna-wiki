# Schema 初稿 v0.1

## 1. 文档定位
本文件用于定义本项目当前阶段最核心对象的最小结构约束。
它承接《项目总需求定位 v2.0》《第一阶段实施方案 v1.0》《系统设计文档 v1.0》《Rulebook 初稿 v0.1》，属于规则层中的 Schema 文档。
本文件的目标不是写尽所有字段，而是先把最关键的对象定型，避免后续页面、记录和自动化在对象边界上漂移。

## 2. 当前阶段 Schema 的作用
当前阶段的 Schema 主要承担四个作用：
1. 固定对象边界
2. 固定最小字段集合
3. 固定目录归属
4. 固定“原件 / raw source / source record / wiki page”之间的关系

## 3. 当前阶段纳入 Schema 的对象
当前阶段只纳入以下四类对象：
- Case
- Concept
- Source Record
- Raw Source

当前阶段暂不纳入：
- Index
- Analysis
- Summary
- Decision Log
- Review Report

这些对象后续再扩展，不在本版 Schema 中展开。

## 4. Schema 设计原则
### 4.1 最小优先
当前阶段只定义“最小可用字段”，不追求一次写满。

### 4.2 稳定优先
字段一旦进入 Schema，应尽量稳定，不随单次项目讨论频繁变化。

### 4.3 分层优先
必须优先区分：
- 原件层
- raw source 层
- record 层
- wiki 页面层

### 4.4 可追溯优先
涉及来源的对象，必须能回到原始出处或原始文本层。

### 4.5 可被人和 LLM 共同理解
字段名称、对象边界和目录归属，应同时对人和 LLM 清楚。

## 5. 对象一：Case
### 5.1 对象定义
Case 是具体并购或资本运作案例对象。
它属于 Wiki 层，正式落点为：
`wiki/cases/`

### 5.2 对象职责
Case 用于承接：
- 单案例研究
- 单案例判断
- 与 Concept 的连接
- 与其他 Case 的连接
- 与 Source 的挂接
- 内容输出基础

Case 字段优先记录交易角色，不预设所有交易都服从 buyer / seller 语义。对于 `spin-off`、`de-spac`、`take-private`、`reverse-merger`、`asset-injection`、`restructuring` 等交易，应优先使用交易角色字段体系。

### 5.3 最小字段
当前阶段，Case 至少应具备以下字段：
- `case_id`
- `case_name`
- `initiating_party`
- `core_entity`
- `counterparty`
- `transaction_structure`
- `control_shift`
- `public_market_vehicle`
- `announced_date`
- `deal_value`
- `industry`
- `region`
- `status`
- `one_line_definition`
- `deal_thesis`
- `core_tension`
- `related_concepts`
- `related_cases`
- `source_refs`

### 5.4 字段解释
- `case_id`：案例稳定编号
- `case_name`：案例正式名称
- `initiating_party`：交易主导方、发起方、推动方
- `core_entity`：本交易中最核心被重组、被装入、被出售、被分拆、被上市化、被私有化的公司、业务、资产或法律主体
- `counterparty`：对手方、处分方、另一侧关键主体；可为空，也可为多值列表
- `transaction_structure`：交易结构类型，应使用受控类型而非自由命名
- `control_shift`：交易完成后控制权如何变化
- `public_market_vehicle`：承担资本市场壳、SPAC、上市平台或公开市场载体作用的主体；如无则可为空
- `announced_date`：宣布时间
- `deal_value`：交易金额
- `industry`：行业
- `region`：地区
- `status`：当前状态
- `one_line_definition`：一句话定义
- `deal_thesis`：交易逻辑分析
- `core_tension`：最值得讲的冲突点
- `related_concepts`：关联母题
- `related_cases`：相关案例
- `source_refs`：来源引用或来源记录入口

### 5.5 transaction_structure 的当前受控类型
当前阶段，`transaction_structure` 应优先使用以下受控类型之一：
- `acquisition`
- `merger`
- `spin-off`
- `take-private`
- `de-spac`
- `reverse-merger`
- `asset-sale`
- `asset-injection`
- `restructuring`
- `joint-venture`

如果后续需要新增类型，应优先修改规则文档，而不是在页面里自由发明新写法。

### 5.6 当前阶段要求
当前阶段不要求每个 Case 一开始就写满所有字段，但以下字段应视为高优先级：
- `case_id`
- `case_name`
- `initiating_party`
- `core_entity`
- `transaction_structure`
- `one_line_definition`
- `related_concepts`
- `source_refs`

## 6. 对象二：Concept
### 6.1 对象定义
Concept 是正式连接层对象。
它属于 Wiki 层，正式落点为：
`wiki/concepts/`

### 6.2 对象职责
Concept 用于承接：
- 母题
- 分析框架
- 多 Case 连接
- 多 Source 连接
- 内容策划角度
- 新母题生长

### 6.3 最小字段
当前阶段，Concept 至少应具备以下字段：
- `concept_id`
- `concept_name`
- `concept_type`
- `status`
- `core_logic`
- `scope`
- `common_misreadings`
- `representative_cases`
- `related_cases`
- `related_sources`
- `content_angles`
- `evolution_notes`

### 6.4 字段解释
- `concept_id`：母题稳定编号
- `concept_name`：母题名称
- `concept_type`：母题类型
- `status`：当前状态
- `core_logic`：核心逻辑
- `scope`：适用边界
- `common_misreadings`：常见误判
- `representative_cases`：代表案例
- `related_cases`：相关案例
- `related_sources`：关联来源
- `content_angles`：可讲角度 / 内容生产价值
- `evolution_notes`：演化记录 / 待扩展点

### 6.5 当前阶段要求
当前阶段至少应优先稳定以下字段：
- `concept_id`
- `concept_name`
- `core_logic`
- `scope`
- `representative_cases`
- `related_sources`

## 7. 对象三：Raw Source
### 7.1 对象定义
Raw Source 是系统内部的原始可读文本层。
它属于 raw-sources 层，正式落点为：
`raw-sources/`

### 7.2 对象职责
Raw Source 用于：
- 保存原始可读文本
- 为 ingest 提供输入
- 为 wiki 判断提供证据层
- 保持可追溯性

### 7.3 与“原件层”的关系
必须明确：
- 原始 PDF 文件、原始网页链接、原始视频链接属于原件层 / 原始出处层
- Raw Source 是从这些原件转化而来的系统内可读文本层
- Raw Source 不是原件本体，但应能指回原件

### 7.4 最小字段
当前阶段，Raw Source 至少应具备以下字段或属性：
- `raw_source_id`
- `title`
- `source_type`
- `origin_reference`
- `imported_at`
- `storage_form`
- `content_body`
- `source_metadata`
- `classification`
- `state`
- `origin_relation_note`

### 7.5 字段解释
- `raw_source_id`：来源文本层稳定编号
- `title`：来源标题
- `source_type`：来源类型
- `origin_reference`：原始出处指针
- `imported_at`：导入时间
- `storage_form`：当前保存形式
- `content_body`：原始文本层主体
- `source_metadata`：作者、发布方、日期等元信息
- `classification`：粗分类
- `state`：当前归属状态
- `origin_relation_note`：原件与文本层关系说明

### 7.6 当前阶段要求
Raw Source 当前阶段最重要的是：
- 可读
- 可追溯
- 不混入总结性知识
- 能被 AI 稳定 ingest

## 8. 对象四：Source Record
### 8.1 对象定义
Source Record 是 Wiki 侧的来源记录对象。
它不是原始资料本体，而是来源的记录页、索引页和挂接页。
它属于 Wiki 侧记录层，正式落点为：
`wiki/sources/`

### 8.2 对象职责
Source Record 用于：
- 记录来源身份
- 指向原始出处
- 指向 raw source
- 说明来源性质
- 提炼核心价值
- 连接 Case 与 Concept
- 指出后续动作和风险

### 8.3 最小字段
当前阶段，Source Record 至少应具备以下字段：
- `source_id`
- `title`
- `source_type`
- `published_at`
- `author_or_publisher`
- `status`
- `origin_location`
- `system_location`
- `source_nature`
- `key_points`
- `linked_cases`
- `linked_concepts`
- `next_action`
- `risk_note`

### 8.4 字段解释
- `source_id`：来源记录稳定编号
- `title`：来源标题
- `source_type`：来源类型
- `published_at`：发布时间
- `author_or_publisher`：作者或发布方
- `status`：当前状态
- `origin_location`：原始出处位置
- `system_location`：系统内位置
- `source_nature`：来源性质说明
- `key_points`：核心要点
- `linked_cases`：关联案例
- `linked_concepts`：关联母题
- `next_action`：后续动作建议
- `risk_note`：风险提示

### 8.5 当前阶段要求
Source Record 当前阶段最重要的是：
- 能回到原始出处
- 能回到 raw source
- 能说明与哪些 Case / Concept 有关
- 能说明这份来源为什么值得保留

## 9. 四类对象之间的关系约束
### 9.1 Case 与 Concept
- 一个 Case 可关联多个 Concept
- 一个 Concept 可连接多个 Case

### 9.2 Source Record 与 Case / Concept
- 一个 Source Record 可关联多个 Case
- 一个 Source Record 可关联多个 Concept

### 9.3 Raw Source 与 Source Record
- Raw Source 是可读文本层
- Source Record 是记录与挂接层
- 一个 Source Record 应能指向一个或多个 Raw Source
- 一个 Raw Source 应能追溯到原始出处

### 9.4 Case / Concept 不应直接替代 Source Record
Case 和 Concept 页面可以引用来源，但不应吞并 Source Record 的记录职责。

## 10. 目录归属规则
当前阶段正式目录归属固定如下：
- `wiki/cases/` → Case
- `wiki/concepts/` → Concept
- `wiki/sources/` → Source Record
- `raw-sources/` → Raw Source

这是当前阶段正式标准。
后续若要调整，必须先改 Schema，再改实现。

## 11. 命名与编号的关系
本文件只固定“对象必须有稳定编号”这一原则，不在此处写死具体编号细则。
具体前缀、位数、命名拼接规则，应下沉到独立的命名实施细则文档。
但当前阶段默认要求：
- Case 有 `case_id`
- Concept 有 `concept_id`
- Raw Source 有 `raw_source_id`
- Source Record 有 `source_id`

## 12. 当前阶段不在本 Schema 中展开的内容
当前阶段暂不在本文件中展开：
- 复杂 metadata 体系
- 全量 provenance 树
- superseded / deprecated 完整状态系统
- Index / Analysis / Summary 的正式 Schema
- 复杂引用机制
- 自动化字段生成规则

这些内容后续扩展，不在本版最小 Schema 中锁死。

## 13. 本文档的作用
本文件的作用，是在当前阶段先把最关键的四类对象定型。
以后：
- 模板落地
- Rulebook 细化
- ingest / write-back / review 标准
- 轻量自动化
都应以本文件为对象结构基础。

## 14. 当前结论
当前阶段的最小 Schema 可以概括为：
- Case 是核心知识对象
- Concept 是正式连接层对象
- Raw Source 是原始可读文本层对象
- Source Record 是 Wiki 侧来源记录对象
- 四者分层明确、目录明确、职责明确

只要这四类对象先定住，后面的规则和实现就不会在对象边界上反复漂移。
