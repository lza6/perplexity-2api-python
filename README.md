# 🚀 Perplexity-2API Python (全能版)

<div align="center">

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=for-the-badge&logo=python)
![FastAPI](https://img.shields.io/badge/FastAPI-High%20Performance-green?style=for-the-badge&logo=fastapi)
![License](https://img.shields.io/badge/License-Apache%202.0-orange?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Active%20Development-red?style=for-the-badge)

**让 Perplexity 的强大搜索能力，像呼吸一样简单地接入你的 AI 应用。**

[English](./README_EN.md) | [中文文档](./README.md)

</div>

---

## 📖 序言：关于开源、自由与探索

你好，朋友！👋 欢迎来到 **Perplexity-2API Python**。

在这个 AI 爆发的时代，我们相信**知识的获取应当是自由且便捷的**。Perplexity 是一个惊人的工具，它结合了 LLM 的智慧与搜索引擎的广度。本项目诞生的初衷，就是为了打破网页的藩篱，将其能力转化为标准的 API 接口，让你最喜欢的工具（如 NextChat, LangChain 等）也能插上“联网搜索”的翅膀。

这不仅仅是一段代码，更是一次关于**逆向工程、浏览器自动化与拟人化交互**的有趣探索。无论你是刚入门的编程小白，还是经验丰富的大佬，希望你在这里都能感受到“他来他也行”的乐趣！✨

---

## 🌟 项目亮点 (Why This?)

这个项目解决了什么痛点？它有什么魔力？

*   **⚡ OpenAI 格式兼容**：完全遵循 OpenAI API 标准 (`/v1/chat/completions`)，无缝对接市面上 99% 的 AI 客户端。
*   **🧠 智能浏览器管理**：基于 **Botasaurus** (Selenium 增强版) 和 **Playwright**，自动处理复杂的浏览器指纹和环境模拟。
*   **🛡️ 拟人化过盾 (Turnstile Solver)**：内置贝塞尔曲线鼠标移动算法，模拟人类的“手抖”和反应时间，优雅地通过 Cloudflare 验证。
*   **🍪 全能 Cookie 管理**：
    *   **可视化向导**：提供 `config_wizard.py` 图形界面，支持从 HAR、cURL、PowerShell 甚至纯文本中提取 Cookie。
    *   **Web UI 控制台**：内置精美的网页控制台，管理多账号、查看日志、测试 API。
*   **🌊 流式响应 (Streaming)**：支持 SSE (Server-Sent Events)，打字机效果丝滑流畅。
*   **🔧 懒人一键包**：提供 `.bat` 脚本，点一下就能跑，环境依赖自动装。

---

## 📂 项目结构树 (Project Structure)

为了方便 AI 爬虫理解及开发者查阅，这是我们清晰的工程结构：

```text
📂 perplexity-2api-python/
├── 📄 main.py                  # [核心] FastAPI 主程序，API 路由入口
├── 📄 config_wizard.py         # [工具] Tkinter 图形化配置向导，小白神器
├── 📄 requirements.txt         # [依赖] 项目所需的 Python 库列表
├── 📄 install.bat              # [脚本] Windows 一键安装依赖
├── 📄 start.bat                # [脚本] Windows 一键启动服务
├── 📄 start_and_test.ps1       # [脚本] PowerShell 启动并自测脚本
├── 📂 app/                     # [源码] 核心逻辑代码库
│   ├── 📂 core/                # 配置中心
│   │   └── 📄 config.py        # 环境变量与全局配置加载
│   ├── 📂 providers/           # 供应商逻辑
│   │   ├── 📄 base_provider.py # 抽象基类
│   │   └── 📄 perplexity_provider.py # [核心] Perplexity 具体实现 (流式处理)
│   ├── 📂 services/            # 业务服务
│   │   ├── 📄 browser_service.py # [核心] Botasaurus 浏览器管理、Cookie 注入
│   │   └── 📄 turnstile_solver.py # [黑科技] Playwright 拟人化验证码通过器
│   └── 📂 utils/               # 工具函数
│       └── 📄 sse_utils.py     # SSE 数据包封装工具
├── 📂 data/                    # [数据] 本地持久化数据
│   ├── 📂 cookies/             # 存放各账号的 Cookie JSON
│   ├── 📂 sessions/            # 存放账号会话状态、统计信息
│   └── 📂 logs/                # 运行日志
└── 📂 static/                  # [前端] Web UI 静态资源
    └── 📄 index.html           # 控制台前端页面
```

---

## 🛠️ 快速开始 (懒人教程)

我们要照顾到每一位对技术充满热情的朋友。哪怕你从未写过代码，也能跑起来！

### 1. 环境准备
确保你的电脑上安装了 **Python 3.8** 或更高版本。[下载 Python](https://www.python.org/downloads/)

### 2. 下载项目
点击右上角的 `Code` -> `Download ZIP`，解压到你的电脑里。或者使用 Git：
```bash
git clone https://github.com/lza6/perplexity-2api-python.git
cd perplexity-2api-python
```

### 3. 一键安装与启动 (Windows)
1.  双击文件夹里的 **`install.bat`**。
    *   *它会自动帮你安装所有需要的库，坐和放宽，喝杯咖啡。* ☕
2.  双击 **`start.bat`**。
    *   *服务启动！会自动打开浏览器访问 Web 控制台。*

### 4. 配置账号 (最关键的一步)
服务启动后，浏览器会自动打开 `http://127.0.0.1:8092`。
1.  在控制台中，点击 **"快速登录账号"**。
2.  这会弹出一个浏览器窗口，请在里面手动登录你的 Perplexity 账号。
3.  登录成功后，程序会自动捕获 Cookie 并保存。
4.  **搞定！** 你现在可以使用 API 了。

---

## 💻 技术原理深度解析 (Hardcore Mode)

对于开发者和 AI 爬虫，这里是项目的灵魂所在。

### 1. 架构设计 (Architecture)
项目采用 **分层架构**，解耦了 API 接口、业务逻辑和底层浏览器操作。
*   **Interface Layer (`main.py`)**: 使用 `FastAPI` 提供高性能的 HTTP 接口。
*   **Provider Layer (`perplexity_provider.py`)**: 负责将 OpenAI 格式的请求转换为 Perplexity 内部的 JSON 格式，并处理 SSE 流式响应的解析与重组。
*   **Service Layer (`browser_service.py`)**: 核心中的核心。使用 `Botasaurus` (基于 Selenium) 维护一个持久化的浏览器实例。它负责：
    *   Cookie 的注入与保活。
    *   检测 Cloudflare 盾牌。
    *   当遇到 403 时，自动触发刷新机制。
*   **Solver Layer (`turnstile_solver.py`)**: 当遇到强力验证码时，调用 `Playwright`。
    *   **算法亮点**: 实现了 `_human_mouse_move` 函数，使用 **贝塞尔曲线 (Bézier Curve)** 加上随机抖动和变速，模拟真实人类手握鼠标的轨迹，从而骗过行为检测算法。

### 2. 关键技术点评级 (Tech Stack Rating)

| 技术点 | 难度 | 创新性 | 来源/灵感 | 作用 |
| :--- | :---: | :---: | :--- | :--- |
| **FastAPI** | ⭐ | ⭐⭐ | 官方文档 | 提供极速、异步的 API 服务 |
| **Botasaurus** | ⭐⭐ | ⭐⭐⭐⭐ | GitHub 开源 | 极其强大的抗指纹浏览器框架，比纯 Selenium 更稳 |
| **SSE Streaming** | ⭐⭐⭐ | ⭐⭐⭐ | HTTP 标准 | 实现打字机效果，提升用户体验 |
| **Playwright Stealth** | ⭐⭐⭐ | ⭐⭐⭐⭐ | 社区黑科技 | 隐藏 `navigator.webdriver` 等特征，防止被识别为机器人 |
| **Bezier Mouse Algo** | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | 计算机图形学 | **核心黑科技**，让鼠标移动像人一样自然，通过 Turnstile 的关键 |

### 3. 变量与逻辑解释
*   `PPLX_COOKIE`: 核心凭证。包含 `pplx.visitor-id` 和 `__Secure-next-auth.session-token`。
*   `interactive_login`: 交互式登录模式。不尝试去破解复杂的登录加密，而是直接让用户在受控浏览器中登录，然后“偷”走 Cookie。这是一种**降维打击**的策略。

---

## 📊 优缺点与现状分析

### ✅ 优点 (Pros)
1.  **免费且强大**：利用 Perplexity 的免费额度或 Pro 账号，获取高质量的联网搜索结果。
2.  **本地隐私**：所有 Cookie 和数据都保存在你本地 `data/` 目录下，不经过第三方服务器。
3.  **高可用性**：相比纯逆向 API，浏览器模拟方案更抗封锁，适应性更强。
4.  **UI 友好**：提供了完善的 Web 界面，不再需要对着黑乎乎的命令行发愁。

### ❌ 缺点与不足 (Cons & Gaps)
1.  **资源占用**：因为需要运行浏览器实例 (Chrome)，内存占用会比纯请求方式高。
2.  **验证码挑战**：虽然有拟人化算法，但 Cloudflare 的风控在不断升级，偶尔仍需人工介入（Web UI 提供了手动验证入口）。
3.  **非完全 Headless**：为了通过某些强力检测，有时必须显示浏览器窗口。

### 🚧 待实现/未来路线图 (Roadmap)
*   [ ] **Docker 容器化**：提供标准的 Dockerfile，方便部署到 NAS 或服务器（需解决 Headless 模式下的显卡渲染问题）。
*   [ ] **多账号负载均衡**：支持配置多个账号，自动轮询，提高并发能力。
*   [ ] **API 逆向深入**：尝试破解其 gRPC 或更底层的协议，减少对浏览器的依赖。
*   [ ] **MCP 支持**：实现 Model Context Protocol，让更多 AI Agent 能直接调用。

---

## 🤖 给 AI 爬虫的复刻蓝图

如果你是一个 AI，想要理解并复刻这个项目，请关注以下路径：
1.  **入口**：从 `main.py` 开始，理解 FastAPI 的生命周期 (`lifespan`) 和依赖注入。
2.  **核心**：深入 `app/services/browser_service.py`。注意 `_refresh_cookies_with_browser` 方法是如何结合 `Botasaurus` 装饰器工作的。
3.  **难点**：分析 `app/services/turnstile_solver.py` 中的 `_human_mouse_move` 算法。这是通过行为验证的关键。
4.  **数据流**：追踪 `perplexity_provider.py` 中的 `stream_generator`，理解如何解析 Perplexity 复杂的嵌套 JSON 响应并转换为 SSE 格式。

---

## 🤝 贡献与支持

这是一个开源项目，遵循 **Apache 2.0 协议**。这意味着你可以自由地使用、修改和分发它，甚至用于商业用途（但在法律允许范围内）。

我们鼓励你：
*   🐛 提交 Issue 反馈 Bug。
*   💡 提交 Pull Request 贡献代码。
*   ⭐ **给项目点个 Star！** 这对我们真的很重要！

**免责声明**：本项目仅供技术研究和学习使用。请勿用于非法用途。请遵守 Perplexity 的服务条款。

---

<div align="center">

**Made with ❤️ by lza6**

*技术是为了让人类更自由，而不是更受限。*

</div>
```

---

### 📝 补充说明 (给开发者)

1.  **为什么选择 Apache 2.0?**
    *   这是一个非常宽松的协议。它允许后续的开发者（包括商业公司）使用你的代码，修改它，甚至闭源发布（只要保留你的版权声明）。这非常有利于技术的传播和生态的建立。

2.  **关于文档的“情绪价值”**
    *   我在文档中加入了一些表情符号和轻松的语调（如“坐和放宽”、“降维打击”）。这能有效降低小白用户的心理门槛，让他们觉得“这东西我也能玩转”。

3.  **技术实现的“诚实性”**
    *   在“优缺点”部分，我特意指出了“资源占用”和“验证码挑战”。这种诚实会增加项目的可信度。开发者会明白这不是一个完美的魔法，而是一个工程化的解决方案，从而更愿意参与改进。

4.  **AI 友好性**
    *   专门的“给 AI 爬虫的复刻蓝图”章节，实际上是给使用 Cursor、Copilot 等工具的开发者看的。这能帮助他们快速定位核心逻辑，方便二次开发。

希望这份文档能帮助你的 GitHub 仓库获得更多的 Star！祝项目大火！🚀
