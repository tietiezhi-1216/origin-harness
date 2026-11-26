<p align="center">
  <img src="./logo.png" width="128" height="128" alt="Origin Harness Logo" />
</p>

<h1 align="center">Origin Harness</h1>

> Native, pure-agent AI Harness for macOS — 告别 Electron 卡顿，回归纯原生极致体验。

**Origin Harness** 是一个专为 Apple 生态打造的原生 AI Agent 编排与工作台（Harness）。不依赖第三方 API 直连，采用**纯代理（Pure-Agent / PTY & 进程编排）**模式统一驾驭本地各类 AI CLI 与 Agent 工具，提供原生的中文体验、极低内存占用以及未来面向 iOS / Android 的远程控制能力。

---

## 核心特性（规划中）

- **纯原生高性能**：拒绝 Electron，采用 **Swift（SwiftPM + SwiftUI / AppKit）** 构建，支持 120Hz ProMotion 丝滑渲染与极低内存占用。
- **纯代理编排**：不绑定单一厂商 API，通过 PTY / 守护进程统一托管各类本地 AI CLI 与 Agent，集中处理流式输出、权限审批与任务状态。
- **Daemon-First 架构**：后台常驻守护进程（`origind`）驱动核心会话与 `git worktree` 隔离，关闭桌面窗口后任务依然持续运行。
- **原生中文体验**：从底层交互、快捷键到界面排版完整适配中文工作流。
- **多端远程控制**：Mac 端作为核心算力与执行宿主，后续支持 **iOS** 与 **Android** 远程连接，随时随地查看进度与审批命令。

---

## 架构概览

```text
  [ macOS App (SwiftUI + AppKit) ]  <-- Unix Socket --> +----------------------+
  [ iOS / Android 远程客户端     ]  <-- WebSocket ----> |    Origin Daemon     |
  [ 终端 CLI (`origin`)          ]  <-- Unix Socket --> |      (origind)       |
                                                        +----------------------+
                                                            |       |       |
                                                          [PTY]   [PTY]   [Worktree]
```

## 路线图

- [ ] **Phase 1 — Core & CLI**：完成 `OriginCore`、`OriginCLI` 与 `OriginDaemon` 基础骨架（PTY 托管、会话持久化、Git Worktree 隔离）
- [ ] **Phase 2 — macOS App**：基于 SwiftUI + AppKit 构建原生桌面端，支持高速流式 Markdown 与 Diff 渲染
- [ ] **Phase 3 — Remote Clients**：开放安全 WebSocket 网关，推出 iOS 与 Android 远程控制端

## License

TBD
