# Muse ↔ Codex 信箱仓（全自动版 v1）

目的：Codex（用户本机）在项目里干活，每完成一个阶段自动写报告并 push 到本仓；Muse（云端）自动巡查本仓，收到新报告后审阅并主动转发给用户。用户不转达、不催促、不打开 ChatGPT 远程功能。

## 目录
- `inbox/codex/` — Muse 投给 Codex 的任务卡 / 修改单
- `inbox/muse/` — Codex 投给 Muse 的报告 / 求助（每个项目一份滚动报告文件，追加不新建）
- `projects/<项目名>/PROJECT.md` — 项目状态页：目标、已知事实、已完成、待办、禁区
- `shared/` — 双方共用文档（大文件放链接，不堆二进制）
- `archive/` — 已完成任务卡按月归档

## 任务卡格式（Markdown，文件名 `YYYYMMDD-主题简写.md`）
```
---
from: muse | codex
to: codex | muse
status: new | ack | doing | done | blocked
created: YYYY-MM-DD HH:MM
project: omen-optimization
---
# 一句话任务名
要解决什么 / 输入在哪 / 期望输出什么、放到哪 / 成功标准 / 禁区
```

## 全自动规则
1. Codex：每完成一个阶段、或被卡住超过一轮尝试，立刻更新本项目的报告文件（`inbox/muse/<项目>-report.md`，追加一段：时间、做了什么、证据、结论、下一步）并 push。不要等整个项目做完才报。
2. Codex：每次新开对话或恢复工作，先 `git pull` 本仓，看 `inbox/codex/` 有没有 Muse 的新卡；先处理新卡再继续旧活。
3. Muse：定时巡查本仓新提交；发现新报告后审阅、提炼，转告用户；发现 blocked 立刻转告，不等下轮。
4. 同一任务只用一张卡，后续沟通在卡内追加，不另开新卡刷屏。
5. 敏感信息（密码、密钥、账号、验证码）永不进仓。
6. 动钱、删数据、改分区、关安全设置等不可逆动作，Codex 必须先在报告里写明并停下等用户在 Muse 侧批准，不得自行执行（项目卡禁区为准）。
