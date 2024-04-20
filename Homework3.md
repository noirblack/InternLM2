## 基础作业

### 茴香豆 Web 端测试
![image](https://github.com/noirblack/InternLM2/assets/9305115/a20e0e04-7519-48ba-806f-6f20c05a483a)
![image](https://github.com/noirblack/InternLM2/assets/9305115/8776e1fd-1a0f-403a-83f3-a8194cdc1d20)
![image](https://github.com/noirblack/InternLM2/assets/9305115/0cf957f1-f2df-48ec-99a3-d1ff832c7f0e)
![image](https://github.com/noirblack/InternLM2/assets/9305115/76748da1-84ed-4506-92f9-c1c8c5f58b0a)
![image](https://github.com/noirblack/InternLM2/assets/9305115/2f8ae1c9-f6aa-41cc-a5be-3f00dbd29eb0)



### 2.在 `InternLM Studio` 上部署茴香豆技术助手

教程文档：https://github.com/InternLM/Tutorial/blob/camp2/huixiangdou/readme.md

根据教程文档，在InternLM Studio上部署茴香豆。

遇到以下问题：
1. 向量化知识库语料，代码报错，超出长度限制
![img_v3_02a3_44312a35-e98d-43ff-b680-7508f97f6c1g](https://github.com/noirblack/InternLM2/assets/9305115/2c168267-f476-4cd0-94ba-963c7caa2ced)
删除 assert 语句后，正常。
2. 茴香豆提问，发现相同语义的问题，得到答案差异很大
queries = ["茴香豆怎么部署到微信群？", "How to deploy huixiangdou in Wechat group?", "茴香豆怎样部署到微信群"]
- 茴香豆怎么部署到微信群？   -- 带有？结尾的问题，被判定为无关。应该是LLM对输入查询进行分类判断时候出错。
  ![img_v3_02a4_3317b24f-9a99-407c-94d1-ac4e96b846dg](https://github.com/noirblack/InternLM2/assets/9305115/2cc22076-eb64-4e59-bee6-7e52019e2106)
- "How to deploy huixiangdou in Wechat group?"  英文查询，给出更像答案格式化回答
![image](https://github.com/noirblack/InternLM2/assets/9305115/460276b2-26c8-462c-aa39-545a34ef4b13)
-"茴香豆怎样部署到微信群" 中文提问，没有问号，得到回答又不一样
![image](https://github.com/noirblack/InternLM2/assets/9305115/859e133f-c288-4c82-a42c-8bf39bd0a448)

### 利用 Gradio 搭建网页 Demo
![image](https://github.com/noirblack/InternLM2/assets/9305115/1afce773-f113-4580-826f-3ec1fdaa51d0)
![image](https://github.com/noirblack/InternLM2/assets/9305115/674cf6de-8dd4-4ec9-9645-5ec766455fec)
![image](https://github.com/noirblack/InternLM2/assets/9305115/2b2a9fc9-a169-4822-b57e-6a167aa1c8e7)




