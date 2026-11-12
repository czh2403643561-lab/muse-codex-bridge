# 项目：暗影精灵 OMEN 体检 / 优化 / 调试（中途接入信箱）

- 机器：HP OMEN 16-b0xxx（暗影精灵7），i7-11800H，核显 8086:9A60，RTX 3050 Ti，16GB，512GB 三星 NVMe，原装单盘
- 定位：闲置退役机、玩票性质；最终目标是 Windows + macOS 双系统、在 macOS 里跑 Codex 做开发/自动化。主力机（RTX 5060）不装黑苹果，此线已关，勿重提。
- 接入时点：2026-11-12 上午。Codex 正在本机执行「从硬件到软件的全面测试调试与优化」，做到一半接入本信箱。此前进度以下方已知事实为准，此后进度由 Codex 在报告文件里补齐。

## 已知事实（2026-11-11 第一阶段体检，Codex 出具、Muse 已判读）
- 存储链路不稳有日志实锤：2026-08-09–25 共 11 次 iaStorVD 129（VMD 控制器重置）+ 19 次 disk 153（I/O 重试），多组同秒；08-13 一次 Kernel-Power 41。凶手范围：SSD 本体 / VMD 控制器与驱动 / PCIe 链路，未定性到 SSD 本体。
- SMART 未读到：盘在 Intel VMD 后面，smartmontools 读取失败。未读到 ≠ 没问题，不许当作零。
- F2 基础版诊断 Storage Tests 报「No hard drive installed」，退出后 Windows 正常进入、无报错。判定：基础版诊断同样看不见 VMD 后的盘，此路作废，不能据此判盘死/盘好。
- 第一阶段结论：暂不放行装机。

## 待 Codex 补齐 / 未决
1. 这块三星 SSD 的确切型号（MZVL… 完整字符串）。若是 PM981a，是 Dortania 点名的 macOS 问题盘；PM9A1 则无此问题。此项未查明前装机不放行。
2. 用支持 VMD 的启动环境（Linux U 盘）读原始 NVMe SMART：Critical Warning、Media Errors 为决定性数据。
3. 内存测试本轮未跑。
4. 当前这轮「优化 + 硬件到软件测试调试」的具体清单与已完成部分——接入后第一份报告必须回填：现在做到哪一步、已动了什么、正在跑什么。

## 硬性禁区 / 注意事项
- Windows 不抹：只压缩分区腾空地，macOS 只装进空地。Windows 是 Codex 执行端、诊断工具与回退底盘。
- 关 VMD 前必须先在 Windows 侧做好切换准备并验证能开机；直接关 VMD 会让现有 Windows 无法启动。
- 动手装机前先把 OMEN Gaming Hub 显卡模式切到「混合模式」；独显直连下 macOS 点不亮内屏。
- 核显路线走 WhateverXe；9A60 在其后端名单内，但 H45 未实测，加速是赌点。禁止套用联想小新 Air 14 的 EFI。
- 3050 Ti 在 macOS 无驱动，装机时屏蔽；HDMI/miniDP 大概率走独显，外接屏希望主要在雷电4口，未验证前不买屏。
