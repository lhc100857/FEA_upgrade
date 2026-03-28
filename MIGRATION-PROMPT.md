# 一键移植提示词

> 将以下内容完整复制并粘贴到目标机器的 Cursor Agent 对话中。

---

免子代理，免 R3R4，直接执行以下移植任务。这是一组已在源仓库通过满编蜂群验证（10 个 Task + R3/R4a/R4b 写码回合）的「主帅上下文生命周期管理协议 v2」升级补丁。

## 任务：移植「主帅上下文生命周期管理协议 v2」

请按以下顺序执行 4 步。所有补丁文件在 `migration-context-lifecycle-v2/` 目录下。

### 第 1 步：复制新文件

1. 读取 `migration-context-lifecycle-v2/new-files/22_主帅上下文生命周期管理.md`，将其**原样写入** `.cursor/skills/hajimi-dog/03_AI行为准则/22_主帅上下文生命周期管理.md`
2. 创建目录 `.cursor/swarm/chains/`（若不存在）
3. 读取 `migration-context-lifecycle-v2/new-files/_CHAIN-STATE-TEMPLATE.md`，将其**原样写入** `.cursor/swarm/chains/_CHAIN-STATE-TEMPLATE.md`

### 第 2 步：应用 .mdc 补丁

按顺序读取并应用 `migration-context-lifecycle-v2/patches/` 下的 8 个补丁文件（01 到 08）。每个补丁包含：目标文件路径、定位方法（查找字符串或节标题）、要插入或替换的文本。

**关键原则**：
- 先读目标文件相关区段，确认当前版本的文本特征
- 使用 StrReplace 工具精确定位并替换/插入
- 若目标文件的文本与补丁中的「查找」不完全匹配（不同版本的措辞差异），根据节标题和上下文定位到语义等价位置插入
- 补丁应用顺序：01（description）→ 02（形状保持）→ 03（续聊）→ 04（蜂群记忆）→ 05（compaction）→ 06（Sub-agent）→ 07（规范栈）→ 08（索引）

**8 个补丁的摘要**：

| 补丁 | 目标 | 操作 |
|------|------|------|
| 01 | `.mdc` description | 追加触发词 + 技能22引用 |
| 02 | `.mdc` 形状保持节 | 插入冻结条四态 + COND上限 2条 |
| 03 | `.mdc` 续聊节 | 替换全量重述为 delta 增量 |
| 04 | `.mdc` 蜂群记忆节 | 插入 CHAIN-STATE 锚点 + 会话切割 2条 |
| 05 | `.mdc` 落盘节 | 插入 Compaction 子节 |
| 06 | `.mdc` Sub-agent 节 | 追加 EP 回流约束 1条 |
| 07 | `.mdc` 规范栈节 | 追加技能22到引用列表 |
| 08 | `SKILL.md` 索引 | 插入技能22条目 |

### 第 3 步：验证

```bash
cd .cursor/skills/hajimi-dog
python skills_linter.py
```

期望：退出码 0，0 新增 error（已有 warning 可忽略）。

### 第 4 步：确认

完成后列出所有改动的文件及行数变化。

---

**注意事项**：
- 若目标仓库的 `.mdc` 版本与补丁描述有差异，以节标题定位为准，补丁内容放在语义正确的位置
- 不要修改补丁中新文件的内容
- 不要触碰不在补丁范围内的 `.mdc` 条款
- 如果目标仓库没有 `.cursor/swarm/` 目录，先创建
