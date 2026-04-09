# 并购视频 Wiki 项目

本目录是“并购视频 Wiki 项目”的正式项目根目录。
该项目以并购案例为核心，服务于研究、知识沉淀与内容生产。
当前目录结构遵循总需求定位文档与 Karpathy Wiki 方法进行组织。

## 建议先阅读
- `docs/foundation/project-positioning-v2.md`：项目总需求定位文档
- `docs/foundation/naming-rulebook-v1.md`：命名规范总纲

## 当前目录结构遵循以下原则
- 以总需求定位文档作为最高方向约束
- 对齐 Karpathy Wiki 的 `raw-sources / wiki / rulebook` 骨架
- 保持目录清晰、长期可维护，便于 Git/GitHub、VS Code、Obsidian、Codex 协同

## 目录职责
- `docs/`：放项目基础文档、规划文档与设计文档
- `rules/`：放规则文档与结构约束，对应 rulebook / schema 层
- `templates/`：放标准模板，用于统一页面骨架
- `raw-sources/`：放原始资料入口与归档层
- `wiki/`：放结构化 Wiki 页面、来源记录页与分析产物
- `scripts/`：放导入、处理、索引与通用工具脚本
- `config/`：放项目配置文件
- `logs/`：放运行日志与检查记录

## 当前目录树
```text
mna-wiki/
├─ README.md
├─ docs/
│  ├─ foundation/
│  ├─ planning/
│  └─ design/
├─ rules/
│  ├─ schema/
│  ├─ rulebooks/
│  └─ standards/
├─ templates/
│  ├─ wiki-pages/
│  ├─ source-records/
│  └─ docs/
├─ raw-sources/
│  ├─ inbox/
│  ├─ cases/
│  └─ general/
├─ wiki/
│  ├─ cases/
│  ├─ concepts/
│  ├─ sources/
│  ├─ indexes/
│  └─ analysis/
├─ scripts/
│  ├─ ingest/
│  ├─ source-processing/
│  ├─ indexing/
│  └─ utilities/
├─ config/
└─ logs/
```
