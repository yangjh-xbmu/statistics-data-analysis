# 来源池 · 运算符与容器系列

规则：**同一 URL 只登记一行**；新页需要同一来源时，在「用于哪几页」里追加 slug，不重复登记、不重复考证。
所有链接均为一手来源（官方文档 / 官方仓库 / 标准站点），已验证可访问。

| 来源 | URL | 用于哪几页 | 关键事实（可直接引用的一句） |
|---|---|---|---|
| Python 速览 · 3.1 用作计算器（中文） | https://docs.python.org/zh-cn/3/tutorial/introduction.html | operators · list | 「除法运算 (/) 总是返回一个浮点数」；`//` 向下取整、`%` 取余、`**` 计算乘方；「字符串可以用 + 合并，也可以用 * 重复」；「简单赋值绝不会复制数据」；索引与切片的入门说明 |
| 内置类型 · 数值类型（中文） | https://docs.python.org/zh-cn/3/library/stdtypes.html#numeric-types-int-float-complex | operators | 官方注脚：「结果总是向负无穷取整：1//2 是 0，(-1)//2 是 -1」；混合类型运算向宽类型看齐 |
| 6. 表达式 · 运算符优先级（中文） | https://docs.python.org/zh-cn/3/reference/expressions.html#operator-precedence | operators | 优先级表：`**` 高于一元 `-`，`*` `/` `//` `%` 同档，比较运算符低于算术运算符 |
| 7. 输入与输出 · 格式化字符串字面值（中文） | https://docs.python.org/zh-cn/3/tutorial/inputoutput.html#formatted-string-literals | operators | `f"{score:.2f}"` 的格式规格迷你语言：`.2f` = 定点两位小数 |
| 内置函数 · round（中文） | https://docs.python.org/zh-cn/3/library/functions.html#round | operators | 两个倍数同样接近时「向偶数方向取整」；二进制浮点误差使 round 不适合当"四舍五入"用 |
| 5. 数据结构（中文） | https://docs.python.org/zh-cn/3/tutorial/datastructures.html | list · dict · table | 列表方法总表（append / extend / insert / remove / pop / clear / index / count / sort / reverse / copy）；「仅修改列表的方法……返回默认值 None」；列表可嵌套；5.5 字典：「键可以是任何不可变类型」「键必须是唯一的」「{} 用于创建空字典」「提取不存在的键会引发 KeyError，可改用 get()」「list(d) 按插入次序」 |
| 内置类型 · 序列通用操作（中文） | https://docs.python.org/zh-cn/3/library/stdtypes.html#common-sequence-operations | list | 切片 s[i:j] 的正式定义：i <= k < j；负索引等价于 len(s) + i；i 或 j 越界时自动截断 |
| 内置类型 · 映射类型 dict（中文） | https://docs.python.org/zh-cn/3/library/stdtypes.html#mapping-types-dict | dict | 映射以可哈希对象为键；`d[key]` 取不存在的键引发 KeyError；`get(key[, default])` 与 `setdefault` 的行为差异 |
| 术语表 · mutable / immutable（中文） | https://docs.python.org/zh-cn/3/glossary.html#term-mutable | list · dict | 「可变对象可以改变其值，值改变后 id() 不变」；不可变对象（str、元组）不可改 |
| 术语表 · hashable（可哈希）（中文） | https://docs.python.org/zh-cn/3/glossary.html#term-hashable | dict | 可哈希的对象在其生命期内哈希值不变、可与其他对象比较；不可变类型通常可哈希，列表等可变容器不可 |
| copy · 浅拷贝与深拷贝（中文） | https://docs.python.org/zh-cn/3/library/copy.html | list | 浅拷贝只复制最外层容器，共享内部对象；深拷贝才逐层复制 |
| 内置函数 · len（中文） | https://docs.python.org/zh-cn/3/library/functions.html#len | list · dict | 返回对象的长度（元素个数 / 键值对个数） |
| 内置函数 · sorted（中文） | https://docs.python.org/zh-cn/3/library/functions.html#sorted | list | 从可迭代对象返回新的排序列表；与原地排序的 list.sort() 分工不同 |
| 内置函数 · sum（中文） | https://docs.python.org/zh-cn/3/library/functions.html#sum | table | 对可迭代对象的元素求和；配合 len() 就是算术平均数 |
| statistics · mean（中文） | https://docs.python.org/zh-cn/3/library/statistics.html#statistics.mean | table | 样本算术平均数；注意与 numpy.mean 的标准差 ddof 差异（第 4 次课再展开） |
| pandas · DataFrame（官方 API） | https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.html | table | 带行列索引的二维表；本次手写的「列表套字典」是它的前身，第 3 次课一行 read_csv 即可得到 |

## 使用说明

- 生成单页时，先从本表取来源；若某页需要新来源，先追加到这里再写进页面。
- 页面溯源节里的卡片，标题与「支撑了哪个事实」可以和本表不同（页面面向读者，本表面向维护）。
- 已废弃 / 改版的链接：在行末加 `（已失效，替代：…）`，不要删行——避免其他页反复重新考证。
- 本系列与 `python-getting-started` 系列共享 `library/functions.html`、`library/stdtypes.html` 两个域名下的页面，但引用的是**不同小节**（那边是 `#type`，本系列是 `#round` `#len` `#sum` `#sorted` 与数值类型、序列、映射三节）。
