# 关于Github主页和项目的简介

## Introduction to GitHub Profile and Projects

# Hi, I'm Jiale Yang 👋

软件工程本科生，专注于 **AI Agent 应用开发工程师** 岗位。

Software Engineering undergraduate focused on building production-grade AI Agent applications across LLM orchestration, retrieval, and observability.

目前主要关注：

* 大模型应用开发 / LLM Application Development
* AI Agent 多智能体编排、Supervisor 路由与降级
* RAG 混合检索（BM25 + 向量 + RRF）与检索质量评测
* 大模型可观测性与评测 Harness
* MCP 跨语言工具层与业务系统集成
* Java / Python 全栈应用开发

我具备完整的多模块工程实践经验，能够参与从需求拆解、接口设计、领域建模，到 AI 能力接入、检索链路设计、工程加固与可观测性建设的完整开发流程。

I have experience across multi-module engineering projects, covering requirement breakdown, API design, domain modeling, LLM integration, retrieval pipelines, service hardening, and observability.

---

## 🧭 Current Focus

* Building Agent systems that are observable, evaluable, and regression-testable 
* Integrating LLMs with real business systems and domain state machines
* Improving retrieval quality through hybrid search and RRF tuning
* Hardening AI services: HITL, checkpointing, rate limiting, token budget
* Exploring Agent evaluation, reranking, and LLM observability

---

## 🛠️ Tech Stack

### Frontend

* Vue 3
* uni-app
* JavaScript / TypeScript
* Element Plus
* Vite

### Backend

* Java / Spring Boot
* MyBatis
* Python / FastAPI
* Pydantic / SQLAlchemy
* RESTful API
* JWT
* WebSocket

### Database & Infrastructure

* MySQL
* Redis
* Milvus
* Docker / Docker Compose
* Prometheus / Grafana / Alertmanager
* Git / GitHub Actions
* Linux

### AI Application Development

* LangGraph / LangChain
* LiteLLM
* DeepSeek API
* Multi-Agent Orchestration
* Supervisor Routing & Fallback
* Hybrid Retrieval（BM25 + Vector + RRF）
* Reranking
* MCP（Server / Client）
* HITL（Human-in-the-Loop）
* Checkpointing（RedisSaver）
* Prompt Engineering
* Structured Output
* Output Validation & Fallback
* Langfuse Observability
* Eval Harness

---

## 🚀 Featured Projects

### Sports Takeout — 上门私教 AI Agent 平台

[View Repository](https://github.com/muyiyang09/sports-takeout)

面向「上门私教」O2O 场景的智能服务平台，在传统业务系统之上独立构建 AI 微服务，实现教练智能推荐、评价摘要与资质智能审核三类 Agent 能力。

An O2O platform for at-home personal training, with a standalone AI microservice delivering coach recommendation, review summarization, and certificate verification agents.

**My Work**

* 设计并实现 AI 微服务：多 Agent 编排、Supervisor 路由与降级策略
* 构建混合检索链路：BM25 + Milvus 向量 + RRF 融合，Milvus 不可用时降级单路
* 落地循环工程：条件分支、失败重试、HITL 中断恢复、Checkpointer 状态持久化
* 封装 MCP 工具层，将 Spring Boot 业务接口暴露为大模型可调用工具
* 建设可观测性：Langfuse trace / span / generation + token 成本，Prometheus / Grafana / Alertmanager 指标告警
* 完成工程加固：限流熔断、Token 预算管控、缓存穿透/击穿/雪崩三防、服务间密钥鉴权

**Keywords**

`LangGraph` `Multi-Agent` `Hybrid RAG` `MCP` `HITL` `FastAPI` `Spring Boot` `Milvus` `Langfuse`

---

## 💼 Experience

### Full-Stack Development Intern · 大连校联科技有限公司

2024.12 - 2026.05

独立完成业务模块的数据库表结构设计，编写 RESTful API 接口并支撑业务需求快速迭代；配合团队将原有单体调用改造为基于 Eureka 的服务注册与发现模式，把服务调用方与被调用方解耦，解决了模块间的硬编码调用问题；负责核心业务接口开发与性能优化，接口响应时间优化到 200ms 以内；承担前后端接口联调，并独立完成数据统计模块的 ECharts 可视化图表；参与代码评审与技术方案讨论。

Worked as a full-stack intern on enterprise code-management and cross-language service systems: designed database schemas, built RESTful APIs, migrated monolithic service calls to Eureka-based service discovery, and optimized core interfaces to sub-200ms response times. Also handled front-end/back-end integration and independently built ECharts visualizations for the statistics module.

主要实践包括：

* **GitLab 代码管理平台**（2025.09 - 2026.02）：负责仓库批量自动化创建核心接口，支持单次批量创建多个仓库；设计 API 调用间隔与重试策略，规避 GitLab API 限流；开发代码提交统计模块，支持按时间范围统计提交次数与代码行数变更；实现项目技术栈自动识别（分析项目文件结构）。批量任务成功率提升至 99% 以上，接口平均响应时间控制在 500ms 以内，技术栈识别准确率达 95% 以上。
* **跨语言服务集成系统**（2026.02 - 2026.04）：负责 Java 主站与 Python FastAPI 服务之间的跨语言调用。爬虫属长耗时任务，与同步 HTTP 调用天然冲突，因此采用「提交任务 + 状态查询」的两段式调用，并为任务定义生命周期状态（启动 / 运行中 / 停止 / 完成 / 失败），保证长任务状态可追踪；封装统一 HTTP 客户端，实现连接超时与读超时分离、带退避策略的重试；统一异常分类与链路日志，跨语言调用失败可定位到具体下游任务。

**Keywords**

`Spring Boot` `MyBatis` `Vue` `ECharts` `GitLab4J API` `RestTemplate` `FastAPI` `MySQL` `Redis` `Eureka` `Spring Cloud Alibaba`

---

## 🎓 Education & Honors

**吉林农业科技学院** — 软件工程（本科，2024 - 2028）

* 2025 年中国大学生数学建模竞赛 吉林省一等奖

---

## 🌱 What I'm Learning

* Agent workflow evaluation and regression testing
* Reranking and retrieval quality tuning
* Multi-agent collaboration patterns
* LLM cost control and semantic caching
* Production observability for AI services

---

## 📫 Contact

* GitHub: [@muyiyang09](https://github.com/muyiyang09)
* Email: muyiyang181@gmail.com

Open to opportunities in:

* AI Agent 应用开发工程师
* 大模型应用开发工程师
