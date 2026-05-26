# Skill 路由规则

> 贴着人说话方式写 skill 描述，让 LLM 意图识别零误判。

## 路由原则

```
用户意图（自然语言）
        │
LLM 意图识别
        │
匹配 skill 描述
        │
执行 skill
```

## taskbus 核心 Skill 映射

| 触发场景 | Skill | 说明 |
|---------|-------|------|
| 要开始做一件事/有个想法要推进 | `O01-decide` | 开 master issue，定靶心 |
| 要把任务拆细/要写需求 | `O03-breakdown` | 拆 child issues |
| 要派给 Cursor 执行 | `O04-dispatch` | 派发 Cursor agents |
| 要验收/要关单/做完了 | `O08-verify` | 跑 T1/T2/T3 验收 |
| 这圈做完了要复盘 | `O10-retro` | 写反馈，决定升圈 |

## Skill 描述写法规范

```
✅ 正确：「用户要付款/订阅/购买时用这个」
❌ 错误：「调用 Stripe API 创建 checkout session」

✅ 正确：「这圈做完了要复盘/总结/看看做了啥」
❌ 错误：「执行 O10 反馈节点写 retro comment」
```

## 路由失败的唯一原因

```
skill 描述用技术语言写
    │
用户用自然语言说
    │
语义 gap → miss
    │
解法：重写 skill 描述，贴人说话方式
```
