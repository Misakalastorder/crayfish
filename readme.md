# 本地大模型-无容器
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