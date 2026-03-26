科研选题副驾系统 (Research Topic Co-pilot) 🚀
基于 Dify 的多智能体科研辅助工作流，利用漏斗架构实现从“模糊意图”到“落地提案”的决策闭环。
🌟 项目亮点 (Key Features)
本系统专为科研新手设计，解决了选题阶段“想法太泛、情报滞后、资源错位”的痛点。
意图对齐层 (Gatekeeper)：采用 FSM (有限状态机) 逻辑，自动识别输入状态（信息不足、资源冲突、准备就绪、决策收敛），实现精准的边界拦截。
情报侦察层 (Scout Agent)：基于 ReAct 范式 调度 Tavily 检索工具，实时抓取最新学术趋势，并自动生成多路径对比矩阵。
资源匹配引擎 (Resource-Aware)：强制校验用户的可用资源（如 10w 预算），确保每一份选题建议都具备 100% 的可落地性。
自动化收敛交付：在用户确认路径后，自动生成包含题目、研究问题 (RQ) 及 48 小时破冰清单的结构化报告。

🏗️ 工作流架构 (Architecture)
系统采用“发散-过滤-收敛”的经典漏斗模型，确保输出结果的高质量与高相关性。

🚀 如何在本地运行 (Quick Start)
想要在你的 Dify 环境中复现此工作流，请遵循以下步骤：
1. 环境准备
确保你拥有 Dify.ai 账号（云端或私有化部署均可）。
准备好以下 API Keys：
LLM Provider: OpenAI 或 DeepSeek (推荐)。
Search Tool: Tavily Search API Key (用于情报侦察层)。

2. 导入工作流 (DSL Import)
下载本仓库 workflow/ 目录下的 research-topic-copilot.yml 文件。
进入 Dify 控制台，点击 “创建应用” (Create App)。
选择 “导入 DSL 文件” (Import DSL File)。
上传刚才下载的 .yml 文件。

3. 配置工具与模型
进入工作流编排界面。
在 意图对齐层 (Gatekeeper) 和 执行交付层 (Convergence) 节点中，选择你的主流大模型（如 gpt-4o 或 deepseek-chat）。
在 Scout Agent 节点中，点击工具图标，填入你的 Tavily API Key。

4. 发布与体验
点击右上角的 “预览” 即可开始对话。

📄 核心逻辑定义 (Logic Definition)
系统内部通过以下状态驱动路由转向：
INSUFFICIENT: 想法太泛，触发导师追问。
CONFLICT: 资源不匹配，触发平替建议。
READY: 意图清晰，触发情报检索。
CONVERGE: 识别到用户选择，触发报告生成。

📜 许可证 (License)
根据 MIT License 授权。
Author: tian415
Topic: AI Application Development / Research Co-pilot
