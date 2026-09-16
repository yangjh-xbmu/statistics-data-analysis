# LLM Wiki 每日维护自动化 — 执行记忆

## 2026-09-16（首次记录）
- 结果：health 20 页全绿；lint 0 断链 / 0 缺失实体(3+) / 修复前 4 个稀疏页、修复后 0
- 自动修复：4 个稀疏页补出链（LostInTheMiddle→ContextWindow、ReAct→ContextEngineering、AndrejKarpathy→RAG、WorkBuddy→ContextWindow）
- raw/ 无新增源（6 份手册已于 09-09 全部 ingest）
- Top 5：渐进式披露 / 检索式练习 / 子代理与上下文隔离 / 费曼学习法 / 自动记忆
- 待宏哥确认：① 5 个候选中勾选建页 ② wiki 仓库大量未提交变更

## 2026-09-16（第二次·用户指令：提交 + 全部创建 + 改为全自动）
- 建 5 个 concept 页：ProgressiveDisclosure / Subagent / AutoMemory / RetrievalPractice / FeynmanTechnique
- 加反向链接：AgentSkills/ContextEngineering/ContextWindow→ProgressiveDisclosure；ContextEngineering/ContextWindow→Subagent；AgentMemory→AutoMemory
- index.md Concepts 9 → 14；复检 25 页 / 0 断链 / 0 稀疏 / 0 缺失实体
- 首次 git commit：ee3385b（33 文件，3812+）。**远端 origin = SamurAIGPT/llm-wiki-agent 上游，无 push 权限，只 commit 不 push**
- prompt 已改为全自动：零询问、Top2 直接建页（每日上限 2 页）、raw 新文件自动 ingest、结束前自动 commit、写本文件

## 稳定经验（下次沿用）
- `find_orphans` 恒报 6 source + 1 synthesis，因 index.md 用相对 Markdown 链接而非 [[wikilink]]，属设计内假阳性，不必修
- `find_missing_entities` 只统计 [[wikilinks]]，纯文本高频词（如「渐进式披露」8 处）不会命中，需人工补查
- 修复稀疏页优先复用已有 hub（ContextWindow / ContextEngineering / RAG），不要为凑数造弱链接
- 网络：curl 直连返回 000，需用 WebFetch / WebSearch 做外部验证

## 待办结转
- [x] 渐进式披露 concept 页（2026-09-16 已建）
- [x] 其余 4 个候选页（2026-09-16 已全部建完）
- [x] git 提交 wiki/ 与 raw/guides/（2026-09-16，commit ee3385b）
- [ ] 5 个新页 sources 为空，待 ingest 官方源后补引用
- [ ] 若需远端备份：先 fork 到自己账号再改 remote，勿直接 push 上游
