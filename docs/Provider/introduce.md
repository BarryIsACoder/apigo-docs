# 一、国外主流厂商（深度版）
## 1.1 OpenAI
### 厂商基本信息
* 厂商名：OpenAI
* 归属地：美国
* 成立时间：2015
* 定位：通用人工智能（AGI）研究与商业化

### 商业模式：
* 官方 API（OpenAI Platform）
* ChatGPT（ToC + ToB）
* 云厂商授权（Azure OpenAI）

### 技术路线：
* 大规模 Transformer
* 多模态统一模型（GPT-4o / GPT-5）
* 强调工具调用、推理能力、系统性工程优化

### 官网：
* https://openai.com
* https://platform.openai.com/docs

### OpenAI 代表性模型总览
| 模型 ID               | 别名   | 类型 |
|---------------------|------|----|
| gpt-5 / gpt-5-chat  | GPT-5 | 文本 / 多模态 |
| gpt-4o | GPT-4 Omni | 文 / 图 / 音 |
| gpt-4.1 | GPT-4.1 | 文本 |
| gpt-4o-mini | 轻量多模态 | 文 / 图 |
| o1 / o3 | 推理模型 | 文本 |
| dall-e-3 | 图像生成 | 图像 |
| whisper-1 | 语音识别 | 音频 |

### 单模型关键能力表
* GPT-4o（核心生产模型）

| 维度 | 说明                      |
| --- |-------------------------|
| 模型 ID | gpt-4o                  |
| 输入能力 | 文本、图片（URL / base64）、音频  |
| 输出能力 | 文本、JSON、音频（部分接口）、工具调用   |
| 上下文长度 | ~128K tokens            |
| 架构特性 | 统一多模态 Transformer（非拼接）  |
| 优势 | 低延迟、多模态一致性强 |
| 典型场景 | AI 助手、客服、图文理解、代码 Copilot |
| Vendor | OpenAI / Azure OpenAI |
* o1 / o3（推理模型）

| 维度 | 说明                      |
| --- |-------------------------|
| 模型类型 | 推理增强模型（Reasoning-first） |
| 输入 | 文本                      |
| 输出 | 文本                      |
| 特点 | 内部多步思考、逻辑推理能力强          |
| 成本 | 高于 gpt-4o-mini          |
| 适用场景 | 数学、规划、复杂业务规则 |

## 1.2 Anthropic（Claude）
### 厂商基本信息
* 厂商名：Anthropic
* 归属地：美国
* 创始背景：前 OpenAI 团队
* 核心理念：Constitutional AI（可控、安全、可靠）
* 技术特点：
  * 极强长文本能力
  * 更“稳态”的对话输出
  * 非常适合企业内部文档处理

### 官网：
* https://www.anthropic.com/claude

### Claude 模型家族
| 模型 ID | 系列 | 定位 |
| --- | --- | --- |
| claude-3-opus | Opus | 高端 |
| claude-3.5 / 3.7-sonnet | Sonnet | 主流 |
| claude-3-haiku | Haiku | 低成本 |
### 单模型关键能力表
* Claude 3.7 Sonnet（主力）

| 维度 | 说明     |
| --- |--------|
| 输入 | 文本、图片  |
| 输出 | 文本、结构化 JSON |
| 上下文 | 200K tokens |
| 架构特性 | 超长上下文优化 |
| 优势 | 阅读、总结、分析能力极强 |
| 典型场景 | 法务、投研、长文档问答 |
| Vendor | Anthropic / 云代理 |

## 1.3 Google DeepMind / Gemini
### 厂商基本信息
* 厂商名：Google DeepMind
* 归属地：美国
* 优势领域：
  * 多模态
  * 工程化稳定性
  * 原生云整合（Vertex AI）

### 官网：
* https://ai.google.dev
* https://cloud.google.com/vertex-ai

### Gemini 系列
| 模型 | 定位 |
| --- | --- |
| Gemini 2.5 Pro | 高端多模态 |
| Gemini 2.5 Flash | 低延迟 |
| Gemini Flash Image | 图像理解 |

### 单模型关键能力表
* Gemini 2.5 Pro

| 维度 | 说明 |
| --- | --- |
| 输入 | 文、图、视频（GCS URI） |
| 输出 | 文本 |
| 架构 | 原生多模态 |
| 优势 | 视频理解、工程集成 |
| 场景 | 媒体分析、内容审核 |
| Vendor | Vertex AI |

## 1.4 xAI（Grok）
### 厂商基本信息
* 厂商名：xAI
* 归属地：美国
* 背景：Elon Musk
* 特点：
  * 实时信息
  * 强推理取向
  * 社交内容分析

### Grok 模型
| 模型 | 说明 |
| --- | --- |
| grok-3 | 标准 |
| grok-3-fast | 低延迟 |
| grok-4 | 推理增强 |

### 单模型关键能力
* Grok-4

| 维度 | 说明 |
| --- | --- |
| 输入 | 文本 |
| 输出 | 文本 |
| 优势 | 实时性、观点分析 |
| 场景 | 舆情、社交分析 |

# 二、国内主流厂商
## 2.1 阿里云（通义 / Qwen）
### 厂商信息
* 厂商名：阿里云
* 归属地：中国
* 平台：百炼
* API 特点：
  * OpenAI 兼容
  * 支持私有化 / 专有云

### Qwen 模型
| 模型 | 定位 |
| --- | --- |
| qwen-max | 高端 |
| qwen-plus | 主流 |
| qwen-turbo | 低成本 |
| qwen-vl | 多模态 |

### 单模型关键能力
* Qwen-Max

| 维度 | 说明 |
| --- | --- |
| 输入 | 文本、图片 |
| 输出 | 文本 |
| 上下文 | 32K |
| 场景 | 企业知识库、客服 |

## 2.2 字节跳动（豆包）
### 厂商信息
* 平台：火山引擎 
* 优势：
  * 中文强
  * 成本低
  * 工程化成熟

### 豆包模型
| 模型 | 定位 |
| --- | --- |
| doubao-pro | 通用 |
| doubao-thinking | 推理 |
| seedream | 图像 |
| seedance | 视频 |

### 单模型关键能力
* Doubao Thinking

| 维度 | 说明 |
| --- | --- |
| 特点 | 强推理 |
| 场景 | 数学、规划、Agent |

## 2.3 DeepSeek
### 厂商信息
* 归属地：中国
* 定位：低成本高性能
* 社区影响力：极高

### DeepSeek 模型
| 模型           | 特点 |
|--------------| --- |
| DeepSeek-V3  | 通用 |
| DeepSeek-R1  | 推理 |

### 单模型关键能力
* DeepSeek-R1

| 维度 | 说明 |
| --- | --- |
| 特点 | 推理接近 o1 |
| 成本 | 极低 |
| 场景 | 工具型推理 |

# 三、Vendor 维度
| 原始模型 | Vendor |
| --- | --- |
| GPT 系列 | OpenAI / Azure |
| Claude | Anthropic / 代理 / AWS |
| Gemini | Vertex AI |
| Qwen | 阿里云 |
| Doubao | 火山引擎 |
| DeepSeek | 官方 / 第三方 |