根据搜索结果，我按12周路线的每个阶段，整理了一份**可以一步一步跟着做**的教程清单，每个阶段都从"最简可运行代码"开始，逐步加复杂度。

---

### 第 0–2 周：手写 ReAct Agent（纯 Python，不依赖框架）

这个阶段的目标是理解 Agent 的本质——一个 while 循环。以下教程都提供完整可复制代码，直接跑通：

**入门必读（理解原理）**
- Anthropic《Building Effective Agents》：https://www.anthropic.com/engineering/building-effective-agents
- Lilian Weng《LLM Powered Autonomous Agents》：https://lilianweng.github.io/posts/2023-06-23-agent/

**手把手代码教程（按顺序做）**

1. **《从零搭建一个最小 AI Agent》**（博客园，约100行完整代码）
   - 内容：Python + OpenAI 兼容接口，实现工具注册表、ReAct 循环、多轮历史
   - 特点：代码极简，注释详细，支持 DeepSeek/通义/智谱等国内模型
   - 链接：https://www.cnblogs.com/exioran/p/21714159

2. **《100行Python代码，搭一个能干活的AI Agent》**（博客园）
   - 内容：Memory 类设计、Agent 主循环、工具 Schema 定义，带运行效果截图
   - 特点：拆解了"思考→判断→行动→观察"每一步，适合理解循环机制
   - 链接：https://www.cnblogs.com/yudanqu/p/22456248

3. **《从零手写 Agent：从最简单的Loop开始》**（微信公众号，约400行生产级代码）
   - 内容：在最小循环基础上加了流式输出、用户取消、最大循环保护、事件流
   - 特点：更接近真实项目结构，适合第2周进阶
   - 链接：https://mp.weixin.qq.com/s?__biz=MzYzMjk0OTg5Mg==&idx=1&mid=2247483670&sn=42853819fe9eabb295e6eabc81ff19b1

4. **《动手学大模型智能体》第二课：手写 ReAct 智能体**（Datawhale 系列）
   - 内容：基于 ReAct 协议，纯手工 Python 编写，含 Thought/Action/Observation 格式约束
   - 特点：带 Mock 模式，没有 API Key 也能理解完整流程
   - 链接：https://mp.weixin.qq.com/s?__biz=MzU2ODAwMzgxMA==&idx=8&mid=2247571846&sn=78d5c58123c842363782eac21ec85a01

---

### 第 3–5 周：RAG 实战（从零搭建知识库问答）

**入门教程（按顺序做）**

1. **《大模型RAG实战：从零搭建专属知识库问答助手》**（博客园，完整4步流程）
   - 内容：数据预处理 → 知识库构建 → 检索生成模块 → 效果测试，每一步都有代码
   - 特点：使用 FAISS + 免费模型，普通笔记本就能跑，不跳步
   - 链接：https://www.cnblogs.com/5409zxy/articles/19600965

2. **Microsoft 官方教程：构建 RAG 应用程序**（Microsoft Learn）
   - 内容：创建知识库 → 生成嵌入 → 相似性搜索 → 生成答案，完整代码
   - 特点：官方出品，代码规范，适合理解标准流程
   - 链接：https://learn.microsoft.com/zh-cn/azure/foundry-local/tutorials/tutorial-build-rag-app

3. **《RAG从入门到精通：一套让大模型"说真话"的实战方案》**（博客园）
   - 内容：四阶段实践路径（MVP → 优化检索 → 优化生成 → 工程化），含评估方法
   - 特点：从简单到复杂，适合第4-5周做进阶优化（混合检索、Rerank、查询改写）
   - 链接：https://www.cnblogs.com/syearn/p/19559337

**评估工具（第5周必做）**
- **DeepEval**（RAG 自动化评估）：https://github.com/confident-ai/deepeval
- **Ragas**（评估框架）：https://github.com/explodinggradients/ragas
- 用法：建一个30-50条的评测集，跑 Faithfulness 和 Answer Relevancy 指标

---

### 第 6–9 周：LangGraph 编排 + MCP + 可靠性

#### LangGraph 学习路线（按顺序做）

**官方文档（最权威，每节都有可复制代码）**
- 英文官方文档：https://langchain-ai.github.io/langgraph/
- 中文官方文档：https://langgraph.com.cn
- 官方 Quickstart（第一个动手资料）：从构建 calculator agent 入门

**视频教程（体系化，从零到部署）**

1. **尚硅谷《LangGraph 从入门到部署》**（B站，6大模块，70+节）
   - 内容：State/Node/Edge → 控制流 → 持久化 → 中断与人机协同 → 流式输出 → LangSmith 调试
   - 特点：面向有 Python 基础者，配套代码资料，基于 DeepSeek 实战
   - B站直达：https://www.bilibili.com/video/BV1z3NY66EY1

**7天快速上手计划（官方推荐学习顺序）**

| 天数 | 内容 | 资源 |
|------|------|------|
| 第1天 | 阅读 Overview + Quickstart，跑通第一个 graph | 官方 Quickstart |
| 第2天 | 理解 StateGraph、state、node、edge、conditional_edges | 官方 Tutorial: Chatbots |
| 第3天 | 学习 tool calling，掌握模型决定调工具的机制 | 官方 Tutorial: Agents |
| 第4天 | 学习 checkpointer/memory，状态持久化 | 官方指南: Persistence |
| 第5天 | 学习 streaming 和 interrupt，流式输出 + 人工确认 | 官方指南: Streaming / Human-in-the-loop |
| 第6-7天 | 完成小项目：带记忆的天气/搜索助手 | 自行组合 |

**进阶实战**
- **《LangGraph 生产级实战：6个工程化要点 + 4个踩坑复盘》**（CSDN）
  - 内容：State 设计、循环控制、异步化、超时、错误处理、缓存，每条附可运行代码
  - 链接：https://blog.csdn.net/qq_54655817/article/details/165751729
- **清华大学出版社《LangGraph 1.0 智能体开发实战》**（配套源码+课件）
  - 内容：9种智能体设计模式，含多智能体协作案例
  - 链接：http://www.tup.com.cn/bookscenter/bookpreface?id=11459701

#### MCP 协议学习（第8-9周）

**入门教程（按顺序做）**

1. **《从零搭建一个 MCP Server》**（博客园，Python 完整示例）
   - 内容：FastMCP 框架，注册工具、资源、提示词，接入 Claude Desktop
   - 特点：代码极简，注释详细，30分钟跑通
   - 链接：https://www.cnblogs.com/exioran/p/21686308

2. **《MCP 协议详解：从底层原理到手把手搭建专属 MCP Server》**（微信公众号）
   - 内容：TypeScript + Node.js 完整实现，含工具/资源/提示词三大能力
   - 特点：从协议原理到代码实现，适合理解底层机制
   - 链接：https://mp.weixin.qq.com/s?__biz=MzIyMDE5MjQyNA==&idx=1&mid=2650410513&sn=813e41e9a06b5e723e4ae67e9cb0a809

3. **MCP 官方文档 + 示例 Servers**
   - 官方入门：https://modelcontextprotocol.io/introduction
   - 官方示例 Servers（直接参考）：https://github.com/modelcontextprotocol/servers
   - Python SDK：https://github.com/modelcontextprotocol/python-sdk

4. **《MCP搭建教程》**（官方知识库，多语言对比）
   - 内容：Python / Node.js / Java 三种语言搭建流程 + 客户端集成配置 + 生产部署规范
   - 链接：https://modelcontextprotocol.io（官方文档站）

---

### 第 10–12 周：完整项目（参考案例）

这个阶段没有固定教程，但以下资源可以帮你选题和参考架构：

- **微软《AI Agents for Beginners》**（12节课，覆盖 RAG/多智能体/MCP，含完整项目）
  - 链接：https://github.com/microsoft/ai-agents-for-beginners
- **Datawhale《Hello-Agents》**（中文，从手搓 Agent 到 LangGraph/多智能体）
  - 链接：https://github.com/datawhalechina/hello-agents
- **Hugging Face Agents Course**（交互式，浏览器就能跑）
  - 链接：https://huggingface.co/learn/agents-course
- **LangGraph 官方示例仓库**（真实场景参考）
  - 链接：https://github.com/langchain-ai/langgraph（examples 目录）

---

### 💡 建议的学习节奏

| 周次 | 每天投入 | 产出物 |
|------|----------|--------|
| 第0-2周 | 2-3小时 | 一个能跑的 CLI Agent（≤300行） |
| 第3-5周 | 2-3小时 | 带评估报告的 RAG 知识库问答 |
| 第6-9周 | 3-4小时 | LangGraph Agent + MCP Server + 监控截图 |
| 第10-12周 | 3-4小时 | 一个可演示的完整项目（Docker化 + README） |

每个阶段的教程都是**从"复制代码跑通"开始**，先让代码跑起来建立体感，再逐步改造成自己的东西。遇到框架细节问题，一律回官方文档核对——这个领域更新太快，二手文章容易过时。
