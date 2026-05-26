# taskbus

Issue-driven task bus — 围绕螺旋执行协议运转的业务任务总线

<div align="center">
  <img src="https://raw.githubusercontent.com/opc-x/opc-x/main/docs/spiral.svg" width="420" alt="OPC-X 螺旋执行协议" />
</div>

## 是什么

taskbus 以 GitHub Issue 为原子任务单元，用 LLM 意图识别驱动 skill 路由，按螺旋执行协议推进业务目标。

```
靶心（业务目标）
      │
每圈 = 一批 issue 闭环
      │
决策 → 需求 → 执行 → 验收 → 反馈 → 下一圈
O01     O03   O04-07   O08    O10
```

## 结构

```
taskbus/
├── protocol/
│   ├── spiral.md        螺旋执行协议规范
│   ├── issue-schema.md  issue 结构标准（LLM可消费）
│   └── skill-routing.md skill 路由规则
└── templates/
    ├── master-issue.md  master issue 模板
    └── child-issue.md   child issue 模板
```

## 核心原则

- **靶心驱动**：每个 issue 必须能回答「为什么做」
- **LLM可消费**：issue 结构贴人说话方式，意图识别零误判
- **只做加法**：每圈在上一圈基础上推进，不推翻重来
- **闭环验收**：T1机器验 / T2 AI验 / T3人工验，缺一不可
