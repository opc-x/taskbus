# taskbus — Agent 指令

## 这是什么

taskbus 是 OPC-X 的业务任务总线。所有任务以 GitHub Issue 为载体，按螺旋执行协议运转。

## 五阶段执行链

```
O01 决策  →  O03 需求  →  O04-07 执行  →  O08 验收  →  O10 反馈
  开 master     开 child      Cursor 跑       verify       关单+复盘
```

## Agent 操作规范

### 开单（O01 → O03）
- master issue：定义靶心 + 本圈边界
- child issue：按 `protocol/issue-schema.md` 结构生成
- 每个 child 必须挂载 master 编号

### 执行（O04-07）
- 派发给 Cursor agent 并行跑
- 每个 child issue 对应一个 Cursor agent
- 执行完 POST report 到 issue comment

### 验收（O08）
- T1：命令跑通 → 期望值匹配
- T2：AI 推理置信度 ≥ 阈值
- T3：人工操作步骤
- 全过才关单

### 反馈（O10）
- 关单时写 retro comment
- 未达靶心 → 开下一圈
- 命中靶心 → 标记 milestone 完成

## 禁止行为

- ❌ 没有 AC 就开 child issue
- ❌ T1 未通过就关单
- ❌ 跳过 O01 直接开 child
