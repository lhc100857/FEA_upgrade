# 主帅上下文生命周期管理协议 v2 — 移植包

## 概述

解决主编排者（统帅/Orchestrator/Commander）窗口上下文膨胀导致的幻觉、部分遗忘与形状漂变问题。引入三层上下文模型、CHAIN-STATE.md 锚点、增量 delta 汇流、冻结条四态生命周期、子代理回流约束、常驻内容分级摘要、会话切割与接力。

## 两套移植方案

### 方案 A：通用版（推荐 · 任意平台）

**适用**：目标系统有类似的多代理治理体系，但路径/命名/措辞不同；或者不是 Cursor。

```
universal/
├── PROTOCOL.md                    ← 完整协议（平台无关 · 独立可读）
├── CHAIN-STATE-TEMPLATE.md        ← 状态锚点模板（通用版）
├── INTEGRATION-GUIDE.md           ← 6 个语义注入点定位指南
└── MIGRATION-PROMPT-UNIVERSAL.md  ← 一键提示词（任意 AI Agent 可用）
```

**用法**：将 `universal/` 文件夹拷到目标系统，将 `MIGRATION-PROMPT-UNIVERSAL.md` 内容粘贴给 AI。

### 方案 B：精确补丁版（本仓库同构）

**适用**：目标系统与本仓库结构完全一致（`hajimidog-4plus1-swarm.mdc` + `hajimi-dog/` 技能树）。

```
new-files/
├── 22_主帅上下文生命周期管理.md   ← 直接复制到 03_AI行为准则/
└── _CHAIN-STATE-TEMPLATE.md      ← 直接复制到 .cursor/swarm/chains/

patches/                           ← 8 个精确文本补丁
├── 01-mdc-description.patch.md
├── 02-mdc-shape-preserve.patch.md
├── 03-mdc-continuation.patch.md
├── 04-mdc-memory-chain-state.patch.md
├── 05-mdc-compaction.patch.md
├── 06-mdc-subagent-ep.patch.md
├── 07-mdc-normstack.patch.md
└── 08-skill-index-entry.patch.md

MIGRATION-PROMPT.md                ← 一键提示词（Cursor Agent 专用）
```

**用法**：整文件夹拷到目标仓库根，将 `MIGRATION-PROMPT.md` 内容粘贴给 Cursor Agent。

---

## 方案 A 详细步骤

1. 拷贝 `universal/` 到目标系统
2. 将 `MIGRATION-PROMPT-UNIVERSAL.md` 内容粘贴给 AI
3. AI 会先探索目标体系结构，再按 `INTEGRATION-GUIDE.md` 的 6 个语义注入点自适应集成
4. 验证：规则文件无矛盾 + 路径一致 + linter（若有）通过

## 方案 B 详细步骤

1. 拷贝整文件夹到目标仓库根
2. 将 `MIGRATION-PROMPT.md` 内容粘贴给 Cursor Agent
3. AI 按 8 个精确补丁逐一应用
4. 验证：`python skills_linter.py` 退出码 0
