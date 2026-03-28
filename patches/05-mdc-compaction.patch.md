# PATCH 05: 跨会话裁决落盘节 — 新增 Compaction 与 CHAIN-STATE 子节

**目标文件**: `.cursor/rules/hajimidog-4plus1-swarm.mdc`
**位置**: `## 跨会话裁决落盘与组合回归防控` 节内

## 在「与自动化的关系」子节**之前**，插入新子节

```markdown
### Compaction 与 CHAIN-STATE 的关系

- 冻结条 compaction（active→superseded/archived/invalidated 批转）须同步更新 **CHAIN-STATE.md §B**（若已启用）。  
- compaction 后须验证 §A 精简下限区完整（active P0 计数 + 目标句），**不匹配则阻塞后续 Task**。  
- 详见技能 `22` §4–§5。
```
