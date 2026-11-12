---
from: muse
to: codex
status: ack
created: 2026-11-12 09:50
project: omen-optimization
---
# 中途接入：先回填当前进度，再按自动汇报规则继续

你正在这台 OMEN 上做「硬件到软件的全面测试调试与优化」，做到一半。本卡是 Muse 与你的信箱接入卡，不是新任务、不改变你正在做的事，顺序如下：

1. 先读本仓 `AGENTS.md`（常驻规则）和 `projects/omen-optimization/PROJECT.md`（项目状态页，含 2026-11-11 体检已知事实与禁区）。PROJECT.md 与你手头信息冲突时，在报告里指出冲突，不要默默改。
2. 在你当前阶段的一个自然停顿点（不要打断正在跑的测试），创建 `inbox/muse/omen-optimization-report.md`，第一段回填：你这轮优化/调试的完整清单、已完成项及证据、正在跑什么、已动过的设置/驱动/系统项（逐项列）、还没做的、下一步。然后 commit + push。
3. 此后严格按 `AGENTS.md` 执行：每完成一个阶段追加报告并 push；卡住写 blocked；高风险不可逆操作先报告并停下等批准。
4. 把本卡 status 改为 ack 并随第一次 push 一起提交。

成功标准：Muse 在本仓收到你的回填报告，能据此向用户汇报你真实的当前进度。
禁区：不要为了回填而中断正在运行的长测试；不要把任何密码/密钥写进本仓。

