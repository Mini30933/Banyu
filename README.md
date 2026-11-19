<div align="center">

<img src="docs/icon.png" width="120" alt="伴语图标">

# 伴语 Banyu

**让喜欢的角色住进你的手机 —— 能陪你聊天，还能替你操作手机的 Android AI 伴侣**

![License](https://img.shields.io/badge/license-MIT-green)
![Platform](https://img.shields.io/badge/platform-Android%208.0%2B-blue)
![Kotlin](https://img.shields.io/badge/Kotlin-Jetpack%20Compose-purple)

</div>

## 这是什么

伴语是一款聊天优先的 AI 伴侣应用：你给它写一段「角色设定」，它就以这个角色的身份和你日常聊天；当你需要它动手时，它还能接管手机，替你打开应用、点按、输入、刷页面 —— 角色扮演和手机操控长在同一个应用里。

它基于开源项目 [roubao（肉包）](https://github.com/Turbo1123/roubao) 二次开发，保留了其 VLM 手机操控内核，并在此之上重做了交互形态和感知方式。

## 功能亮点

- **角色扮演对话**：DeepSeek 风格的聊天界面是首页；系统提示词即「角色设定」，想让谁陪你聊、用什么语气，都由你写
- **多会话侧边栏**：会话可搜索、置顶、重命名、分组（置顶/今天/昨天/7天内/更早）、多选批量删除，标题自动生成
- **对话中直接操控手机**：角色在回复里发出控制标记即可执行任务（打开抖音、发消息、查东西……），执行结果会回到对话里继续聊
- **三种控制方式**（任选其一即可）：
  - **Shizuku**：经典方案，权限完整
  - **无障碍**：免 Shizuku，系统无障碍服务直接操控
  - **ADB 无线调试**：应用自连接手机的无线调试（libadb-android），无需电脑
- **元素树感知**：操控时优先把无障碍 UI 元素树（带索引）发给模型，按元素直达点击，不再靠猜截图坐标；坐标路径作为游戏/网页等场景的兜底
- **长期记忆**：跨会话记住偏好、关系进展和重要事件；记忆达到 8000 字时自动由模型压缩 —— 最新 10% 保留原文，其余浓缩成摘要，不丢关键信息
- **够长的陪伴**：单任务最多 300 步，单次回复 max_tokens 8192，长对话不怕被截断
- **Swarm 启动动画**：冷启动时 20 只彩色小光标在屏幕上协作、打字、发送，再汇成标志 —— 只播一次，点一下就跳过

## 快速开始

1. **下载安装**：到 [Releases](https://github.com/Mini30933/Banyu/releases) 下载最新 APK 安装（Android 8.0+）
2. **配置模型**：打开「设置」，填入任意 OpenAI 兼容接口的地址、API Key 和模型名（需要支持看图的视觉模型才能操控手机），可一键拉取模型列表
3. **选一种控制方式**：
   - Shizuku：按应用内指引发起授权
   - 无障碍：到系统设置里开启「伴语」无障碍服务
   - ADB：开发者选项 → 无线调试 → 用配对码配对，把端口和配对码填进设置页的 ADB 卡片
4. **写角色设定**：在设置里写下你想要的角色和说话方式，回到对话页开始聊天

## 技术栈

Kotlin · Jetpack Compose / Material 3 · OkHttp · Shizuku · libadb-android · BouncyCastle

## 致谢与许可

- 基于 [Turbo1123/roubao](https://github.com/Turbo1123/roubao)（MIT）二次开发，感谢原作者的开源工作；元素树感知的思路借鉴了 dsh-go 与 droidrun/mobilerun 的公开实践（仅思路，未复制代码）
- 本项目同样以 [MIT](LICENSE) 许可发布

---

## English (brief)

**Banyu** is a chat-first Android AI companion: give it a persona ("character setting") and it chats with you in character — and when you ask, it takes over the phone and operates apps for you. Features multi-session chat with a DeepSeek-style UI, three control backends (Shizuku / Accessibility / ADB wireless debugging), accessibility-tree perception with index-based element actions, and long-term memory with model-based compression (at 8,000 chars: newest 10% verbatim + summarized digest). Based on the MIT-licensed [roubao](https://github.com/Turbo1123/roubao) project. Grab the APK from [Releases](https://github.com/Mini30933/Banyu/releases).
