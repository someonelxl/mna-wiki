# Rulebook 初稿 v0.1

## 1. 文档定位
本文件用于承接《项目总需求定位 v2.0》《第一阶段实施方案 v1.0》《系统设计文档 v1.0》，为本项目提供第一版规则层骨架。
本文件不负责解释项目为什么存在，也不负责定义页面的最终具体栏目，而是回答：
- 系统按什么规则长
- 哪些对象分别属于哪一层
- 哪些内容可以写，哪些内容不能乱写
- 人与 Codex 在当前阶段分别应如何行动

## 2. 规则层的作用
Rulebook / Schema 层的作用有四个：
1. 固定对象边界
2. 固定命名与目录理解方式
3. 固定写入边界
4. 固定 ingest / write-back / review 的基本纪律

如果没有这一层，项目会逐渐出现：
- 目录混乱
- 对象混淆
- source 与 wiki 混写
- AI 写回失控
- 后续 review 无法收敛

## 3. 系统对象边界
### 3.1 Case
Case 是具体并购或资本运作案例对象。
Case 属于 Wiki 层，不属于 raw sources 层。
Case 页面用于承接：
- 单案例研究
- 单案例判断
- 与其他 Case 的连接
- 与 Concept 的连接

Case 不等于 source 容器，也不等于原始资料本身。

### 3.2 Concept
Concept 是正式连接层对象。
Concept 属于 Wiki 层，不属于 raw sources 层。
Concept 不是普通标签，而是：
- 母题承载对象
- 分析框架对象
- 多 Case、多 Source 的连接节点

Concept 可以吸收来源，也可以随着来源进入而生长。

### 3.3 Source
Source 是来源对象，必须区分两层：
1. raw source 文本层
2. source record 记录层

raw source 属于 `raw-sources/`。
source record 属于 Wiki 侧记录层对象，正式落点为 `wiki/sources/`。

Source 的职责是提供来源与证据，不等于整理后的知识页。

### 3.4 Raw Source
Raw Source 是 source of truth 的文本化原始资料层。
Raw Source 应尽量保持原始性和可追溯性，不应用来承载后期总结性知识。

## 4. 三层结构规则
### 4.1 Raw Sources 层
这一层放原始可读资料。
允许进入这一层的内容包括：
- 网页转出的 Markdown 文本
- PDF 提取后的文本层
- 视频 transcript 文本
- 书籍、研报、文献、报告的原始可读文本层

这一层的目标是：保存原始资料，不直接承担知识总结功能。

### 4.2 Wiki 层
这一层放整理后的知识页面。
允许进入这一层的对象包括：
- Case
- Concept
- Source Record
- Index
- 后续的 analysis / summary

这一层的目标是：整理知识、建立连接、承接 write-back、服务研究与内容生产。

### 4.3 Rulebook / Schema 层
这一层放规则文档。
允许进入这一层的内容包括：
- 对象边界说明
- 命名规范
- ingest 规则
- write-back 规则
- review / lint 规则
- 写入边界规则

这一层的目标是：定义秩序，而不是承载知识内容。

## 5. 命名与目录规则
### 5.1 文件系统层
文件系统层统一采用 `kebab-case`。
适用对象：
- repo 名
- 项目根目录
- 文件夹名
- 文件名
- 脚本名
- 配置文件名

### 5.2 知识对象层
知识对象优先采用“前缀 + 编号”体系。
适用对象：
- Case
- Source
- Concept / 母题
- 决策记录

具体前缀与编号细节，后续可在专门文档中扩展，但原则在这里先固定。

### 5.3 显示层
页面标题、文档标题、README 标题优先采用自然语言标题。
显示层可以保留中文或人类可读表达，但应保持：
- 清楚
- 克制
- 不口号化
- 不冗长

### 5.4 规则层
规则文件应带显式前缀，优先使用：
- `rulebook-`
- `schema-`
- `standard-`

## 6. 写入边界规则
### 6.1 Raw source 不作为自由写作区
Raw source 不应用来承载：
- 后续总结
- AI 判断
- 主观结论
- 结构化知识整理

Raw source 的原则是：保存原始文本层，而不是让 AI 在上面自由重写。

### 6.2 Wiki 页面允许写回，但应受约束
Wiki 页面允许随着 ingest、write-back、review 逐步更新。
但更新应遵守：
- 优先更新知识层，不污染来源层
- 优先在结构稳定的位置更新
- 高风险更新应可审核

### 6.3 Rulebook 文件不应被自由改写
Rulebook 文件属于高约束文档。
在没有明确任务和理由时，不应让 Codex 自由改写规则层文件。
规则层修改应视为高风险变更。

## 7. Case 字段规则
### 7.1 交易角色字段优先于买卖语义
Case 字段优先记录交易角色，不预设所有交易都服从“buyer / seller / target”的标准并购语义。
对于以下交易类型尤其如此：
- spin-off
- de-spac
- take-private
- reverse-merger
- asset-injection
- restructuring

在这些情形下，应优先记录：
- `initiating_party`
- `core_entity`
- `counterparty`
- `transaction_structure`
而不是强行套入 buyer / seller 语义。

### 7.2 transaction_structure 必须受控
`transaction_structure` 不应作为自由文本字段任意发挥。
当前阶段应优先使用受控类型，例如：
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

若需要新增类型，应优先更新规则或 Schema，而不是在页面里自由发明写法。

### 7.3 counterparty 的边界
`counterparty` 可为空，也可为多值列表。
并非所有交易都存在清晰单一的对手方。
例如：
- spin-off 可能无传统对手方
- take-private 可能对应公众股东整体
- reverse-merger 可能涉及壳公司、控制人或多方结构主体

因此，不应为了字段完整而强行虚构单一对手方。

### 7.4 control_shift 与 public_market_vehicle
对于复杂资本运作案例，以下字段应被视为重要字段：
- `control_shift`
- `public_market_vehicle`

原因是很多案例的分析重点不在标准买卖关系，而在于：
- 控制权如何迁移
- 上市平台如何被使用
- 壳、SPAC 或公开市场载体如何参与结构设计

因此，后续模板与写入应保留这两个字段，不应省略。

### 7.5 Case 与母题关联
当前阶段，一个 Case 可以关联多个母题。
Wiki 层不强制区分主母题、辅助母题、相关母题等主次层级。
推荐流程应为：
- AI 推荐多个相关母题候选
- 人工删除明显不相关项并确认保留结果

“哪个母题适合支撑长视频”属于内容生产层判断，不属于当前 Wiki 基础结构，不应在本层提前写死。

## 8. Ingest 规则
### 8.1 Ingest 的定义
Ingest 不是简单导入文件，而是：
- 读取新 source
- 判断其重要性与影响范围
- 让系统吸收新资料
- 推动 wiki 更新

### 8.2 Ingest 的输入
当前阶段 ingest 的主要输入包括：
- 新案例
- 新来源
- 新分析结果

### 8.3 Ingest 的输出
Ingest 可能带来的输出包括：
- 新的 Case 页面
- 更新的 Concept 页面
- 新的 Source Record
- 新的页面连接
- 后续 analysis / summary 的基础

### 8.4 Ingest 的边界
当前阶段的 ingest 不应直接自由大改整个 wiki。
更稳的原则是：
- 先生成候选更新
- 再由人审核关键判断
- 再正式写回

## 9. Write-back 规则
### 9.1 Write-back 的定义
Write-back 指把新的理解、判断和连接正式写回 Wiki。
它不是把 raw source 再存一遍，而是把新知识沉淀到知识层。

### 9.2 哪类内容值得 write-back
当前阶段优先考虑以下内容：
- 更清楚的案例判断
- 更稳的母题归属
- 有价值的跨案例连接
- 值得长期保留的分析角度
- 对内容生产有直接价值的结构化结论

### 9.3 哪类内容暂不 write-back
当前阶段不应轻易写回：
- 尚未成熟的临时想法
- 没有来源支撑的判断
- 一次性对话情绪
- 过于零散的碎片化结论

### 9.4 Write-back 的目标位置
当前阶段 write-back 的目标位置优先是：
- Case 页面
- Concept 页面
- Index 页面

analysis 页面后续再逐步引入。

## 10. Review / Lint 规则
### 10.1 Review / Lint 的目标
Review / lint 的目标不是生产新知识，而是给系统做体检。
重点检查：
- 冲突
- 孤立
- 缺口
- 过时
- 误关联

### 10.2 当前阶段重点检查项
当前阶段优先检查：
- 页面是否孤立
- 重要判断是否缺少来源支撑
- Concept 是否存在明显该建未建
- 目录与对象是否脱节
- source 与 wiki 是否发生混写
- Case 是否被错误地强行写成 buyer/seller 结构

### 10.3 当前阶段的执行方式
当前阶段 review / lint 以：
- 人工主导
- AI 辅助
- 输出问题清单
为主，不追求自动修复。

## 11. Codex 的规则边界
### 11.1 Codex 在当前阶段可以做什么
Codex 当前阶段可以：
- 阅读总纲、实施方案、系统设计文档和规则文档
- 协助整理目录与文档结构
- 协助生成模板骨架
- 协助补轻量 glue code
- 协助提出更新建议

### 11.2 Codex 当前阶段不应做什么
Codex 当前阶段不应：
- 自由决定系统长期方向
- 在无审核下批量写正式知识页
- 自由重写 Rulebook
- 把 raw source 改写成总结页
- 越过总纲和规则自行定义对象边界
- 把非标准交易自由硬套成标准 buyer / seller 结构

### 11.3 当前阶段的默认原则
Codex 是受约束施工队，不是自由总设计师。
如果没有明确授权，应优先：
- 建议
- 草拟
- 生成骨架
而不是直接大改正式结构。

## 12. 当前阶段的最小执行纪律
当前阶段无论是人还是 Codex，在新增内容前，都应先判断：
1. 这属于哪一层
2. 这属于哪类对象
3. 应写到哪个目录
4. 是否会污染 raw source
5. 是否应先形成建议而不是直接写回
6. 命名是否符合总纲
7. 是否错误地把交易角色问题简化成买卖语义

## 13. 本文档的作用
这份 Rulebook 初稿的作用，是在第一阶段先把最基本的秩序立起来。
它不是终稿，也不是详尽规则全集。
后续随着：
- 模板层明确
- source 流程明确
- review 机制明确
本文件会继续扩展版本。
但在当前阶段，它已经足以作为：
- 人的行动边界
- Codex 的施工边界
- 后续模板与实现文档的规则基础
