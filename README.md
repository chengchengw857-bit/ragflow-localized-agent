# 基于 RAGFlow 的企业级私有化智能知识库 🚀

<p align="center">
  <a href="https://github.com/chengchengw857-bit/ragflow-localized-agent">
    <img src="https://raw.githubusercontent.com/infiniflow/ragflow/main/graphics/ragflow_logo.png" alt="RAGFlow Logo" width="400">
  </a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.11-blue.svg" alt="Python">
  <img src="https://img.shields.io/badge/RAGFlow-v0.27.1-brightgreen.svg" alt="RAGFlow">
  <img src="https://img.shields.io/badge/Docker-Supported-blue.svg" alt="Docker">
  <img src="https://img.shields.io/badge/License-Apache%202.0-yellow.svg" alt="License">
</p>

---

**ragflow-localized-agent** 是一个基于开源 RAGFlow 引擎深度构建的**企业级私有化智能知识库系统**。

针对供应链场景下海量复杂的 PDF 扫描件、海关单据、合同及结构化表格，本项目通过全流程本地化部署，提供高精度的深度文档解析、智能体（Agent）工作流编排与高可信度的上下文问答能力。

---

## 🌟 核心特性

- 📄 **深度文档理解 (Deep Document Understanding)**
  - 集成 LayoutLM 与 OCR 视觉算法，完美解析复杂 PDF 扫描件、双栏排版、供应链拓扑图及嵌套表格。
  - 规避传统 RAG 系统中段落切片（Chunking）导致的上下文丢失。
- 🛡️ **全栈私有化与本地化部署**
  - 基于 Docker 容器化技术，数据不外流，支持私有化大语言模型（如 Qwen-Chat 系列）本地调用，保障供应链核心机密。
- 🤖 **Agent 智能体工作流编排**
  - 内置 Agent 工作流引擎，支持多步推理（Chain of Thought, CoT）链路设计，结合混合检索及重排（Rerank）机制，大幅降低模型幻觉。

---

## 🏗️ 系统架构与数据流向

```text
[非结构化文档] (PDF/Excel/图片) 
       │
       ▼ (深度文档理解: Layout + OCR)
[精准语义分块 (Chunks)]
       │
       ▼ (Embedding 向量化)
[向量数据库 (Milvus/ES)] ◄─── (混合检索 + Rerank 优化) ───► [用户提问 (Prompt)]
       │                                                         │
       └───────────────────► [Agent 决策流/CoT] ◄────────────────┘
                                    │
                                    ▼ (本地私有化 LLM 召回)
                             [高可信度场景回答]
