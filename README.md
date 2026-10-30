# Hi, I'm Jiale Yang 👋

软件工程本科生，2028 届。目前专注 **AI Agent 应用开发**。

比起让大模型把话说得更漂亮，我更在意的是：**Agent 在真实业务里出错时，能不能兜住。**
路由要有降级，状态要能恢复，检索要可评测，调用要能追溯 —— 这是我在做的事。

目前主要围绕 `LangGraph`、`FastAPI`、`Spring Boot` 与可观测性工程持续实践。

---

## 🧩 我在做什么

**🤖 Agent 编排与可靠性**
关注多 Agent 的任务分发、失败降级与状态持久化，尤其是「单点 Agent 异常不该拖垮整体响应」这件事怎么在代码里落地。

**📚 混合检索与评测**
关注 BM25 稀疏检索与向量召回的融合（RRF）、重排，以及检索质量怎么量化 —— 而不只是「跑起来能出结果」。

**📊 LLM 可观测性**
关注 trace / span / generation 级别的追踪、token 成本归因与指标告警。也关心一件事：**监控本身不能成为新的故障源**。

---

## 🚀 主要项目

### 上门体育 Onsite Fitness — 上门私教 O2O 平台与 AI Agent 微服务

**独立开发 · 2026.06 – 至今**

[github.com/muyiyang09/onsite-fitness](https://github.com/muyiyang09/onsite-fitness)

#### 为什么做这个项目

上门私教这个场景有三类问题，正好对应三类 Agent 能力：

- **选不出教练** —— 用户不知道该找哪位（增肌 / 减脂 / 拉伸 / 产后恢复，诉求差别很大），只能翻列表看简介
- **评价不可信** —— 评价区几百条，真假难辨，用户没法快速判断
- **资质靠人工审** —— 教练上传的证书要一张张看，慢且容易漏

所以这个项目最后不是「一个 Agent 做所有事」，而是三个子 Agent 各解一类问题，外面套一层 Supervisor 做分发。

#### 我做了什么

**01 · 用 Supervisor 分发三类子任务，并设计失败降级**
教练推荐、评价摘要、资质审核在语义和执行路径上都不一样，用统一 Prompt 硬塞进去只会互相干扰。以 Supervisor 模式做路由，重点是**单点 Agent 异常时整体响应不能挂** —— 降级兜底优先于准确率。

**02 · 混合检索链路，并让它在组件失效时自动降级**
BM25 稀疏检索 + Milvus 向量召回 + RRF 融合 + Reranker 重排。这条链路里任何一环都可能失效，所以 **Milvus 不可用时要能自动降级为 BM25 单路**，而不是直接报错。

**03 · HITL 中断恢复与状态持久化**
用 LangGraph 的 Checkpointer（RedisSaver）保存状态，让人工介入后能从中断点继续，而不是从头重跑。这是「Agent 敢在真实业务里用」的前提。

**04 · 用 MCP 把 Java 业务接口暴露成模型可调用的工具**
业务逻辑在 Spring Boot 里，AI 在 Python 里。与其在 Python 侧重写一遍业务，不如用 MCP 把已有的 Spring Boot 接口按标准协议暴露成 Tool —— **跨语言复用，不重复造**。

**05 · 可观测性：Langfuse + Prometheus / Grafana / Alertmanager**
LLM 的调用链和传统服务不一样，一次请求涉及的 span 和 token 成本需要单独看。接了 Langfuse 做 trace / span / generation 级追踪，指标层用 Prometheus + Grafana + Alertmanager 告警。

#### 一个我想单独讲的取舍

Langfuse 我**默认关闭**，并且做了 **fail-open** —— 可观测性组件自己挂掉时，主业务链路照常走。

理由很简单：监控是为了发现问题，不是为了制造问题。如果接了监控之后，Langfuse 抖一下用户就用不了，那这个监控不如不接。**可靠性建设的第一步，是别让自己成为新的单点。**

#### 技术栈

`LangGraph` `Python` `FastAPI` `Spring Boot` `MyBatis` `MySQL` `Redis` `Milvus` `MCP` `HITL` `Checkpointer(RedisSaver)` `Langfuse` `Prometheus` `Grafana` `Vue 3` `uni-app` `Docker`

---

## 💼 实习经历

### 大连校联科技有限公司 · 后端开发实习生

**2025.12 – 2026.04**

参与企业代码管理平台与跨语言服务集成两类系统的开发。

- **GitLab 代码管理平台**：负责仓库批量自动化创建的核心接口，支持单次批量创建多个仓库，替代原有人工逐个建仓的流程；设计 API 调用间隔与重试策略，规避 GitLab API 限流；开发代码提交统计模块；实现项目技术栈自动识别（分析项目文件结构与依赖描述文件）。
- **跨语言服务集成系统**：负责 Java 主站与 Python FastAPI 服务之间的跨语言调用。爬虫属长耗时任务，与同步 HTTP 调用天然冲突，因此采用「提交任务 + 状态查询」的两段式调用，并为任务定义完整生命周期状态（启动 / 运行中 / 停止 / 完成 / 失败），保证长任务可追踪；封装统一 HTTP 客户端，做到连接超时与读超时分离、带退避策略的重试；统一异常分类与链路日志，跨服务调用失败能定位到具体下游任务。

**这段经历让我意识到：跨服务调用最难的不是把请求发出去，而是失败之后能不能定位到是哪一环、哪一次。** 所以后面做 AI 服务时，我对状态机和链路日志一直很在意。

`Spring Boot` `MyBatis` `Vue` `ECharts` `GitLab4J API` `RestTemplate` `FastAPI` `MySQL` `Redis` `Eureka` `Spring Cloud Alibaba`

---

## 🛠️ 技术栈

| 方向 | 技术 |
|---|---|
| AI 应用 | LangGraph / LangChain、Multi-Agent 编排、Supervisor 路由与降级、HITL、Checkpointer（RedisSaver）、MCP（Server / Client）、RAG 混合检索（BM25 + 向量 + RRF）、Reranking、Structured Output、Eval Harness |
| 后端 | Python / FastAPI、Pydantic、Java / Spring Boot、MyBatis、Spring Cloud Alibaba、Eureka、RESTful API、JWT |
| 数据与中间件 | MySQL、Redis、Milvus |
| 可观测性与工程 | Langfuse、Prometheus / Grafana / Alertmanager、Docker Compose、Git / GitHub Actions、Linux |
| 前端 | Vue 3、uni-app、TypeScript、Element Plus、Vite |

---

## 🏆 荣誉

- 2025 年全国大学生数学建模竞赛 吉林省一等奖

---

## 🌱 目前在学习

- Agent 工作流评测与回归测试（怎么证明改了 Prompt 之后没有变差）
- 检索质量调优与 Reranker 选型
- LLM 成本控制与语义缓存
- AI 服务的生产可观测性

---

## 📫 联系我

- GitHub：[@muyiyang09](https://github.com/muyiyang09)
- Email：muyiyang181@qq.com ｜ muyiyang181@gmail.com

目前开放 **AI Agent / AI 应用开发方向的实习机会**：每周可到岗 5 天，可连续实习 6 个月以上，**2026 年 12 月中旬可开始**，可远程、可异地。

如果你也在做 Agent 或 RAG 方向，欢迎交流。

*Keep building.*
