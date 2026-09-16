# Python 起步 · 概念切分表

> 来源：`notes/python-pandas-course-plan.md` 第 1 次课上半场（环境、Notebook、报错怎么读、变量与基本类型）
> 结论：四个概念，四页手册 + 1 个 hub（`guides/python-getting-started/`）

## 切分结果

| # | 概念 | slug | 一句话定义 | 核心图 | 判据自检 |
|---|---|---|---|---|---|
| 1 | Python 运行环境 | `python-environment` | 解释器、编辑器、包管理是三个独立程序，各管一段 | 三层栈：编辑器 → 解释器 → site-packages（含 PATH 指向关系） | ①一句话 ②官方 4 源 ③独立考点 ④不与邻页重图 —— 全过 |
| 2 | Notebook 与内核 | `jupyter-notebook` | `.ipynb` 是一份 JSON 文档，真正执行的是常驻内存的内核 | 文档（cell 列表 + 保存的输出）↔ 内核（REPL + 对象表） | 全过（nbformat 规范是一手来源） |
| 3 | 报错与 Traceback | `python-traceback` | 异常是对象，Traceback 从下往上读，最后一行是类型与原因 | Traceback 三层解剖 + 异常家族树（Exception 下方分支） | 全过（官方 errors / exceptions / executionmodel 三源） |
| 4 | 变量与基本类型 | `python-variables` | 变量是「名字指向对象」，四种基本类型决定它能做什么运算 | 名称→对象绑定图 + 类型四分表（对应四种测量尺度） | 全过 |

**为什么不再合并**：现有 `python-basics-guide.html` 是四个概念的"平均分"——01 属于 ②、02 属于 ④、03 属于 ③、04 的铁律各混一条。每节只能给一句 lead + 一张图，导致 ② 讲不深（缺 nbformat、cell 类型与状态）、① 几乎没讲（PATH、版本、包管理）。

## 顺序与依赖

```
① 环境 ──▶ ② Notebook ──▶ ③ 报错怎么读 ──▶ ④ 变量与基本类型
   ▲                                              │
   └──────── ④ 要真的跑起来，仍依赖 ①② ◀──────────┘
```

- ①② 是前提（先能跑起来）；
- ③ 是**工具性知识**，必须排在 ④ 之前：先学会读报错，写变量时第一次出错才不会卡住；
- ③ 与 ④ **可以互换顺序**（hub 上已标注）；
- ④ 回指 ①②：没有环境与内核，变量无处安放。

## 每页自测点（先定考点，避免跨页撞题）

| slug | 基础 · 识别 | 进阶 · 理解 | 挑战 · 应用 |
|---|---|---|---|
| `python-environment` | 解释器与编辑器是不是同一个程序；终端里找不到 `python` 命令通常是哪里的问题 | 换解释器为什么行为会变；`pip` 装的包落在哪个目录 | 两个项目要不同版本的 pandas 怎么办；三个终端显示不同版本的原因 |
| `jupyter-notebook` | `.ipynb` 打开成文本是什么格式；重启内核后输出与变量各自还在不在 | 关掉内核变量为何消失；两种 cell 类型的分工 | 交付前为什么要「重启内核 + 全部运行」；`.ipynb` 与 `.py` 各适合什么场景 |
| `python-traceback` | 哪一行说明错误类型；SyntaxError 与 NameError 分别发生在哪一步 | 为什么语法错误的箭头不一定指在要改的位置；`^^^^` 细粒度定位表达什么 | NameError 与 UnboundLocalError 的关系；一份二十行 Traceback 的读法顺序 |
| `python-variables` | `type(78)` 是什么；`"1" + "1"` 与 `1 + 1` 各自结果 | `b = a` 后改 b 为何 a 也变；四种类型对应哪种测量尺度 | 为什么 `int("3.5")` 报错；什么时候该用 int 而不是 float |

## 来源候选

| slug | 一手来源 | 与邻页重叠 |
|---|---|---|
| `python-environment` | python.org/downloads · docs.python.org/zh-cn/3/using/ · tutorial/venv · code.visualstudio.com/docs/python/environments | 与 ② 共享 VS Code 域名，但页面不同 |
| `jupyter-notebook` | nbformat.readthedocs.io（Notebook 格式规范）· docs.jupyter.org/en/latest/what_is_jupyter.html · code.visualstudio.com/docs/datascience/jupyter-notebooks | 无重叠 |
| `python-traceback` | tutorial/errors · library/exceptions · reference/executionmodel（NameError / UnboundLocalError） | 与 ④ 共享 executionmodel，**同一来源只在来源池登记一次**，两页各自引用不同小节 |
| `python-variables` | reference/executionmodel（名称绑定）· library/stdtypes · library/functions#type · tutorial/inputoutput（f-string）· peps.python.org/pep-0008 | 同上 |

## 状态

- [x] 切分表已确认（2026-09-16，方案 A + 4 页 + `guides/` 子目录）
- [ ] hub 页（`index.html`）
- [ ] 第 1 页 `python-environment-guide.html`
- [ ] 第 2 页 `jupyter-notebook-guide.html`
- [ ] 第 3 页 `python-traceback-guide.html`
- [ ] 第 4 页 `python-variables-guide.html`
- [ ] 系列质检（跨页一致性 + 链接 + 截图）
