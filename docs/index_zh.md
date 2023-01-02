# LHS智能医学系统实用指南
陈安均博士，[LHS技术论坛项目](https://www.learninghealth.org/2020-lhs-technology-forum) 联合主席，国际LHS社区（非营利）


[本指南持续更新, [英文版](index.md)]

## 目录

1. [LHS智能医学系统的愿景](#1-the-vision-of-learning-health-systems)
2. [医学证据和知识的生成](#2-evidence-and-knowledge-generation)
3. [医学知识和模型的传播](#3-knowledge-and-model-dissemination)
4. [构建LHS智能医学系统](#4-building-lhs)
5. [机器学习赋能的模拟LHS](#5-ml-enabled-lhs-simulation)
6. [机器学习赋能的LHS项目实例](#6-ml-enabled-lhs-project-examples)
7. [医疗健康数据](#7-health-data)
8. [合成患者病历数据](#8-synthetic-patient-data)
9. [数据驱动的机器学习方法](#9-data-centric-ml)
10. [更多LHS项目实例](#10-more-lhs-project-examples)
11. [相关资源](#11-related-resources)
12. [参考资料](#12-references)


# 概述

《LHS智能医学系统实用指南》专注于为软件开发人员和医疗健康机构临床团队提供技术实用信息，帮助您快速启动对未来Learning Health System (LHS)智能医学系统的研发和应用。

指南内容基于我对美国医学科学院 (US National Academy of Medicine, NAM) 发表的LHS 系列报告的理解和解读，以及 LHS 这一新领域迄今为止取得的进展。NAM提出的LHS愿景和制定的LHS顶层框架不仅将引导美国整个医疗健康系统向智能医学循环学习和传播系统转型，而且会影响全球各国医疗健康系统的更新。

本指南首先总结了 NAM LHS 系列报告，以期回答 LHS 基本问题：我们为什么需要 LHS？什么是 LHS？谁在搭建 LHS？ 

然后指南简要描述了应用机器学习 (machine learning, ML) 构建 LHS 小型单元的最新技术发展。亮点是首次使用合成患者数据模拟的机器学习赋能的 LHS (即 ML-LHS)，所用数据可在 GitHub 上的“[开放合成患者数据](https://github.com/lhs-open/synthetic-data)” (Open Synthetic Patient Data)项目获取。出于示范目的，指南分享了来自不同医院或医疗系统的LHS项目实例，这些项目正在为疾病风险预测和精准医疗等不同临床任务构建真实患者的ML-LHS 单元。为加速LHS发展，我提出了一个“合成+真实”数据的新策略，有助于更有效地构建 ML-LHS 单元。

随后的章节提供了有关ML-LHS 不可或缺的电子病历数据 (electronic medical record, EMR 或 electronic health record, EHR)、合成患者数据、数据驱动的机器学习以及其他技术组件的更多详细信息。 

指南主要目标： 
>1.	为软件开发者和医疗健康机构临床团队提供实用技术信息，帮助快速了解LHS的优点并开始研发LHS。
>2.	解释为什么构建小型 ML-LHS 单元更切实可行，而不应被另一种大而全的LHS构想所束缚。 
>3.	提出“合成+真实”新策略：首先利用合成患者数据模拟ML-LHS单元，然后应用模拟流程帮助构建真实病历数据的ML-LHS单元。 

指南还对 ML-LHS 提出以下假设： 
>1.	ML-LHS性能假设：因其内在的以数据为核心的机器学习方法，ML-LHS 最终可以为大多数疾病和健康状况实现高性能的预测 (>95%) 。 
>2.	ML-LHS平等假设：由大医院主导的临床研究网络 ML-LHS 可以有效地用机器学习模型为小型医疗机构赋能，从而减小在医疗服务不足人群中的医疗服务差异 (health care disparities)。 
>3.	ML-LHS AI假设：因为LHS具有数据驱动和部署导向的特征，大部分基于电子病历数据的AI将以LHS形式更有效地实现和传播。

[LHS 实用指南](https://github.com/lhs-open/lhs-guide)是 GitHub 上开放 LHS 项目（Open LHS）的一部分，旨在智能医学系统新兴领域，促进全球范围的研究、开发和实施等方面的分享和协作。作为 LHS 的动态技术文档，本指南发布在 GitHub平台，将在LHS新信息出现时进行更新，及时为LHS社区提供最新进展。

#### 下一步：

>   在阅读本快速实用指南后，如果您想尝试病历机器学习或 ML-LHS 研究，可先在GitHub上的开放合成数据项目查看已有数据 (https://github.com/lhs-open/synthetic-data)。如果您需要新的合成数据，可联系我 (ajchen at web2express.org) 讨论如何产生新数据。合成数据有望加速您的项目进程，开源Synthea技术能够模拟任何疾病或健康状况，因此可能是产生您所需的合成数据的起点。 

【LHS名称翻译】

LHS作为新的专业技术术语，本指南采用美国医学科学院发表的 LHS系列报告中的定义。因为中文直译不能反映LHS的核心含义，我给出有助于理解的意译。
>-   英文全称：Learning Health System。缩写： LHS。
>-   中文全称：智能医学循环学习和传播系统。简称：LHS智能医学系统。

<br>

---