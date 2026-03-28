# PATCH 02: 形状保持节 — 新增冻结条四态 + COND 上限

**目标文件**: `.cursor/rules/hajimidog-4plus1-swarm.mdc`
**位置**: `### 形状保持与防目标漂变（统帅强制 · 薄条款）` 节内

## 在「定义」条之后、「用户明示优先」条之前，插入以下 2 条

```markdown
- **冻结条四态生命周期**：**active**（当前有效）→ **superseded**（被新条替代，须指向替代条 ID）→ **archived**（compaction 时仅留 1 行墓碑；墓碑 >20 行时清理到最近 5 行）→ **invalidated**（被 BREAKING 变更推翻，关联 Gate 裁决须重验）。冻结条**只增不减**的问题通过生命周期管理解决；详见技能 `22`。  
- **COND 追踪硬上限**：同时 open 的 COND_PASS 条件 **≤8 条**；第 9 条到来时最旧 open → expired 并记入风险登记。  
```
