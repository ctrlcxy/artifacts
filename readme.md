# ChatGPT Artifacts

> 将 Claude 的 Artifacts 功能带到 ChatGPT - 一个强大的AI对话和代码预览平台

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![Node.js Version](https://img.shields.io/badge/node-%3E%3D16.0.0-brightgreen)](https://nodejs.org/)
[![Next.js](https://img.shields.io/badge/Next.js-14.2.4-black)](https://nextjs.org/)

## 📖 项目简介

ChatGPT Artifacts 是一个创新的Web应用程序，它将Claude AI的Artifacts功能引入到ChatGPT中。该项目提供了一个直观的界面，让用户可以与AI进行对话，并实时预览和编辑生成的代码、HTML、CSS等内容。

## ✨ 主要特性

- 🤖 **多AI模型支持**: 支持OpenAI GPT、Ollama本地模型、Groq、Azure OpenAI
- 🎨 **实时代码预览**: 即时预览HTML、CSS、JavaScript代码效果
- 📝 **Markdown渲染**: 完整的Markdown支持和语法高亮
- 🌓 **深色/浅色主题**: 可切换的主题模式
- 💾 **对话历史**: 自动保存和管理对话记录
- ⌨️ **键盘快捷键**: 提高操作效率的快捷键支持
- 🔄 **实时通信**: 基于Socket.IO的实时消息传输
- 📱 **响应式设计**: 适配各种设备屏幕尺寸
- 🛠️ **代码编辑器**: 内置代码编辑功能
- 🔔 **通知系统**: 智能的消息通知机制

## 🎬 预览演示



![html.jpg](C:\Users\13903\Desktop\测试\html.jpg)

![Snipaste_2025-06-08_15-29-01.jpg](C:\Users\13903\Desktop\测试\Snipaste_2025-06-08_15-29-01.jpg)

![代码示例.jpg](C:\Users\13903\Desktop\测试\代码示例.jpg)

![界面.jpg](C:\Users\13903\Desktop\测试\界面.jpg)

![赛博朋克.jpg](C:\Users\13903\Desktop\测试\赛博朋克.jpg)







## 🛠️ 技术栈

- **前端框架**: Next.js 14.2.4
- **UI库**: React 18.3.1
- **样式**: Sass
- **实时通信**: Socket.IO
- **代码高亮**: React Syntax Highlighter
- **Markdown解析**: Marked
- **图标**: Lucide React
- **AI接口**: OpenAI API

## 📋 系统要求

- Node.js >= 16.0.0
- npm 或 yarn 包管理器
- 现代浏览器 (Chrome, Firefox, Safari, Edge)

## 🚀 快速开始

### 1. 克隆项目

```bash
git clone https://github.com/ozgrozer/chatgpt-artifacts.git
cd chatgpt-artifacts
```

### 2. 安装依赖

```bash
npm install
# 或者使用 yarn
yarn install
```

### 3. 环境配置

创建环境变量文件：

```bash
cp .env.example .env
```

编辑 `.env` 文件，添加您的API密钥：

```env
OPENAI_API_KEY=your_openai_api_key_here
```

### 4. 构建应用

```bash
npm run build
```

### 5. 启动应用

```bash
# 生产环境
npm start

# 开发环境
npm run dev
```

应用将在 `http://localhost:3000` 启动。

## 🔧 配置选项

### OpenAI GPT (默认)

默认配置使用OpenAI的GPT模型，只需在 `.env` 文件中设置API密钥即可。

### Ollama 本地模型支持

要使用本地LLM模型（如Llama3或Gemma2），请修改 `/pages/api/chat.js` 文件：

```javascript
// 修改OpenAI客户端配置
const openai = new OpenAI({
  apiKey: 'ollama',
  baseURL: 'http://127.0.0.1:11434/v1'
})

// 修改模型名称
const stream = await openai.chat.completions.create({
  stream: true,
  model: 'llama3', // 或其他本地模型
  messages: conversations[conversationId]
})
```

**注意**: 确保Ollama服务正在运行并且已安装所需模型。

### Groq 支持

1. 在 [Groq Console](https://console.groq.com/keys) 获取API密钥
2. 修改 `/pages/api/chat.js` 文件：

```javascript
const openai = new OpenAI({
  apiKey: process.env.GROQ_API_KEY, // 在.env中添加GROQ_API_KEY
  baseURL: 'https://api.groq.com/openai/v1'
})

const stream = await openai.chat.completions.create({
  stream: true,
  model: 'llama3-70b-8192', // 或其他Groq支持的模型
  messages: conversations[conversationId]
})
```

### Azure OpenAI 支持

1. 在 [Azure Portal](https://portal.azure.com/) 创建OpenAI资源
2. 在 [Azure OpenAI Studio](https://oai.azure.com/) 创建部署
3. 修改 `/pages/api/chat.js` 文件：

```javascript
const openai = new OpenAI({
  apiKey: process.env.AZURE_OPENAI_API_KEY,
  defaultQuery: { 'api-version': '2023-03-15-preview' },
  defaultHeaders: { 'api-key': process.env.AZURE_OPENAI_API_KEY },
  baseURL: 'https://<RESOURCE_NAME>.openai.azure.com/openai/deployments/<DEPLOYMENT_NAME>'
})
```

## 📚 使用指南

### 基本操作

1. **开始对话**: 在输入框中输入您的问题或请求
2. **代码预览**: AI生成的代码会自动在预览区域显示
3. **编辑代码**: 点击代码块可以进入编辑模式
4. **主题切换**: 使用右上角的主题切换按钮
5. **查看历史**: 通过侧边栏访问对话历史

### 键盘快捷键

- `Ctrl/Cmd + Enter`: 发送消息
- `Ctrl/Cmd + K`: 清除当前对话
- `Ctrl/Cmd + D`: 切换主题
- `Esc`: 关闭模态框或取消编辑

### 支持的内容类型

- HTML页面和组件
- CSS样式和动画
- JavaScript应用程序
- React组件
- Markdown文档
- 数据可视化图表
- SVG图形

## 🔍 故障排除

### 常见问题

**Q: API密钥无效错误**
A: 请检查 `.env` 文件中的API密钥是否正确，确保没有多余的空格或引号。

**Q: 本地模型连接失败**
A: 确保Ollama服务正在运行，端口11434可访问，并且已安装所需的模型。

**Q: 预览区域空白**
A: 检查浏览器控制台是否有JavaScript错误，尝试刷新页面或清除浏览器缓存。

**Q: Socket连接失败**
A: 检查防火墙设置，确保WebSocket连接未被阻止。

### 调试模式

在开发环境中启用详细日志：

```bash
DEBUG=* npm run dev
```

### 开发规范

- 使用 [Standard](https://standardjs.com/) 代码风格
- 编写清晰的提交消息
- 添加适当的注释和文档
- 确保所有测试通过

## 📄 许可证

本项目采用 [GPL-3.0](https://github.com/ozgrozer/chatgpt-artifacts/blob/main/license) 许可证。

## 🙏 致谢

- 感谢 [Anthropic](https://www.anthropic.com/) 提供的Artifacts功能灵感
- 感谢 [OpenAI](https://openai.com/) 提供强大的AI模型
- 感谢所有贡献者和社区成员的支持

---

⭐ 如果这个项目对您有帮助，请给我们一个星标！
