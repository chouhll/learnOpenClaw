# learnOpenClaw
以下是为你整理的 **Mac (18G内存) OpenClaw 部署配置完整 MD 文档**，你可以直接复制保存为 `.md` 文件，方便随时查看和使用：

```markdown
# Mac (18G内存) OpenClaw 部署配置指南
## 一、环境说明
- 设备：Mac（18G 内存）
- 系统：macOS（兼容所有主流版本）
- 核心目标：稳定部署、流畅运行，支持本地 AI 执行电脑操作
- 最优模型：Ollama + qwen2.5:7b（18G 内存适配，无卡顿）

## 二、前置准备
1. 确保网络正常（无需特殊环境）
2. 关闭不必要的大型软件（如 Photoshop、Xcode 等），释放内存

## 三、一键部署步骤
### 1. 安装 Ollama（本地模型核心）
打开 Mac 终端，执行以下命令：
```bash
# 方式1：通过 brew 安装（推荐，需提前安装 brew）
brew install ollama

# 方式2：无 brew 则先安装 brew，再装 Ollama
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
brew install ollama
```

### 2. 拉取适配 18G 内存的模型
终端执行，自动下载 qwen2.5:7b 模型（约 4GB，耐心等待）：
```bash
ollama pull qwen2.5:7b
```

### 3. 安装 OpenClaw 核心框架
终端执行一键安装脚本：
```bash
curl -fsSL https://download.openclaw.ai/install.sh | sh
```

### 4. 验证安装
安装完成后，系统会自动打开 OpenClaw 网页面板，地址：
```
http://localhost:3000
```
若未自动打开，手动在浏览器输入上述地址即可。

## 四、10秒配置（关键步骤）
1. 进入网页面板后，点击左侧「设置」→「模型选择」
2. 模型类型选择：**Ollama**
3. 填写配置信息（直接照抄）：
   - Ollama 地址：`http://localhost:11434`
   - 模型名称：`qwen2.5:7b`
4. 点击「保存」，然后点击页面右上角「重启服务」

## 五、18G 内存专属优化
### 1. 内存优化（可选，更流畅）
终端执行以下命令，限制 Ollama 内存占用：
```bash
# 临时生效（重启终端失效）
export OLLAMA_CPU_MEMORY=8GB

# 永久生效（推荐）
echo 'export OLLAMA_CPU_MEMORY=8GB' >> ~/.zshrc
source ~/.zshrc
```

### 2. 使用建议
- 避免同时开启大量 Chrome 标签 + 大型软件（如 Final Cut Pro）
- 执行复杂任务（如批量处理文件）时，关闭其他 AI 工具
- 无需升级 14B 模型（18G 内存运行 14B 会卡顿，7B 足够日常使用）

## 六、快速测试（验证是否可用）
在 OpenClaw 聊天框输入以下指令，验证是否能正常执行：
1. 「帮我整理下载文件夹，按文件类型分类」
2. 「打开浏览器，搜索 OpenClaw 常用指令」
3. 「写一段 Python 脚本，输出 1-10 的平方」

## 七、常见问题解决
| 问题现象                | 解决方法                                  |
|-------------------------|-------------------------------------------|
| 网页面板打不开          | 重启终端，重新执行 OpenClaw 安装脚本      |
| AI 不执行电脑操作       | 在系统设置中给终端/浏览器开启「辅助功能」权限 |
| 模型响应慢              | 关闭其他占用内存的软件，执行内存优化命令  |
| Ollama 启动失败         | 卸载 Ollama 后从官网重新下载安装          |
```

### 总结
1. 核心配置：Mac 18G 内存优先选择 `Ollama + qwen2.5:7b`，兼顾流畅度和功能；
2. 部署关键：按步骤执行终端命令，配置页面填写 `http://localhost:11434` 和 `qwen2.5:7b` 后重启服务；
3. 优化要点：通过环境变量限制 Ollama 内存占用，避免同时开高内存软件。

你保存这份 MD 文档后，后续部署或遇到问题时，直接对照步骤操作即可。如果需要补充「常用指令清单」或「权限配置细节」，可以告诉我。
