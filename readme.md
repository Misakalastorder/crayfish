# 本地运行
## Node.js
## 运行前
###　ollama

ollama ps
返回：
ollama ps
NAME          ID              SIZE      PROCESSOR    CONTEXT    UNTIL
qwen2.5:7b    845dbda0ea48    6.3 GB    100% GPU     16384      4 minutes from now
检查是否有在运行的模型
ollama stop qwen2.5:7b
结束正在运行的模型
### 
ollama用户自行设长上下文，用modelfile
'''
type Modelfile
FROM qwen2.5:7b
PARAMETER num_ctx 16384
'''
不需要再重设模型上下文，ollama里面可以一键设置
### openclaw
|
o  I understand this is personal-by-default and shared/multi-user use requires lock-down. Continue?

|  Yes

|
o  Onboarding mode

|  Manual
|

o  What do you want to set up?

|  Local gateway (this machine)
|

o  Workspace directory

|  D:\code\crayfish\history
|

o  Model/auth provider

|  Custom Provider
|

o  API Base URL

|  http://localhost:11434/v1
|

o  How do you want to provide this API key?

|  Paste API key now
|

o  API Key (leave blank if not required)

|  ollama
|

o  Endpoint compatibility

|  OpenAI-compatible
|

o  Model ID

|  qwen2.5:7b
|

o  Verification successful.
|

o  Endpoint ID

|  custom-localhost-11434
|

o  Model alias (optional)

|  qwen2.5:7b
Configured custom provider: 

custom-localhost-11434/qwen2.5:7b
|

o  Gateway port

|  18789
|

o  Gateway bind

|  Loopback (127.0.0.1)
|

o  Gateway auth

|  Token
|

o  Tailscale exposure

|  Off
|

o  How do you want to provide the gateway token?

|  Generate/store plaintext token
|

o  Gateway token (blank to generate)

|
|
o  Channel status ----------------------------+
|                                             |
|  Telegram: needs token                      |
|  WhatsApp (default): not linked             |
|  Discord: needs token                       |
|  Slack: needs tokens                        |
|  Signal: needs setup                        |
|  signal-cli: missing (signal-cli)           |
|  iMessage: needs setup                      |
|  imsg: missing (imsg)                       |
|  IRC: not configured                        |
|  Google Chat: not configured                |
|  LINE: not configured                       |
|  Feishu: install plugin to enable           |
|  Google Chat: install plugin to enable      |
|  Nostr: install plugin to enable            |
|  Microsoft Teams: install plugin to enable  |
|  Mattermost: install plugin to enable       |
|  Nextcloud Talk: install plugin to enable   |
|  Matrix: install plugin to enable           |
|  BlueBubbles: install plugin to enable      |
|  LINE: install plugin to enable             |
|  Zalo: install plugin to enable             |
|  Zalo Personal: install plugin to enable    |
|  Synology Chat: install plugin to enable    |
|  Tlon: install plugin to enable             |
|                                             |
+---------------------------------------------+
|

o  Configure chat channels now?

|  No
Updated ~\.openclaw\openclaw.json
Workspace OK: D:\code\crayfish\history
Sessions OK: ~\.openclaw\agents\main\sessions
|

o  Web search ----------------------------------------+
|                                                     |
|  Web search lets your agent look things up online.  |
|  Choose a provider and paste your API key.          |
|  Docs: https://docs.openclaw.ai/tools/web           |
|                                                     |
+-----------------------------------------------------+
|

o  Search provider

|  Skip for now
|

o  Skills status -------------+
|                             |
|  Eligible: 3                |
|  Missing requirements: 40   |
|  Unsupported on this OS: 8  |
|  Blocked by allowlist: 0    |
|                             |
+-----------------------------+
|

o  Configure skills now? (recommended)

|  Yes
|

o  Install missing skill dependencies

|  Skip for now
|
o  Set GOOGLE_PLACES_API_KEY for goplaces?

|  No
|
o  Set GEMINI_API_KEY for nano-banana-pro?

|  No
|
o  Set NOTION_API_KEY for notion?

|  No
|
o  Set OPENAI_API_KEY for openai-image-gen?

|  No
|
o  Set OPENAI_API_KEY for openai-whisper-api?

|  No
|
o  Set ELEVENLABS_API_KEY for sag?

|  No
|

o  Hooks ------------------------------------------------------------------+
|                                                                          |
|  Hooks let you automate actions when agent commands are issued.          |
|  Example: Save session context to memory when you issue /new or /reset.  |
|                                                                          |
|  Learn more: https://docs.openclaw.ai/automation/hooks                   |
|                                                                          |
+--------------------------------------------------------------------------+
|

o  Enable hooks?


|  Skip for now

Config overwrite: C:\Users\yan\.openclaw\openclaw.json (sha256 fd250107942e5574993b6c75fb3177cdd20ed1127dbc6d64b0161b96327c25ba -> c41535e34a7408831540a9e54fbe5dcdf16f9e26d5e02f5a16d5b65bde9b21c1, backup=C:\Users\yan\.openclaw\openclaw.json.bak)
|

o  Install Gateway service (recommended)

|  No
|

o
Health check failed: gateway closed (1006 abnormal closure (no close frame)): no close reason
  Gateway target: ws://127.0.0.1:18789
  Source: local loopback
  Config: C:\Users\yan\.openclaw\openclaw.json
  Bind: loopback
|

o  Health check help --------------------------------+
|                                                    |
|  Docs:                                             |
|  https://docs.openclaw.ai/gateway/health           |
|  https://docs.openclaw.ai/gateway/troubleshooting  |
|                                                    |
+----------------------------------------------------+
|

o  Optional apps ------------------------+
|                                        |
|  Add nodes for extra features:         |
|  - macOS app (system + notifications)  |
|  - iOS app (camera/canvas)             |
|  - Android app (camera/canvas)         |
|                                        |
+----------------------------------------+
|
o  Control UI -------------------------------------------------------------------------------+
|                                                                                            |
|  Web UI: http://******/                                                           |
|  Web UI (with token):                                                                      |
|  http://********/#token=********            |
|  Gateway WS: ws://127.0.0.1:18789                                                          |
|  Gateway: not detected (gateway closed (1006 abnormal closure (no close frame)): no close  |
|  reason)                                                                                   |
|  Docs: https://docs.openclaw.ai/web/control-ui                                             |
|                                                                                            |
+--------------------------------------------------------------------------------------------+
|

o  Workspace backup ----------------------------------------+
|                                                           |
|  Back up your agent workspace.                            |
|  Docs: https://docs.openclaw.ai/concepts/agent-workspace  |
|                                                           |
+-----------------------------------------------------------+
|
o  Security ------------------------------------------------------+
|                                                                 |
|  Running agents on your computer is risky — harden your setup:  |
|  https://docs.openclaw.ai/security                              |
|                                                                 |
+-----------------------------------------------------------------+
|
*  Enable zsh shell completion for openclaw?
|  > Yes /   No

令牌
 http://********/#token=********
 qwen2.5:7b

 在终端交互界面中退出
如果你正处于 ollama run 开启的对话模式中：
输入指令：直接输入 /bye 然后按回车。这是最推荐的退出方式，它会向 Ollama 后端发送一个明确的终止信号。
快捷键：按下 Ctrl + D。这在 Linux 和 Windows 终端中通常代表“发送结束符（EOF）”，也能触发正常退出。

终端窗口退出（最彻底）
如果你是在 CMD 或 PowerShell 中运行 openclaw gateway 启动的：
操作：直接在那个运行窗口按下 Ctrl + C。
确认：如果出现“终止批处理操作吗(Y/N)？”，输入 Y 并回车。
物理关闭：直接点击窗口右上角的 X。关闭这个黑色窗口后，OpenClaw 的后端进程会立即停止。

# 容器运行openclaw
## 安装docker
安全一点使用容器运行
## docker-setup.sh
这个 docker-setup.sh 脚本主要用于自动化部署和配置基于 Docker 的 OpenClaw 网关环境。具体功能如下：

环境检查与初始化

检查 docker 和 docker compose 命令是否可用。
初始化目录结构，如 OPENCLAW_CONFIG_DIR 和 OPENCLAW_WORKSPACE_DIR，并确保它们存在。
验证环境变量（如挂载路径、卷名称）的合法性，防止包含非法字符。
配置管理

生成或复用 OPENCLAW_GATEWAY_TOKEN（优先从配置文件或 .env 读取，否则生成新 token）。
通过 upsert_env 函数将当前配置持久化到 .env 文件中。
根据 OPENCLAW_HOME_VOLUME 和 OPENCLAW_EXTRA_MOUNTS 动态生成 docker-compose.extra.yml 文件以配置卷挂载。
镜像处理

如果 OPENCLAW_IMAGE 为 openclaw:local，则使用 Dockerfile 构建镜像。
否则，尝试从 registry 拉取指定的镜像。
权限修复

运行一个临时的 root 用户容器，修复挂载目录（如 .openclaw）的所有者权限为 node:node，避免容器内写入权限问题。
服务启动与配置

执行 openclaw-cli onboard 进行交互式初始化。
设置网关模式（gateway.mode=local）和绑定地址。
配置 Control UI 的允许来源（gateway.controlUi.allowedOrigins）。
启动 openclaw-gateway 服务。
沙盒环境支持（可选）

如果设置 OPENCLAW_SANDBOX=1，脚本会检查 Docker CLI 可用性。
生成 docker-compose.sandbox.yml 挂载 Docker Socket（/var/run/docker.sock）。
配置 agents 的沙盒模式（agents.defaults.sandbox.mode）。
信息输出

打印网关访问地址、配置路径、Token 以及用于查看日志和健康检查的命令。