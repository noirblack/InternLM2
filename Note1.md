# 书生·浦语大模型全链路开源开放体系

视频链接: https://www.bilibili.com/video/BV1Vx421X72D/?spm_id_from=333.788&vd_source=2d819b0496a60786d3051e1efa611f6d

## 大模型 VS 小模型

专用模型：正对特定任务，一个模型解决一个问题

通用模型：一个模型应对多种任务、多种模态 (AGI关键路径)

## 书生·浦语大模型体系

**历史**：23.06.07 InternLM开源 ... 24.01.17 InternLM2开源

**模型**：2.0包括 7B和20B 两种参数量，分别有InternLM-Base(底座)，InternLM2（强化）,InternLM-Chat（对话）三个版本

**改进**： 训练数据优化，数据清洗、评价、多样性补全
            20万token超长上下文
            推理、数学、代码能力提升
            对话和创作能力
            工具调用能力，构建复杂智能体
            内生计算能力

## 模型到应用全工具链体系

- **数据集**：书生万卷 1.0 & CC，多模态，多任务

- **预训练**：支持大规模训练（8卡→千卡），兼容HuggingFace

- **微调**：XTuner 支持全参数微调、LoRA微调，最低8G显存可微调7B模型

- **部署**：LMDeploy提供模型轻量化和服务

- **评测**：OpenCompass 全方位评测，测评工具链，社区

- **应用**： Lagent, AgentLego 支持多种智能体、代码解析等工具调用

# InternLM2 技术报告笔记
链接：https://arxiv.org/pdf/2403.17297.pdf

介绍InternLM2的大型语言模型，该模型在主观和客观评估中表现出色。

InternLM2经过超过2T的高质量预训练语料训练，适用于不同规模的应用场景。

主要贡献了InternLM2模型，支持200k超长上下文，数据准备指导和 Conditional Online RLHF微调技术

**Infrastructure** 
1. InternEvo 轻量化的框架，用于模型Pre-training, SFT and RLHF

2. Model Structure: LLaMA基础上使用，Grouped-Query Attention (GQA)支持超长上下文

**Pre-train**
Text data, Code data, Long context Data

**Alignment**
1. Supervised Fine-Tuning: 10M instruction instances

2. Conditional Online Reinforcement Learning from Human Feedback (COOL RLHF) 解决偏好冲突和奖励“欺诈”的问题

3. Long context finetuning during SFT and RLHF

4. Tool-Augmented: General tool calling, code interpreter


