## 提示词优化器 🚀

<div align="center">

[English](README_EN.md) | [中文](README.md)

[![GitHub stars](https://img.shields.io/github/stars/linshenkx/prompt-optimizer)](https://github.com/linshenkx/prompt-optimizer/stargazers)
![Chrome Web Store Users](https://img.shields.io/chrome-web-store/users/cakkkhboolfnadechdlgdcnjammejlna?style=flat&label=Chrome%20Users&link=https%3A%2F%2Fchromewebstore.google.com%2Fdetail%2F%25E6%258F%2590%25E7%25A4%25BA%25E8%25AF%258D%25E4%25BC%2598%25E5%258C%2596%25E5%2599%25A8%2Fcakkkhboolfnadechdlgdcnjammejlna)

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Docker Pulls](https://img.shields.io/docker/pulls/linshen/prompt-optimizer)](https://hub.docker.com/r/linshen/prompt-optimizer)
![GitHub forks](https://img.shields.io/github/forks/linshenkx/prompt-optimizer?style=flat)
[![Deploy with Vercel](https://img.shields.io/badge/Vercel-indigo?style=flat&logo=vercel)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Flinshenkx%2Fprompt-optimizer)

[Online Experience](https://prompt.always200.com) | [Quick Start](#快速开始) | [FAQ](#常见问题) | [Development Documentation](dev.md) | [Vercel Deployment Guide](docs/vercel.md) | [Chrome Plugin](https://chromewebstore.google.com/detail/prompt-optimizer/cakkkhboolfnadechdlgdcnjammejlna)

</div>

## 📖 Project Introduction

Prompt Optimizer is a powerful AI prompt optimization tool to help you write better AI prompts and improve AI output quality. Supports both Web application and Chrome plugin usage.

### 🎥 Feature Demonstration

<div align="center">
  <img src="images/contrast.png" alt="功能演示" width="90%">
</div>

## ✨ Core Features

- 🎯 **Intelligent Optimization**: One-click optimization of prompts, supports multi-round iterative improvement, improving the accuracy of AI responses
- 🔄 **Contrast Testing**: Supports real-time comparison of original prompts and optimized prompts, intuitively demonstrating the optimization effect
- 🤖 **Multi-Model Integration**: Supports mainstream AI models such as OpenAI, Gemini, DeepSeek, Zhipu AI, and SiliconFlow
- ⚙️ **Advanced Parameter Configuration**: Supports configuring LLM parameters such as temperature and max_tokens separately for each model
- 🔒 **Secure Architecture**: Pure client-side processing, data interacts directly with AI service providers, without going through intermediate servers
- 💾 **Privacy Protection**: Local encrypted storage of historical records and API keys, supports data import and export
- 📱 **Multi-Terminal Support**: Simultaneously provides Web application and Chrome plugin usage methods
- 🎨 **User Experience**: Concise and intuitive interface design, responsive layout, and smooth interactive animation effects
- 🌐 **Cross-Domain Support**: Supports using Edge Runtime proxy to solve cross-domain issues when deploying with Vercel
- 🔐 **Access Control**: Supports password protection to ensure deployment security

## Quick Start

### 1. Use the Online Version (Recommended)

Directly visit: [https://prompt.always200.com](https://prompt.always200.com)

The project is a pure front-end project, and all data is only stored locally in the browser and will not be uploaded to any server, so using the online version directly is also safe and reliable

### 2. Vercel Deployment
Method 1: One-click deployment to your own Vercel:
   [![Deploy to Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Flinshenkx%2Fprompt-optimizer)

Method 2: Fork the project and import it into Vercel (Recommended):
   - First Fork the project to your own GitHub
   - Then import the project into Vercel
   - Can track source project updates, easy to synchronize the latest features and fixes
- Configure environment variables:
  - `ACCESS_PASSWORD`: Set the access password to enable access restriction
  - `VITE_OPENAI_API_KEY` etc.: Configure the API keys of various AI service providers

For more detailed deployment steps and precautions, please see:
- [Vercel Deployment Guide](docs/vercel.md)

### 3. Install the Chrome Plugin
1. Install from the Chrome Store (due to slow approval, it may not be the latest): [Chrome Store Address](https://chromewebstore.google.com/detail/prompt-optimizer/cakkkhboolfnadechdlgdcnjammejlna)
2. Click the icon to open the prompt optimizer

### 4. Docker Deployment
```bash
# Run the container (default configuration)
docker run -d -p 80:80 --restart unless-stopped --name prompt-optimizer linshen/prompt-optimizer

# Run the container (configure API key and access password)
docker run -d -p 80:80 \
  -e VITE_OPENAI_API_KEY=your_key \
  -e ACCESS_USERNAME=your_username \  # Optional, defaults to "admin"
  -e ACCESS_PASSWORD=your_password \  # Set access password
  --restart unless-stopped \
  --name prompt-optimizer \
  linshen/prompt-optimizer
  
```

### 5. Docker Compose Deployment
```bash
# 1. Clone the repository
git clone https://github.com/linshenkx/prompt-optimizer.git
cd prompt-optimizer

# 2. Optional: Create a .env file to configure the API key and access authentication
cat > .env << EOF
# API Key Configuration
VITE_OPENAI_API_KEY=your_openai_api_key
VITE_GEMINI_API_KEY=your_gemini_api_key
VITE_DEEPSEEK_API_KEY=your_deepseek_api_key
VITE_ZHIPU_API_KEY=your_zhipu_api_key
VITE_SILICONFLOW_API_KEY=your_siliconflow_api_key

# Basic Authentication Configuration (Password Protection)
ACCESS_USERNAME=your_username  # Optional, defaults to "admin"
ACCESS_PASSWORD=your_password  # Set access password
EOF

# 3. Start the service
docker compose up -d

# 4. View logs
docker compose logs -f
```

You can also directly edit the docker-compose.yml file to customize the configuration:
```yaml
services:
  prompt-optimizer:
    image: linshen/prompt-optimizer:latest
    container_name: prompt-optimizer
    restart: unless-stopped
    ports:
      - "8081:80"  # Modify port mapping
    environment:
      - VITE_OPENAI_API_KEY=your_key_here  # Set the key directly in the configuration
```

## ⚙️ API Key Configuration

### Method 1: Configure Through the Interface (Recommended)
1. Click the "⚙️ Settings" button in the upper right corner of the interface
2. Select the "Model Management" tab
3. Click on the model you need to configure (e.g., OpenAI, Gemini, DeepSeek, etc.)
4. Enter the corresponding API key in the pop-up configuration box
5. Click "Save"

Supported models:
- OpenAI (gpt-3.5-turbo, gpt-4, gpt-4o)
- Gemini (gemini-1.5-pro, gemini-2.0-flash)
- DeepSeek (deepseek-chat, deepseek-coder)
- Zhipu 智谱 (glm-4-flash, glm-4, glm-3-turbo)
- SiliconFlow (Pro/deepseek-ai/DeepSeek-V3)
- Custom API (OpenAI compatible interface)

In addition to API keys, you can also configure advanced LLM parameters for each model individually in the model configuration interface. These parameters are configured through a field called `llmParams`, which allows you to specify any parameters supported by the LLM SDK in the form of key-value pairs, thus controlling model behavior more precisely.

**Advanced LLM Parameter Configuration Example:**
- **OpenAI/Compatible API**: `{"temperature": 0.7, "max_tokens
