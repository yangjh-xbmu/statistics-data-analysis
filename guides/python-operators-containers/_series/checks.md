# 系列质检报告 · 运算符与容器

执行日期：2026-09-16 · 校验对象：`guides/python-operators-containers/`（4 页 + hub）

## 逐页

| 检查项 | operators | list | dict | table |
|---|---|---|---|---|
| 每节事实均有一手出处 | ✓ 5 张源卡 | ✓ 6 张 | ✓ 5 张 | ✓ 5 张 |
| 每节 = 一句 lead + 一张图 | ✓ | ✓ | ✓ | ✓ |
| 只有一种强调色（#C4633F 系） | ✓ | ✓ | ✓ | ✓ |
| 六题三级递进（2/2/2） | ✓ | ✓ | ✓ | ✓ |
| CSS 选择器已收窄（无裸 `.opt`） | ✓ | ✓ | ✓ | ✓ |
| JS 字符串内无 ASCII 直引号 | ✓ | ✓ | ✓ | ✓ |
| `node --check` 通过 | ✓ | ✓ | ✓ | ✓ |
| 导航齐备（crumbs + pn） | ✓ | ✓ | ✓ | ✓ |
| SVG marker id 全局唯一 | `op1` | `—（无 marker）` | `—` | `tb1` |

> 注：list 与 dict 两页的核心图不需要连线，因此没有 marker；operators 用 `op1`、table 用 `tb1`，与 hub 的 `oc1`/`oc2` 不冲突。

## 跨页

- [x] hub 的 `PAGES.ready` 全为 `true`，四张卡都可点
- [x] 每页能回 hub、能到前后页 —— 内部链接扫描 0 断链（`index.html`、`_series/*.md`、`../../python-containers-guide.html`、前后页共 19 条）
- [x] 术语措辞与 hub 术语表一致（一行=字典、一列=键、列表套字典=一张表）
- [x] 来源无重复考证 —— 对照 `sources.md`，同一 URL 只登记一行
- [x] 自测考点无原题照搬（见下方答案分布）
- [x] 答案索引在系列内打散

答案分布（`a:` 索引）：

```
operators  1,2,3,1,2,1
list       1,3,2,3,1,2
dict       2,1,2,1,3,3
table      2,3,2,1,3,2
```

四个位置在 24 题里都出现过，单页内无同一位置连出三次。

## 关键事实的本机实测（Python 3.13.14）

| 事实 | 实测结果 | 出现在 |
|---|---|---|
| `/` 恒返回浮点 | `7/2 = 3.5`（float） | operators 01 |
| `//` 向负无穷取整 | `7//2 = 3`、`-7//2 = -4`、`7.0//2 = 3.0` | operators 01/04 |
| 余数跟着除数走 | `-7%2 = 1`、`7%-2 = -1` | operators 01 |
| `**` 优先级高于一元 `-` | `-3**2 = -9`、`(-3)**2 = 9`、`2**3**2 = 512` | operators 04 |
| 类型不匹配 | `'3'+5 → TypeError: can only concatenate str (not "int") to str` | operators 02 |
| `round` 向偶数取整 | `round(2.5)=2`、`round(3.5)=4`、`round(0.5)=0` | operators 04 |
| 浮点显示位数 | `2320/30 = 77.33333333333333`；`f"{…:.2f}" = '77.33'` | operators 03 |
| 切片含头不含尾 | `[78,85,62,91,100][1:3] = [85, 62]` | list 02 |
| 切片越界自动截断 | `s[10:] = []`，而 `s[10] → IndexError` | list 02/04 |
| 赋值不复制 | `a=[1,2,3]; b=a; b.append(4)` → `a == [1,2,3,4]` | list 04 |
| 改列表的方法返回 None | `x.sort()` → `None`；`y = y.sort()` → `y is None` | list 04 |
| 混类型求和 | `sum([78,'缺考',91]) → TypeError: unsupported operand type(s) for +: 'int' and 'str'` | list 01 |
| 键必须可哈希 | `{[1,2]:'x'} → TypeError: unhashable type: 'list'` | dict 02 |
| 覆盖而非新增 | `d['midterm']=78` 后再 `=80` → 只有 1 个键，值 80 | dict 03 |
| 缺字段用 get 兜底 | 三行记录中一行无 `final` → `get` 跳过得 `170/2 = 85.0` | dict 06 / table 04 |
| 列表不能按名字取 | `rows['final'] → TypeError: list indices must be integers or slices, not str` | table 02 |
| 真实数据结论 | `datasets/scores.csv` 30 条：期中均分 75.43、期末均分 77.33、及格率 93.3% | table 03 |

## 视觉自验

agent-browser 的常驻守护进程在本机多次静默 SIGTERM（与 `series-contract.md` 记录一致）。本次改用系统自带 Edge 无头模式逐节截图，路径已验证可靠：

```bash
# 把目标页复制一份，加 :target 只显示某一节（并给各节打 id）
python - <<'PY'
import re
h=open('python-list-guide.html',encoding='utf-8').read()
h=h.replace('<header>','<header id="hdr">',1)
n=[0]
h=re.sub(r'<section>',lambda m:(n.__setitem__(0,n[0]+1) or '<section id="s%d">'%n[0]),h)
h=h.replace('</head>','<style>\n.wrap > *{display:none}\n.wrap > *:target{display:block}\nbody{padding-top:0}\n</style>\n</head>',1)
open('_shots/v_list.html','w',encoding='utf-8').write(h)
PY

# 逐节截图（注意路径必须是 Windows 风格，MSYS 的 /c/... 会被判为"找不到路径"）
EDGE="/c/Program Files (x86)/Microsoft/Edge/Application/msedge.exe"
"$EDGE" --headless=new --disable-gpu --hide-scrollbars \
  --window-size=820,800 --virtual-time-budget=2000 \
  --user-data-dir="C:\\…\\_shots\\ud" --screenshot="C:\\…\\_shots\\r_list.png" \
  "file:///C:/…/_shots/v_list.html#s2"
```

覆盖套路：

- 想一次看到**首屏 + 面包屑 + 上下页 + footer**：把 `.wrap > section{display:none}`，四者会挤在一起，一屏看完两处导航；
- 想验证**答题反馈样式**：进 `#s6` 后注入 `setTimeout(()=>pick(0),50)` 自动点一个错选项，一张图同时看到绿/红两态与解析。

本次截图发现的缺陷（已修复）：

1. operators 流程图中 `sum(...) / len(...)` 在 151px 宽的格子里顶到右边框 → 改为 `sum / len`；
2. table 页 `rows["final"]` 一行文字挤边框 → 缩短为两行排布；
3. 三处 caption 折行后留下孤立单字 → 收短文案；
4. 4 个页面的「系列首页」原写作 `../index.html`，实际 hub 在同一目录 → 全部改为 `index.html`（真 bug，内部链接扫描发现）。
