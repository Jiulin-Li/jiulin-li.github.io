---
permalink: /
title: "李九林 / Jiulin Li"
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

## 你好，我是李九林

我是一个 **AI-Native 的产品与工程实践者**：既做多模态大模型和 Agent 系统研究，也做从 0 到 1 的 AI 产品、后端服务、前端体验、支付交付、数据资产、运维发布和多 Agent 协作流程。

我就读于北京邮电大学计算机技术硕士项目，曾在北京通用人工智能研究院（BIGAI）参与 Any2Any 多模态大模型系统与多智能体框架工作，同时创办并主导建设六艺AI，围绕 AI 传统文化内容产品、垂直领域算法库、数据集与评测、全栈 Web 工程和 agent-assisted DevOps 做持续实践。

我不只把 AI 当作调用接口的工具，而是把它当作新的研发与产品组织方式：用 Agent 拆解任务、沉淀上下文、执行数据工作流、辅助部署验收、压缩长对话历史，并把结果转化为可复用的产品、文档和工程资产。

[查看完整项目集](/projects/) ｜ [English version](/en/) ｜ [Google Scholar](https://scholar.google.com/citations?user=730nEoQAAAAJ&hl=zh-CN&oi=ao) ｜ [六艺AI](https://www.liuyi.life)

## 能力关键词

- **AI Agent 与工作流**：Multi-Agent，Context Engineering，工具调用，MCP/Function Call 理解，subagent 任务拆解，cron agent 定时执行，OpenClaw/Codex/Claude 协作，长上下文压缩与事实库治理。
- **多模态与大模型工程**：MLLM，Any2Any，Qwen2.5-Omni，Wan2.1，Diffusion，VILA-U，NeXT-GPT，Open-Sora，指令数据构建，模型部署与评测，benchmark 设计。
- **产品与全栈工程**：React 19，Vite，TypeScript，FastAPI，Postgres，支付/订单/券码，报告生成服务，SKU 配置，运营看板，systemd/nginx/CDN 发布验收。
- **数据与评测**：垂直领域数据集，结构化知识抽取，QA 生成，provenance，去重缓存，模型评测标准，AI-Native 数据资产构建。
- **研究能力**：视觉语言模型、测试时增强、视频理解、即时配送优化，已发表 CCF-A / CCF-C / JCR Q2 论文，并拥有授权专利。

## 我正在寻找的方向

我更适合需要“技术理解 + 产品判断 + 工程落地 + AI-Native 工作方式”的岗位，例如：

- AI Agent / AI 工具链研发
- 大模型应用与 AI 策略产品工程
- 多模态大模型算法与工程落地
- AI 编程产品、Agent 平台、开发者工具
- AI 产品从 0 到 1、数据资产构建和业务闭环

## 代表项目

### 六艺AI：AI 传统文化内容产品与商业化闭环

我主导建设了六艺AI，一个面向传统文化/个性化报告场景的 AI 内容产品。公开站点已上线：[www.liuyi.life](https://www.liuyi.life)。产品链路覆盖热门议题、出生信息输入、结构化问卷、免费预览、微信/支付宝支付、兑换码、完整报告生成、我的报告找回、服务协议和隐私政策。

工程侧，FateRipple 仓库包含 React/Vite/TypeScript 前端、FastAPI Base 后端、FastAPI GenService 生成服务和 Postgres 数据库。后端负责认证、档案、报告、订单、支付、钱包、活动、staff 工具和运营看板；生成服务负责批量运势、热门议题报告、报告生成和调度任务。围绕 SKU-Settings、SKU_DEV、GenMonitor、Ops Dashboard、礼品券码脚本和 HARNESS 部署文档，我把产品内容、生成链路、商业化交付和运维验收串成一个可迭代系统。

### DingMing：命理 AI 基座算法库与 YiWorld 服务

DingMing 是我主导沉淀的垂直领域 Python 核心库，按“核心库 + 外置应用”模式组织，核心算法包构建传统文化推理基本算法，包括排盘、生克分析、报告分析链路等。将八字算法浓缩到算法库中。

在应用层，我将排盘与报告能力封装为 YiWorld 基础算法服务、AWS Lambda + Supabase 异步报告生成服务、React 前端和飞书机器人后端，让同一套规则计算、结构化中间结果、prompt 模板和 LLM 报告能力可以被多个产品入口复用。

### OpenClaw 多 Agent 指挥与数据资产构建

我长期维护并调度 OpenClaw agent，把复杂任务拆解为 subagent 任务和 cron agent 定时任务，组织 agent 执行 B站/社媒命理内容采集、作者发现、作者池扩展、JSONL 增量写入、去重、状态更新和飞书日报回传。

这套流程不是单次聊天，而是一种 agent operations：任务中明确要求读取 skill 文档、使用 browser snapshot、避免把完整作者池塞入上下文、更新 `author_pool.json` / `author_status.json` / `stats_summary.json`，并在 SIGTERM 中断、数据不一致、权限和文件上传问题出现时继续排障与总结。后续我又把两个 OpenClaw 历史包压缩成 archive index、session summaries、command digest 和项目卡，合并进简历事实库。

### BIGAI Any2Any 与 MAGUS 多智能体多模态系统

在 BIGAI，我参与 Any2Any 多模态大模型系统建设，调研 2023 至 2025 年的前沿多模态模型、编码器和数据集，部署评测 VILA-U、NeXT-GPT、Wan2.1、Open-Sora，探索 VAE projector 与多模态指令数据构建，完成硬路由式全模态理解与生成系统，并扩展情绪分析专家能力。

该工作进一步发展为 **MAGUS: A Unified Multi-Agent Framework for Universal Multimodal Understanding and Generation**。MAGUS 将多模态理解与生成拆为 Cognition 与 Deliberation 两阶段，通过 Perceiver、Planner、Reflector 等角色化 MLLM agents 和 Growth-Aware Search 协调 LLM 推理与 diffusion 生成。论文已在 arXiv 发布：[arXiv:2508.10494](https://arxiv.org/abs/2508.10494)。

### 垂直领域 Benchmark 与 QA 数据管线

我建设了命理 benchmark 数据集与 QA 生成管线，从原始书籍、章节切分、结构化抽取、命例题生成到 provenance 和去重缓存，形成三阶段数据流程。当前内部事实库记录 `stage3_qa_data/qa_summary.json` 中包含 76,431 条 QA 数据，其中 `mingli_question` 68,095 条、`mingli_example` 8,336 条。公开使用该规模前仍需确认版权和披露边界。

## 研究与论文

- **MAGUS: A Unified Multi-Agent Framework for Universal Multimodal Understanding and Generation**, arXiv, 2025. [link](https://arxiv.org/abs/2508.10494)
- **WaveDN: A Wavelet-based Training-free Zero-shot Enhancement for Vision-Language Models**, ACM MM 2024, CCF-A. [link](https://dl.acm.org/doi/10.1145/3664647.3681559)
- **Enhancing the Zero-shot Capability of Vision-Language Models from the Perspective of Modality Divergence / AdaDN**, manuscript under review, 2025.
- **A Fuzzy Error Based Fine-Tune Method for Spatio-Temporal Recognition Model**, PRCV 2023, CCF-C. [link](https://link.springer.com/chapter/10.1007/978-981-99-8429-9_8)
- **Meal delivery routing optimization with order allocation strategy based on transfer stations for instant logistics services**, IET Intelligent Transport Systems, 2022. [link](https://ietresearch.onlinelibrary.wiley.com/doi/pdf/10.1049/itr2.12206)
- **Real-time logistics order splitting method, apparatus, device, and storage medium**, CN112950119B, 2022. [link](https://patents.google.com/patent/CN112950119B/zh)

## 教育与荣誉

- 北京邮电大学，计算机技术硕士，2023-2026（预计）
- 北京邮电大学 + Queen Mary University of London，物联网工程本科，First Class Honours，2019-2023
- 硕士研究生国家奖学金，2024-2025
- 北京市级优秀毕业生，2026
- 北京邮电大学校级优秀毕业生，2026
- 北京邮电大学优秀研究生，2024
- 网络与交换技术全国重点实验室优秀研究生，2024
- 北京邮电大学硕士研究生一等奖学业奖学金，2023-2024、2024-2025
- 北京邮电大学硕士研究生一等奖学业奖学金，2025-2026
- 全国“互联网+”快递业创新创业大赛银奖，2022



*Last updated: May 2026*
