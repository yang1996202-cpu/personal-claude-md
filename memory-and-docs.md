---
last_updated: 2026-06-26
status: Active
scope: 记忆持久化、文档组织
trigger: 当 Agent 需要保存记忆、组织文档或修改身份文件时加载
---

# 记忆与文档规则

## 记忆工具：默认 gbrain
- 默认记忆工具是 **gbrain**（本地 PGLite，已配为 MCP server）。不再用 Nowledge Mem / nmem（太重、需额外服务，已弃用）。
- 主文件第 14 节是记忆分工的权威源；本文件只补操作细则。

## 何时保存
- 用户明确说“保存”“记住”“沉淀”“持久化” → 必须保存。
- 踩坑、反直觉发现、SOP、决策理由 → 主动保存，不等提醒。
- 只对本对话有意义、不跨会话的，不保存。

## 怎么保存（按优先级）
1. **gbrain MCP**（首选）：`mcp__gbrain__put_page`，slug 短横线命名，frontmatter 设 `type: reference/feedback/project`。无 `capture` 工具，不要调 `gbrain__capture`。
2. **gbrain CLI**：`gbrain capture --stdin --slug <name> --type <t>` 或 `gbrain put <slug>`。
3. **项目级本地文件**：`~/.claude/projects/<project>/memory/`，仅 gbrain 不可用时 fallback。

## 怎么检索
- 优先 `mcp__gbrain__query` / `mcp__gbrain__search`；其次 `gbrain query "问题"`。

## “想不起来”的对策
- 必须**每次生效**的硬纪律 → 写进 CLAUDE.md 体系（主文件或 ~/docs/ 子文档），**不进 gbrain**。gbrain 按需检索，不保证每次想起。
- 大块、低频、参考性的背景 → 进 gbrain（省 context）。

## 修改身份文件
- 改 soul.md / user.md / CLAUDE.md / ~/docs/ 子文档 → 先告知用户具体改什么（主文件第 16 节硬暂停）。
- 禁止把持久记忆写进 settings.json、~/CLAUDE.md 等配置文件。

## 文档组织
- 知识类文档可用 `[[文件名]]`、`#标签` 和 YAML frontmatter。
- 项目工程文档优先遵守仓库既有结构，不为知识管理形式破坏工程目录。
- 少用深层文件夹；长期检索的内容用标签、链接或索引页。

## 安全
- 不在记忆文件中存储密码、API key、token。
