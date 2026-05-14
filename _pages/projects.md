---
layout: single
title: "项目全集"
permalink: /projects/
author_profile: true
---

这里按类别和时间整理我的主要项目。首页只放代表性项目，本页保留更完整的项目脉络，方便快速了解我做过的 AI 产品、Agent 工作流、多模态系统、数据集、后端平台和科研工作。

## AI 产品与平台工程

### 2025.10-至今：六艺AI / FateRipple 全栈 AI 报告产品

- **定位**：AI 传统文化内容产品、个性化报告平台、商业化交付链路。
- **角色**：CEO / CTO / 产品负责人。
- **公开站点**：[www.liuyi.life](https://www.liuyi.life)
- **核心链路**：热门议题 -> 出生信息与问卷 -> 结构化命盘分析 -> 免费预览 -> 微信/支付宝支付或兑换码 -> 完整报告生成与找回。
- **工程栈**：React 19，Vite，TypeScript，FastAPI，Postgres，DingMing，Dulupay，SKU 配置，GenService，Ops Dashboard，systemd，nginx，CDN。
- **后端与生成服务**：Base 后端负责认证、档案、运势查询、报告、订单、支付、钱包、活动、staff 工具和运营看板；GenService 负责批量运势、热门议题、君臣/报告生成、单议题报告生成和调度任务。
- **商业化与运营工具**：SKU-Settings 作为唯一运行时配置目录；SKU_DEV 支持候选 SKU 编辑、prompt 调试和样例输入验证；Ops Dashboard 聚合订单、收入、漏斗、功能访问、议题表现和 GenService 健康状态；礼品券码脚本支持生成、查询和停用报告券码。

### 2025-2026：DingMing 命理 AI 基座算法库与 YiWorld 服务

- **定位**：垂直领域算法核心库 + 报告生成服务 + 多应用入口。
- **核心库**：`dingming==0.0.2`，按“核心库 + 外置应用”组织。
- **核心模块**：`Ming`、`PanEngine`、`ReportManager`、`ReportStreamManager`、Romance/Career/SelfRomance/Hepan 报告服务、FateRippleSupporter。
- **算法能力**：纯排盘规则计算、真太阳时、大运/年份范围查询、YiWorld 查询、君臣 COT 分析、结构化中间结果和 prompt 模板。
- **服务化**：LiuyiYiWorldBaseServer 将排盘核心能力封装为 FastAPI 服务，提供简版/详细版排盘、大运查询、年份范围查询、API Key 鉴权、限流、防爆破和审计日志。
- **应用集成**：LiuyiWorld 使用 AWS Lambda + Supabase 异步队列生成报告；LiuyiWorldFrontend 使用 React 19 + Vite + Tailwind 承接用户输入、购买/券码和轮询展示；LarkQAServer 提供飞书长连接机器人 `/lead`、`/ask` 能力。

### 2026：AI 命理报告深度解析与 AI-Native 测评体系

- **定位**：面向私域场景的高客单内容型 AI 报告交付方案。
- **输入**：生辰信息、问卷回答、具体问题场景。
- **输出**：命盘结构分析、AI 内容生成、个性化报告。
- **主题**：感情、事业、财运、关系、阶段决策、自我成长、阶段运势。
- **研究布局**：用 AI-Native 方式构建数据集与测评体系，定义垂直领域模型“算准”的标准。

## Agent 工作流、运维与数据资产

### 2026.03-2026.05：OpenClaw 多 Agent 指挥与数据资产构建

- **定位**：AI-native engineering management / agent operations / 数据资产构建。
- **工作方式**：维护并调度 OpenClaw agent，通过主对话、subagent task、cron task、skill workflow 和飞书回传组织长期任务。
- **核心任务**：B站/社媒命理内容采集、作者发现、作者池扩展、JSONL 增量写入、去重、状态更新、执行摘要和每日汇报。
- **调度设计**：B站内容抓取按每 30 分钟执行，B站作者发现按每 1 小时执行；每次返回处理作者数、新增记录数、发现关联作者数、拒绝数、新标记 exhausted 关键词数和作者池统计。
- **工程约束**：读取 skill 文档、使用 browser snapshot、避免把整个作者池塞入上下文、预去重、增量写 JSONL、更新 `author_pool.json` / `author_status.json` / `stats_summary.json`、处理 retry queue 和 SIGTERM 中断后的摘要。
- **知识治理**：将两个 OpenClaw 历史包压缩为 archive index、session summaries、command digest 和项目卡，再合并进标准化简历事实库。

### 2026：HARNESS / nanobot Agent 驱动部署与资料治理

- **定位**：Agent-assisted DevOps、发布工程、知识治理。
- **范围**：FateRipple 维护 `AGENTS.MD`、`HARNESS/DEPLOYMENT.md`、`HARNESS/SERVER.md`、`HARNESS/COMMIT_RULE.md`。
- **部署规范**：通过 nanobot 在服务器执行 git pull、依赖安装、rsync、systemd restart、健康检查、前端构建与静态目录同步。
- **配置与验收**：线上配置真源统一为 `/liuyi/service_config/{服务名}.envs`；部署后校验 systemd、实际进程配置路径、源站 `origin.liuyi.life` 与 CDN 域名 `www.liuyi.life` / `liuyi.life`。
- **资料治理**：将业务 PRD、支付计划、增长方案、服务器运维、benchmark 管线、简历事实库等跨项目资料沉淀到 agentOS_docs。

## 多模态大模型与算法工程

### 2025.03-2025.08：BIGAI Any2Any 多模态大模型系统

- **机构**：北京通用人工智能研究院（BIGAI）
- **方向**：Any2Any 多模态理解与生成、多模态模型部署评测、多智能体协作式多模态系统。
- **模型与工具**：VILA-U，NeXT-GPT，Wan2.1，Open-Sora，Qwen2.5-Omni，Wan2.1-VACE，AudioLDM2，EmotiVoice，VAE projector，LLaMA Factory。
- **工作内容**：调研 2023-2025 前沿多模态模型、模态编码器和多模态数据集；部署与评测 VILA-U、NeXT-GPT、Wan2.1、Open-Sora；探索 VAE 多模态编码；构建多模态指令数据并尝试 MLLM 指令微调。
- **系统建设**：实现硬路由式 text/image/audio/video 全模态理解与生成系统，扩展情绪分析专家能力，并完成多智能体协作式多模态系统设计、实现与集群部署。

### 2025.07-2025.08：MAGUS 全模态多智能体框架

- **论文**：[A Unified Multi-Agent Framework for Universal Multimodal Understanding and Generation](https://arxiv.org/abs/2508.10494)
- **方向**：Any-to-Any 多模态理解与生成、多智能体协作、LLM 与 diffusion 模型协同。
- **架构**：将多模态理解与生成拆分为 Cognition 与 Deliberation 两阶段。
- **Agent 设计**：Cognition 阶段包含 Perceiver、Planner、Reflector 三类角色化 MLLM agents，在共享文本工作区协作理解与规划。
- **推理生成协同**：Deliberation 阶段通过 Growth-Aware Search 协调 LLM 推理与 diffusion 生成。
- **特点**：支持 text、image、audio、video 的可插拔 Any2Any 理解与生成，无需联合训练。

## 数据集、Benchmark 与评测

### 2026：命理 Benchmark 数据集与 QA 生成管线

- **定位**：中文垂直领域 QA benchmark、AI 评测、RAG/Agent 评测数据。
- **流程**：`stage0_raw_books -> stage1_chapter_texts -> stage2_fine_text -> stage3_qa_data`。
- **数据处理**：原始电子书、章节纯文本、结构化抽取、知识单元、命例抽取、QA 生成、provenance 和去重缓存。
- **当前内部规模**：事实库记录 `qa_summary.json` 含 76,431 条 QA 数据，其中 `mingli_question` 68,095 条、`mingli_example` 8,336 条。公开使用前需确认版权、来源和披露边界。
- **论文准备**：已整理 benchmark 论文可强调的任务定义、数据构建、评测维度、评价方法、基线实验和误差分析口径。

### 2026：B站/社媒命理内容数据资产

- **定位**：为垂直 AI 产品、内容洞察和数据资产建设提供外部内容样本。
- **方式**：通过 OpenClaw agent、browser snapshot、Bilibili author discovery/content crawl skills 组织持续抓取。
- **治理**：作者池、作者状态、统计摘要、去重哈希、retry queue、每日汇报。
- **注意**：该部分涉及平台内容和合规边界，公开页面只描述流程能力，不公开原始数据包和敏感账号信息。

## 视觉语言模型、视频理解与智能交通研究

### 2023.11-2025.01：WaveDN 视觉语言模型测试时增强

- **论文**：[WaveDN: A Wavelet-based Training-free Zero-shot Enhancement for Vision-Language Models](https://dl.acm.org/doi/10.1145/3664647.3681559)，ACM MM 2024，CCF-A。
- **问题**：视觉语言模型后处理可能造成信息损失，影响零样本分类和图文检索。
- **方法**：从信号处理视角提出 WaveDN，训练无关，部署友好。
- **贡献**：完成 idea、实现、实验、论文写作与修改，并组织实习生推进任务。

### 2023.11-2025.01：AdaDN 模态差异自适应归一化

- **论文状态**：Manuscript under review, 2025。
- **问题**：已有 distribution-normalization 方法忽略文本与图像模态分布差异，可能造成文本语义损失或图像归一化不足。
- **方法**：根据特征熵动态调整归一化强度，文本端弱归一化保护语义，图像端强归一化增强对齐。
- **验证**：在超过 10 个数据集和多个视觉语言模型上验证性能与鲁棒性提升。

### 2022.11-2023.06：3D CNN 视频理解中的模糊误差微调

- **论文**：[A Fuzzy Error Based Fine-Tune Method for Spatio-Temporal Recognition Model](https://link.springer.com/chapter/10.1007/978-981-99-8429-9_8)，PRCV 2023，CCF-C。
- **问题**：3D CNN 在低信息量视频帧上容易产生高置信错误预测，影响视频级结果聚合。
- **方法**：设计 fuzzy error loss 进行微调，降低低语义信息片段对最终预测的负面影响。

### 2021.07-2022.06：即时配送订单拆分与路径优化

- **论文**：[Meal delivery routing optimization with order allocation strategy based on transfer stations for instant logistics services](https://ietresearch.onlinelibrary.wiley.com/doi/pdf/10.1049/itr2.12206)，IET Intelligent Transport Systems，JCR Q2。
- **专利**：[CN112950119B](https://patents.google.com/patent/CN112950119B/zh)
- **角色**：学生团队负责人。
- **问题**：城市即时配送中的长距离跨区域订单影响整体配送效率。
- **方法**：提出订单拆分与中转站策略；旧简历记录使用 ALNS heuristic 做路径规划，使用 LSTM 预测配送时间。

## 产品、增长与商业化方案

### 2026：单议题快消报告 V1 与增长链路

- **产品方案**：SKU、免费预览、支付/兑换解锁、我的报告找回。
- **增长方案**：外部平台内容、H5 免费结果卡、热门议题转化、兑换码/KOC、私域召回。
- **工程落点**：已与 FateRipple 热门议题、SKU-Settings、GenService、支付和报告链路结合。

### 2026：Ops Dashboard 与 GenService 配置工具

- **Ops Dashboard**：独立 FastAPI + Basic Auth，聚合订单、收入、访问转化漏斗、功能访问、热门议题表现、近期订单和 GenService 健康/日志摘要。
- **GenMonitor**：本地静态页面生成 GenService `.envs.dev` / `.envs.prod` 模板，输出本地启动与 systemd/nohup 运行建议。

## 项目组合视角

- **AI Agent / 工具链**：OpenClaw 多 Agent 指挥、HARNESS/nanobot、MAGUS、命理 benchmark。
- **AI 产品 / 产品工程**：六艺AI、FateRipple、DingMing/YiWorld、单议题快消报告、Ops Dashboard。
- **多模态算法工程**：BIGAI Any2Any、MAGUS、WaveDN、AdaDN。
- **数据 / 评测**：命理 benchmark、B站/社媒内容数据资产、多模态指令数据。
- **后端 / 平台**：FastAPI 服务拆分、支付订单状态恢复、GenService、YiWorld 基础服务、systemd/nginx/CDN 部署。
