# 佐罗斯AI · Zorrose-bot

一个纯前端实现的网页版 AI 聊天助手，由个人开发者**钟锦明（佐罗斯）**打造。基于浏览器原生能力与第三方大模型 API 构建，无需后端服务，部署即用。

> AI 调用由第三方大模型提供支持，对外统一以「佐罗斯AI」身份服务。

## ✨ 功能特性

### 核心对话
- **多轮对话**：保留上下文（最近 20 条消息），对话连贯自然
- **快捷回复**：预设关键词（如「你好」「你是谁」）触发即时响应
- **错误重试**：API 调用失败自动重试，最多 3 次
- **消息复制**：一键复制任意一条回复内容

### 交互体验
- **语音播报**：使用浏览器原生 `SpeechSynthesis` 朗读 AI 回复，可随时开关
- **主题切换**：深色 / 浅色双主题，默认浅色，偏好本地持久化
- **Toast 提示**：操作反馈以轻量提示条呈现，不打断对话
- **返回顶部**：长对话滚动后一键回顶
- **侧边导航**：抽屉式侧边栏，链接到作者其他子站

### 工程化能力
- **本地持久化**：对话历史、主题偏好、错误日志均存于 `localStorage`
- **调试面板**：隐藏入口（发送「测试」或侧边栏「调试」），查看运行时错误日志
- **防窥探机制**：禁用右键菜单与开发者工具快捷键
- **输入校验**：空消息输入框抖动提示，避免无效请求

## 🛠 技术栈

- **HTML / CSS / 原生 JavaScript**（无构建工具、无框架依赖）
- **Agnes AI API**（`agnes-2.0-flash` 模型，通过 `apihub.agnes-ai.com/v1` 调用）
- **Web Speech API**（`SpeechSynthesis` 语音合成）
- **Font Awesome** + **Material Symbols Rounded**（图标库）
- **Poppins** 字体
- **GitHub Actions** → **GitHub Pages**（CI/CD 自动部署）

## 📁 项目结构

```
AI-main/
├── .github/
│   └── workflows/
│       └── deploy-pages.yml   # GitHub Pages 自动部署工作流
├── images/
│   ├── favicon.ico             # 站点图标
│   ├── gemini.jpg              # AI 头像
│   └── user.jpg                # 用户头像
├── index.html                  # 主应用（聊天助手）
├── one_a.html                  # 应用导航 hover 动效演示页
└── README.md
```

## 🚀 部署

项目通过 GitHub Actions 自动部署到 GitHub Pages：

1. 推送代码到 `main` 分支
2. 工作流执行时通过 `sed` 将 `index.html` 中的占位符 `__AGNES_API_KEY__` 替换为仓库 Secret `AGNES_API_KEY`
3. 上传部署制品并发布到 GitHub Pages

> 部署前需在仓库 Settings → Secrets and variables → Actions 中配置 `AGNES_API_KEY`。

## 📖 使用说明

1. 访问部署后的 GitHub Pages 站点
2. 在底部输入框输入问题，回车或点击发送按钮
3. 点击建议卡片可快速发起对话
4. 右下角操作按钮：
   - 🌗 主题切换（深色 / 浅色）
   - 🔊 语音播报开关
   - 🗑 清空聊天记录（需二次确认）
5. 发送「测试」可呼出调试面板

## 📄 附加页面

`one_a.html` 是一个独立的应用导航动效演示页，使用 GSAP 实现导航项 hover 时相邻项联动展开的弹性动画，灵感来自 Osmo UI。

## 👤 作者

**钟锦明 / 佐罗斯（Zorrose）**

- GitHub：[@Zok66](https://github.com/Zok66)

## 📜 许可

本项目为个人学习与作品展示用途，如需引用请保留作者署名。
