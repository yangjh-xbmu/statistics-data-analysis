# 运算符与容器 · 概念切分表

> 来源：`notes/python-pandas-course-plan.md` 第 1 次课下半场（运算符与 f-string、列表、字典、"列表套字典 = 一张表"）
> 结论：四个概念，四页手册 + 1 个 hub（`guides/python-operators-containers/`）

## 切分结果

| # | 概念 | slug | 一句话定义 | 核心图 | 判据自检 |
|---|---|---|---|---|---|
| 1 | 运算符与表达式 | `python-operators` | 运算符把值算成新值，算什么由操作数的类型决定 | 八格「表达式 → 结果」表 + 同一符号在 str / int 上的分歧对照 | ①一句话 ②官方 4 源 ③独立考点 ④不与邻页重图 —— 全过 |
| 2 | 列表 | `python-list` | 列表是一个名字装下有序的一列值，按位置取 | 下标尺（正 / 负索引同轴）+ 切片半开区间 | 全过（tutorial 速览 + datastructures 两源） |
| 3 | 字典 | `python-dict` | 字典是键值对的集合，按键取，键唯一且不可变 | 键→值 标签盒 + 取值三条路（下标 / get / in） | 全过（datastructures 5.5 是一手来源） |
| 4 | 列表套字典 = 一张表 | `python-table` | 列表的每一项是一行、字典的每个键是一列，合起来就是数据表 | 双形态对照（代码 ↔ 表格）+ 统计四步数据流 | 全过（与 2、3 不重图：2 讲取值、3 讲键，本页讲行列结构） |

**为什么不再合并**：单页版 `python-containers-guide.html` 是四个概念的"平均分"——第 3 节能给列表套字典只留一张图，讲不了"每行键可以不一致"这个真实坑；运算符那页也只能停在符号表，讲不透"结果由类型决定"。每页只有一个 lead + 一张图时，四合一必然每件都讲浅。

## 顺序与依赖

```
① 运算符 ──▶ ② 列表 ──▶ ③ 字典 ──▶ ④ 列表套字典 = 一张表
                  └──────────┴──────────────▲
                     ④ 的行就是 ③，④ 的表就是 ②
```

- ① 在最前面：`+ - * / // % **` 是后面所有取值、统计动作的动词；
- ② 与 ③ **顺序可互换**（hub 上已标注）：一个讲"按位置取"，一个讲"按名字取"，互不依赖；
- ④ 必须最后：它同时用掉 ② 的列表和 ③ 的字典，是第 3 次课 pandas 的正式伏笔；
- ④ 之后回指 ③：真实数据里某一行可能缺一个键，那是 `.get()` 的用武之地。

## 每页自测点（先定考点，避免跨页撞题）

| slug | 基础 · 识别 | 进阶 · 理解 | 挑战 · 应用 |
|---|---|---|---|
| `python-operators` | `7 / 2` 是什么类型；`'10' + 5` 为什么报 TypeError | `//` 与 `%` 的结果为什么和"想当然"不同；`**` 与 `-` 谁先算 | `-7 // 2` 为什么是 -4；什么时候该用 `//` 而不是 `round()` |
| `python-list` | `s[0]` 与 `s[-1]` 各是谁；`len(s)` 给什么 | `s[1:3]` 为何是两个元素；下标越界与切片越界的差别 | `b = a` 后改 b 为何 a 也变；怎么安全地拿一份能改的副本 |
| `python-dict` | 一条"学生记录"的键和值分别是什么；`len(d)` 数的是什么 | `d[key]` 与 `d.get(key)` 的分工；键为什么不能用列表 | 复合键怎么表达一列；缺字段时怎么算平均分不中断 |
| `python-table` | 列表的每一项对应表的什么；字典的每个键对应表的什么 | 为什么 `rows["final"]` 一定报错；行的顺序有什么含义 | 30 条记录求均值该怎么写；这件事 pandas 怎么一行做完 |

## 来源候选

| slug | 一手来源 | 与邻页重叠 |
|---|---|---|
| `python-operators` | tutorial/introduction（3.1 计算器）· library/stdtypes#numeric-types-int-float-complex · reference/expressions（运算符优先级）· tutorial/inputoutput#formatted-string-literals · library/functions#round | 无重叠（上半场 f-string 只作为 `variables` 页的引用登记，本系列主讲运算符一侧） |
| `python-list` | tutorial/introduction#lists · tutorial/datastructures（列表方法）· library/stdtypes#common-sequence-operations · library/functions#len · library/functions#sorted | 与 ④ 共享 datastructures 域，但页面不同小节 |
| `python-dict` | tutorial/datastructures#dictionaries · library/stdtypes（映射类型）· library/functions#len | 无重叠 |
| `python-table` | tutorial/datastructures（列表嵌套）· library/functions#sum · library/statistics#statistics.mean · pandas DataFrame API | **同一来源只在来源池登记一次**，本页引用不同小节 |

## 状态

- [x] 切分表已确认（2026-09-16，沿用 `python-getting-started` 的 4 页 + hub 结构）
- [x] hub 页（`index.html`）—— 概念地图 + 顺序依赖 + 术语表 + 使用方法
- [x] 第 1 页 `python-operators-guide.html`
- [x] 第 2 页 `python-list-guide.html`
- [x] 第 3 页 `python-dict-guide.html`
- [x] 第 4 页 `python-table-guide.html`
- [x] 系列质检：5 页 JS 语法校验通过、答案分布无扎堆、核心图逐页截屏核验（无溢出 / 无重叠）、跨页无重复考点
- [x] 全部数值在本机 Python 3.13.14 实测（`-7//2=-4`、`-3**2=-9`、`round(2.5)=2`、`s[1:3]=[85,62]`、`list indices … not str`、scores.csv 均分 77.33 / 75.43 / 及格率 93.3%）
