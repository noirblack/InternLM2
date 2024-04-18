# 视频链接 # 
https://www.bilibili.com/video/BV1QA4m1F7t4/
# 教程文档 #
https://github.com/InternLM/Tutorial/blob/camp2/huixiangdou/readme.md


## RAG
RAG（Retrieval Augmented Generation）技术，通过检索与用户输入相关的信息片段，并结合外部知识库来生成更准确、更丰富的回答。解决 LLMs 在处理知识密集型任务时可能遇到的挑战, 如幻觉、知识过时和缺乏透明、可追溯的推理过程等。提供更准确的回答、降低推理成本、实现外部记忆。
RAG 能够让基础模型实现非参数知识更新，无需训练就可以掌握新领域的知识。茴香豆应用了RAG 技术，可以快速、高效的搭建自己的知识领域助手。

**RAG概述**
![image](https://github.com/noirblack/InternLM2/assets/9305115/e730c526-50ee-465f-8dac-e5c59dc3e6e6)

**RA原理**
三个主要部分： index 索引， retrieval 检索， generation 生成
![image](https://github.com/noirblack/InternLM2/assets/9305115/ced58c28-07a1-4eb2-99d0-63e8790ab57b)

**向量数据库**
![image](https://github.com/noirblack/InternLM2/assets/9305115/c07df8c7-b78a-43d1-ba51-277cdae6591e)

**RAG工作流程**
![image](https://github.com/noirblack/InternLM2/assets/9305115/adb9fc94-3d60-48c3-8d70-a598e682a64d)

**RAG发展历史**
2020年第一次提出，演化成3种形式：
- Naive RAG: 问答系统，信息检索
- Advanced RAG: 摘要生成，内容推荐
- Modular RAG: 多模态任务，对话系统
![image](https://github.com/noirblack/InternLM2/assets/9305115/3463f55d-e2a1-48e6-8afc-84ae31f4257f)

**RAG常见优化方法**
嵌入，索引，查询，上下文管理，迭代检索，递归检索，自适应检索，LLM微调
![image](https://github.com/noirblack/InternLM2/assets/9305115/cd606cb8-d06a-4908-9332-00c9754f9fa2)

**RAG VS Finetune**
![image](https://github.com/noirblack/InternLM2/assets/9305115/e384b93e-dcf6-42c5-b4e9-84f6131f7838)

**LLM常用优化方法比较**
![image](https://github.com/noirblack/InternLM2/assets/9305115/256a3cff-923b-43bb-afb3-412090db86d0)

**RAG技术评价指标**
![image](https://github.com/noirblack/InternLM2/assets/9305115/04e15852-2b05-44db-8349-03b796445a53)

**RAG总结**
![image](https://github.com/noirblack/InternLM2/assets/9305115/c677d108-e0f8-4ef1-b016-a33ccb6ee417)

## 茴香豆（豆哥）介绍
![image](https://github.com/noirblack/InternLM2/assets/9305115/72818009-6bb0-46c5-9a7b-55a80c11ff39)

**豆哥特点**
![image](https://github.com/noirblack/InternLM2/assets/9305115/2c5ef787-2c6a-4201-a491-9efa69307e7a)

**豆哥构成**
4个部分：知识库，前端（用户输入），LLM后端，茴香豆组合
![Uploading image.png…]()

# 笔记
茴香豆技术报告：https://arxiv.org/abs/2401.08772
本文主要介绍了一种名为"HuixiangDou"的技术助手，它是一个泛学术类文献阅读助手。文章首先介绍了该助手的三个部分：预处理、拒绝和回应，并详细描述了它们的功能。
接着，文章讨论了助手对于不同类型问题的回答能力，并提供了一些示例。然后，文章介绍了助手的一些技术实现和验证，包括LLM的Fine-tuning过程、拒绝流程的效果、评分方法的实施和测试、长上下文回应的必要实验以及搜索能力的增强尝试。
最后，文章提出了一些助手的局限性和未来的改进方向。

### 群聊的技术助手特点：
- True help-seekers： 只回答技术相关问题，不闲聊
- Strictly no hallucination： 真实可靠，不能有幻觉
- Understand domain-specific knowledge：知道领域知识，并且可以以相对地成本的方式更新知识库
- No rush for response：不需要太及时的相应 # 个人对这点存疑

## 主要方法
这篇论文介绍的主要实现方法包括以下几个方面：

1. **预处理用户输入**：将多个连续的消息整合为一个单一消息，同时使用OCR服务解析图像，并忽略其他元素如视频、表情符号和语音消息。

2. **拒绝管道**：基于LLM评分和text2vec模型来判断是否回应用户的问题。这样做的目的是避免模型产生虚幻的回应。

3. **响应管道**：利用LLM的NLP部分词分割任务优势来从查询中提取关键字和短语。首先从多个搜索结果中提取数据（根据模型支持的最大token长度），然后使用LLM评分过滤与问题相关的结果。最后将这些结果打包成背景文档。

4. **特征和重排**：通过混合使用LangChain和BCEmbedding来检索特定领域的知识。为了节省成本，论文中提到了一种混合调度不同LLM的方法。此外，论文还建立了一套安全机制，以确保对话组回复不涉及敏感主题。

5. **安全**：通过LLM评分检查所有字符串变量及其与禁止主题的关联，以避免生成非法内容。同时，设置助手的工作时间，以确保所有活动都在人类监督下进行。

这些方法共同构成了一个全面的技术助手解决方案，可以在群聊场景中有效地帮助用户解答问题。

![image](https://github.com/noirblack/InternLM2/assets/9305115/653100ed-6e1b-4bd2-88cd-cee22ca5ce18)
![image](https://github.com/noirblack/InternLM2/assets/9305115/1ab76521-dd05-4387-beb9-4267c6887ed5)

