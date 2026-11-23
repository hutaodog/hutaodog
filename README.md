<div align="center">

# Ayanami · 项目导航

**13 个公开仓库，按用途分类 —— 点名字直达**

<sub>桌面工具 · DeepSeek Harness 插件 · 游戏自动化 · 客户端改造 · 服务镜像</sub>

</div>

---

## 目录

| | 分类 | 内容 |
|:--|:--|:--|
| 🖥️ | **[桌面工具](#️-桌面工具)** | 证件照排版、软件汉化 |
| 🔌 | **[DeepSeek Harness 插件](#-deepseek-harness-插件)** | 网络分流代理、语音输入 |
| 🎮 | **[游戏自动化](#-游戏自动化)** | 赛车游戏脚本、Minecraft 备份 Mod |
| 📱 | **[客户端改造](#-客户端改造)** | 抖音 4K 全平台（PC + 手机网页 + 安卓） |
| 📚 | **[服务与镜像](#-服务与镜像-fork)** | 网易云 API、Tauri 客户端、购票工具 |
| 🧪 | **[实验与归档](#-实验与归档)** | CI 试验场、占位仓库 |

---

## 🖥️ 桌面工具

| 项目 | 说明 | 技术栈 | 版本 |
|:--|:--|:--|:--|
| **[证件照排版助手](https://github.com/hutaodog/idphoto-layout-studio)** | 导入照片 → 自动抠图换底 → 按规格裁剪 → 排版到 5/6/7 寸相纸 → 导出可直接冲印。全程离线，CPU 推理约 1 秒/张 | `Python` · `PySide6` · `MODNet` · `ONNX` | `v1.6.6` |
| **[VD Streamer 汉化补丁](https://github.com/hutaodog/VirtualDesktop-Chinese)** | Virtual Desktop Streamer 简体中文界面补丁。自动定位程序、识别版本、备份原版，不依赖 Python / .NET Runtime | `C#` · `PowerShell` · `Go` | 无版本号<br><sub>commit 6 次</sub> |

<details>
<summary><b>证件照助手能做什么</b></summary>

- 人像抠图（MODNet）+ 人脸检测（MTCNN）本机推理，不上传任何照片
- 底色：白 / 标准蓝 / 红 / 深蓝 / 浅灰 / 申根浅灰 / 黑，以及任意自定义颜色
- 发丝、肩膀半透明边的内部空洞修补默认开启
- 三种打包形态：单文件 exe、便携 zip、安装包
- 唯一联网点是「检查更新」（只取一个版本号），可在「帮助」菜单关掉

</details>

---

## 🔌 DeepSeek Harness 插件

| 项目 | 说明 | 技术栈 | 版本 |
|:--|:--|:--|:--|
| **[DSH API 代理](https://github.com/hutaodog/dsh-api-proxy)** | 只给指定的 API 域名挂梯子。本机托管 mihomo 核心、导入 Clash 订阅、按域名精确分流，其余流量全部直连 | `Python` · `mihomo` | `v1.0.6` |
| **[DSH 语音输入](https://github.com/hutaodog/dsh-voice-input)** | 输入框右侧麦克风按钮，实时流式识别，结果追加进输入框不自动提交。支持硅基流动 / 千问两家 ASR | `JavaScript` | `0.1.0` |

<details>
<summary><b>为什么 API 代理不是「直接开全局梯子」</b></summary>

- **不碰系统**：mihomo 只监听 `127.0.0.1` 的随机端口，走普通 HTTP 代理协议
- **不开 TUN**：不需要 WinTUN 驱动，不需要管理员权限，不改系统代理设置
- **只代理该代理的**：网页抓取、联网搜索、HTTP MCP 全部保持直连
- **不用常开**：DSH 起来它才起来，关掉什么都没了

</details>

---

## 🎮 游戏自动化

| 项目 | 说明 | 技术栈 | 版本 |
|:--|:--|:--|:--|
| **[FH6Auto](https://github.com/hutaodog/FH6Auto)** | FH6 视觉脚本：截图识别游戏状态 → 判断是否进入目标页 → 触发键鼠 → 出错自动恢复。支持循环跑图、批量买车、超级抽奖、模块串联 | `Python` · `OpenCV` | `v1.1.7.3` |
| **[QuickBackupM Reforged 1.20.1](https://github.com/hutaodog/QuickBackupM-Reforged-1.20.1)** | Minecraft 1.20.1 备份 / 回档 Mod（仅 Fabric）。上游 v3 的社区移植分支，支持权限、热键、自动备份与服务器用法 | `Java` · `Fabric` · `NeoForge` | `v3.3.1-1.20.1` |

> FH6Auto 仅供 Python 自动化技术交流与学习使用，请勿用于商业用途或破坏游戏平衡。

---

## 📱 客户端改造

> 抖音 4K 改造：PC 一键补丁 + 手机网页油猴脚本 + 安卓壳 App，全在这一个仓库里。

| 项目 | 说明 | 技术栈 | 版本 |
|:--|:--|:--|:--|
| **[抖音 4K 改造（全平台）](https://github.com/hutaodog/douyin-4k-mod)** | PC 一键补丁 + **手机网页油猴脚本**（86KB 单文件）+ **安卓壳 App**（原生播放器、推荐流复刻），附 **24 篇开发记录**：从「为什么抖音默认不是 4K」到接口逆向总览、画质档位对照表、踩坑清单 | `JavaScript` · `Java` · `PowerShell` | `v1.1` |

<details>
<summary><b>三个端怎么用</b></summary>

- **电脑上看 4K** → `pc-oneclick/`，双击 `一键开启4K.cmd`，按提示走完（若抖音正在运行会自动关闭并在打完后重开）。还原双击 `恢复原版.cmd`。之前装过旧版可直接覆盖安装——安装器按标记先剥离旧补丁再追加，不会叠加两份。
- **手机浏览器上看 4K** → `mobile-web/douyin-4k.user.js`，Tampermonkey / Kiwi 装油猴脚本，浏览器必须切「桌面版网站」（移动版网页只给 720P 水印流）。
- **手机原生 App** → `mobile-app/`，系统 WebView 打底 + 原生 MediaPlayer 硬解 HEVC，已在 Redmi K40 实测 3840×2160 出画面。

实机效果以解码尺寸为准，不以「超清 4K」标签作为画质证据；PC 版按 `Alt+I` 可看真实解码分辨率。

</details>

<details>
<summary><b>想搞懂原理看这里</b></summary>

`docs/` 下 **24 篇**从零到定稿的开发记录，包括：为什么抖音默认不是 4K、接口逆向总览、画质档位对照表、安卓壳 K40 实测、PC 高画质起播修复报告、以及一路踩过的坑和失败的尝试。

</details>

---

## 📚 服务与镜像 (Fork)

> 这三个是上游项目的完整备份 / 自用版本，原作者与上游链接一并标注。

| 项目 | 上游 | 说明 | 技术栈 | 版本 |
|:--|:--|:--|:--|:--|
| **[Ayanami-api-enhanced](https://github.com/hutaodog/Ayanami-api-enhanced)** | [NeteaseCloudMusicApiEnhanced](https://github.com/NeteaseCloudMusicApiEnhanced/api-enhanced) | 网易云音乐 API 增强版，自原版 v4.28.0 后自行维护。**391 个接口文件**，npm 发布 `@neteasecloudmusicapienhanced/api` | `JavaScript` · `Node.js` | `4.32.0` |
| **[HGhub](https://github.com/hutaodog/HGhub)** | [bashirian777/HGhub](https://github.com/bashirian777/HGhub) | YellowFruit 第三方客户端，基于 Rust + Tauri 2 的跨平台界面实践 | `TypeScript` · `Rust` · `Tauri 2` | `1.2.1` |
| **[biliTickerBuyBackup](https://github.com/hutaodog/biliTickerBuyBackup)** | [mikumifa/biliTickerBuy](https://github.com/mikumifa/biliTickerBuy) | B 站会员购购票辅助工具的完整备份 | `Python` · `PyQt` | `2.15.17` |

> 这三个都没有发 GitHub Release，版本号取自仓库内的 `package.json` / `pyproject.toml`。

---

## 🧪 实验与归档

| 项目 | 说明 | 状态 |
|:--|:--|:--|
| **[build-ijk](https://github.com/hutaodog/build-ijk)** | ijkplayer 的 CI 构建试验场，用于验证 `.so` 收集与 Java 源码打包流程 | 仅含 1 个 workflow |
| **[bilibilixaizai](https://github.com/hutaodog/bilibilixaizai)** | 占位仓库 | 空 |

---

## 📌 最近更新

| 更新日 | 项目 |
|:--|:--|
| 2026-11-16 | [抖音 4K 改造](https://github.com/hutaodog/douyin-4k-mod) — 高画质 HEVC 起播修复 |
| 2026-10-22 | [证件照排版助手](https://github.com/hutaodog/idphoto-layout-studio) — v1.6.6 去掉照片列表、修复拖放 |
| 2026-10-16 | [DSH API 代理](https://github.com/hutaodog/dsh-api-proxy) — v1.0.6 |
| 2026-09-11 | [DSH 语音输入](https://github.com/hutaodog/dsh-voice-input) — 首个版本 |
| 2026-08-22 | [VD Streamer 汉化补丁](https://github.com/hutaodog/VirtualDesktop-Chinese) — BAML 本地化实现 |
| 2026-08-13 | [QuickBackupM Reforged](https://github.com/hutaodog/QuickBackupM-Reforged-1.20.1) — v3.3.1 移植完成 |
| 2026-06-15 | [FH6Auto](https://github.com/hutaodog/FH6Auto) — v1.1.7.3 选车逻辑重构 |

---

## 关于

<div align="center">

**另有 11 个私有仓库**（开发中 / 个人自用，含游戏自动化生态与 Minecraft 模组移植），不在此页列出。

<sub>本页为手工整理的导航，最后更新 2026-11-23</sub>

</div>
