# statistics-data-analysis

统计与数据分析课程学习仓库

## 简介

本仓库用于记录统计与数据分析课程的学习笔记、代码练习和数据集。

## 目录结构

```
statistics-data-analysis/
├── notes/       # 课程笔记（按章节组织）
├── exercises/   # 课后练习与代码
├── datasets/    # 课程数据集
└── projects/    # 课程项目/作业
```

## 课件与数据集

- [Python 基础语法 + pandas 四次课方案](notes/python-pandas-course-plan.md)（4 × 90 分钟；基础语法 2 次 + pandas 2 次）
- 系列学习材料：`guides/<系列名>/`（每个概念一页手册 + 一个路径页）
  - [Python 起步](guides/python-getting-started/index.html) — 环境 / Notebook 与内核 / 报错与 Traceback / 变量与基本类型，共 4 篇 + 路径页（第 1 次课上半场）
  - [运算符与容器](guides/python-operators-containers/index.html) — 运算符与表达式 / 列表 / 字典 / 列表套字典 = 一张表，共 4 篇 + 路径页（第 1 次课下半场）
  - 混合版单页手册：[python-basics-guide.html](python-basics-guide.html)、[python-containers-guide.html](python-containers-guide.html)（各概念的浅版，正被上述系列逐页取代）
- 数据集：
  - `datasets/scores.csv` — 30 条学生成绩（干净数据），第 1–3 次课使用
  - `datasets/scores_messy.csv` — 同一批学生的脏数据版（32 行，含缺失/重复/类型错/异常值），第 4 次课清洗练习
  - `datasets/survey.csv` — 32 条问卷数据（含定类、定序变量），交叉表与分组练习
- 三份 CSV 均带 UTF-8 BOM，用于演示 `encoding="utf-8-sig"`

## 学习进度

- [ ] 第 1 章：描述性统计
- [ ] 第 2 章：概率基础
- [ ] 第 3 章：假设检验
- [ ] 第 4 章：回归分析
- [ ] 第 5 章：数据可视化
