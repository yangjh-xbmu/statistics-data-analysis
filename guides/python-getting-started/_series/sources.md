# 来源池 · Python 起步系列

规则：**同一 URL 只登记一行**；新页需要同一来源时，在「用于哪几页」里追加 slug，不重复登记、不重复考证。
所有链接均为一手来源（官方文档 / 官方仓库 / 标准站点），已验证可访问。

| 来源 | URL | 用于哪几页 | 关键事实（可直接引用的一句） |
|---|---|---|---|
| Python Downloads | https://www.python.org/downloads/ | environment | 当前稳定版 3.14.7（2026-08-05 发布）；3.15 计划 2026-10-01 发布 |
| 使用 Python 解释器（中文） | https://docs.python.org/zh-cn/3/using/index.html | environment | 解释器的调用方式、命令行参数与退出状态 |
| 虚拟环境与包（教程） | https://docs.python.org/zh-cn/3/tutorial/venv.html | environment | 项目级隔离环境；pip 把包装进当前环境的 site-packages |
| Python environments in VS Code | https://code.visualstudio.com/docs/python/environments | environment | 编辑器如何选择解释器；切换解释器会改变运行行为 |
| What is Jupyter? | https://docs.jupyter.org/en/latest/what_is_jupyter.html | notebook | 内核是常驻内存的 REPL；跨单元格保住变量，关掉内核即丢失 |
| The Jupyter Notebook Format（nbformat 规范） | https://nbformat.readthedocs.io/en/latest/format_description.html | notebook | `.ipynb` 是 JSON 文档，顶层字段含 cells 与 metadata；cell 有 code / markdown 等类型 |
| Jupyter Notebooks in VS Code | https://code.visualstudio.com/docs/datascience/jupyter-notebooks | notebook | 单元格运行快捷键、内核选择器、重启 / 中断内核的位置 |
| 8. 错误和异常（中文） | https://docs.python.org/zh-cn/3/tutorial/errors.html | traceback | 「错误信息的最后一行说明程序遇到了什么类型的错误」；语法错误的箭头不一定指在要修的位置 |
| 内置异常（中文） | https://docs.python.org/zh-cn/3/library/exceptions.html | traceback | 异常层次：BaseException → Exception → 各类具体异常 |
| 4. 执行模型 · 名称的绑定（中文） | https://docs.python.org/zh-cn/3/reference/executionmodel.html | traceback · variables | 「名称用于指代对象」；NameError 的判定；UnboundLocalError 是 NameError 的子类 |
| 内置类型（中文） | https://docs.python.org/zh-cn/3/library/stdtypes.html | variables | int / float / str / bool 的定义与各自支持的操作 |
| 内置函数 type()（中文） | https://docs.python.org/zh-cn/3/library/functions.html#type | variables | 返回对象的类型；`type(78)` → int |
| 格式化字符串字面值 / f-string（中文） | https://docs.python.org/zh-cn/3/tutorial/inputoutput.html#formatted-string-literals | variables | `f"{score:.2f}"` 的格式规格迷你语言 |
| 2. 词法分析（中文） | https://docs.python.org/zh-cn/3/reference/lexical_analysis.html | variables | 引号、括号、缩进的语法规定（全角符号为何不能通过解析） |
| PEP 8 · 函数与变量命名 | https://peps.python.org/pep-0008/#function-and-variable-names | variables | 小写 + 下划线；禁止 l / O / I 作单字符变量名 |

## 使用说明

- 生成单页时，先从本表取来源；若某页需要新来源，先追加到这里再写进页面。
- 页面溯源节里的卡片，标题与「支撑了哪个事实」可以和本表不同（页面面向读者，本表面向维护）。
- 已废弃 / 改版的链接：在行末加 `（已失效，替代：…）`，不要删行——避免其他页反复重新考证。
