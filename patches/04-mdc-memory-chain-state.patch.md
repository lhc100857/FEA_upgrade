# PATCH 04: 蜂群记忆与跨轮接力 — 新增 CHAIN-STATE 锚点 + 会话切割

**目标文件**: `.cursor/rules/hajimidog-4plus1-swarm.mdc`
**位置**: `### 蜂群记忆与跨轮接力` 节内

## 修改 A：在该节正文第一条之前（即在「要解决的问题」段落之后），插入新首条

```markdown
- **CHAIN-STATE.md 锚点**：每条任务链**建议**维护一份 `CHAIN-STATE.md`（路径见技能 `22` §2），作为**工作记忆锚点**。前 20 行（§A 精简下限区）须零 Read 即可回答目标句 + P0 + 裁决 + 三字段。模板：`.cursor/swarm/chains/_CHAIN-STATE-TEMPLATE.md`。  
```

## 修改 B：查找「多窗口文件总线」条，在其**之前**插入新条

```markdown
- **会话切割与接力**：主帅窗口达到 **≥15 轮（军团）/ ≥20 轮（蜂群）** 或 **≥50k token 估算** 时，**强烈建议**切割会话；同一 P0 连续 3 轮 FAIL 时**强制切割**并 R1+R2 重入。切割时须写 **HANDOFF** 文件（路径 `.cursor/swarm/chains/{CHAIN-ID}/HANDOFF-R{N}.md`，内容 = active 冻结条 + P0 + Gate 进度 + 最近 2 轮 delta + 下轮指令）。新会话起手优先级：**HANDOFF > CHAIN-STATE > 从头**。  
```
