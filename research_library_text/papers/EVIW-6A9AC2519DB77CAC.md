# Benchmarking protein language models for protein crystallization

- **论文 ID：** `EVIW-6A9AC2519DB77CAC`
- **期刊 / 来源：** Scientific Reports（DOI 前缀识别）
- **发表时间：** 未记录
- **DOI：** [10.1038/s41598-025-86519-5](https://doi.org/10.1038/s41598-025-86519-5)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `论文声明资源` / `语言模型` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

论文声称通过 TRILL 平台系统 benchmark 多种 open PLM 的平均 embedding + 传统分类器，用于 protein crystallization propensity prediction，并进一步用 fine-tuned ProtGPT2 生成、筛选出 5 个潜在可结晶的新蛋白序列。[doi:10.1038/s41598-025-86519-5, p.1]

## 创新边界

`新意主要在于“PLM embedding + downstream classifier”的跨模型系统比较，以及一个纯计算的生成后处理流程；它没有提出新的 PLM 架构，也没有做湿实验验证。`。这不是全球首创性检索或独立复现结论。

## 研究问题

作者要解决的是：仅凭蛋白序列，能否准确预测 protein crystallization propensity，并判断 open protein language models (PLMs) 是否能在这一 property prediction 任务上优于既有 sequence-based 方法。[doi:10.1038/s41598-025-86519-5, p.1]

## 方法

- embeddings+classifiers/finetuning。

## 数据与基准

- crystallized/noncrystallized proteins。

## 比较基线

- traditional crystallization predictors。

## 结果证据

- 论文报告模型差异；为计算。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 实验条件/发表偏差/label噪声。

## 仍未知

- 5 个候选蛋白是否在后续工作中获得实验确认，冻结页无法得知。
- Supplementary material 中的部分超参数与训练曲线未在当前页完整展开。
- 仅凭冻结页不能独立核验 GitHub 仓库是否包含完整可复现实验环境与许可证细节。

## Pi 结构化证据摘录

- **baseline：** 主要比较对象包括 fDETECT、DeepCrystal、ATTCrys 和 CLPred；作者还系统比较了 XGBoost、LightGBM、MLP，以及 CNN/LSTM 版本之间的差异。[doi:10.1038/s41598-025-86519-5, p.2]
  - 证据：[doi:10.1038/s41598-025-86519-5, p.2]；[doi:10.1038/s41598-025-86519-5, p.7]；[doi:10.1038/s41598-025-86519-5, p.8]；[doi:10.1038/s41598-025-86519-5, p.10]
- **baseline：** 作者明确说明，GCmapCrys、BCrystal 等依赖 MSA/额外特征且较慢的方法不适合作为这项高通量、sequence-only benchmark 的公平主对照。[doi:10.1038/s41598-025-86519-5, p.2]
  - 证据：[doi:10.1038/s41598-025-86519-5, p.2]
- **data：** 主数据来自 processed PepcDB：初始共有 28,731 条序列，经 25% identity filter 与 Lmax=800 过滤后剩 25,120 条；按既有 protocol 划分后，D2 为 1,787 条平衡测试集（891 positive / 896 negative）。[doi:10.1038/s41598-025-86519-5, p.4]
  - 证据：[doi:10.1038/s41598-025-86519-5, p.4]
- **data：** 作者还使用 SwissProt 导出的 SP_final（237 条蛋白）与 TrEMBL 导出的 TR_final（1,012 条蛋白）作为两个独立外部测试集，用来检验泛化能力。[doi:10.1038/s41598-025-86519-5, p.4]
  - 证据：[doi:10.1038/s41598-025-86519-5, p.4]
- **declared_resources：** 数据与外部基准资源包括 PepcDB、SwissProt、TrEMBL、UniRef100，推理/组织框架使用 TRILL。[doi:10.1038/s41598-025-86519-5, p.3]
  - 证据：[doi:10.1038/s41598-025-86519-5, p.3]；[doi:10.1038/s41598-025-86519-5, p.4]；[doi:10.1038/s41598-025-86519-5, p.15]
- **declared_resources：** 机器学习与结构评估工具链包括 XGBoost、LightGBM、scikit-learn 1.5.1、Python 3.10.0、CD-HIT/CD-HIT-2D、PSIPRED 4.02、UMAP、AlphaFold2、RoseTTAFold2、GalaxyRefine、ModFold、ProFitFun、ProCheck、Errat 和 MolProbity。[doi:10.1038/s41598-025-86519-5, p.5]
  - 证据：[doi:10.1038/s41598-025-86519-5, p.5]；[doi:10.1038/s41598-025-86519-5, p.6]；[doi:10.1038/s41598-025-86519-5, p.7]；[doi:10.1038/s41598-025-86519-5, p.12]；[doi:10.1038/s41598-025-86519-5, p.13]
- **declared_resources：** 作者在文末给出代码仓库 https://github.com/raghvendra5688/crystallization_benchmark，明确表示分析代码可获得。[doi:10.1038/s41598-025-86519-5, p.15]
  - 证据：[doi:10.1038/s41598-025-86519-5, p.15]
- **limitations：** 作者承认受 NVIDIA RTX A6000 48GB 显存限制，无法对超大 PLM 做端到端 fine-tuning，因此主线只能采用 zero-shot embeddings 加传统分类器。[doi:10.1038/s41598-025-86519-5, p.3]
  - 证据：[doi:10.1038/s41598-025-86519-5, p.3]；[doi:10.1038/s41598-025-86519-5, p.5]
- **limitations：** 文中没有给出这 5 个生成候选蛋白的湿实验验证；作者仅在结尾建议进一步 experimental validation。[doi:10.1038/s41598-025-86519-5, p.15]
  - 证据：[doi:10.1038/s41598-025-86519-5, p.15]
- **method：** 作者将蛋白结晶可成晶性建模为二分类任务：先用 TRILL 为多种 PLM 提取蛋白平均 embedding，再在这些表示上训练 XGBoost、LightGBM 和部分 MLP 分类器；对 top-performing PLM 还额外叠加 CNN/LSTM 进行序列级建模。[doi:10.1038/s41598-025-86519-5, p.3]
  - 证据：[doi:10.1038/s41598-025-86519-5, p.3]；[doi:10.1038/s41598-025-86519-5, p.5]；[doi:10.1038/s41598-025-86519-5, p.6]
- **method：** 生成部分先用 crystallizable class 微调 ProtGPT2 10 个 epoch，再生成 3000 条序列，并依次通过 CD-HIT-2D、CD-HIT、secondary structure compatibility、aggregation screening、UniRef100 homology search，以及 AlphaFold2 / RoseTTAFold2 / GalaxyRefine / ModFold / ProFitFun / ProCheck / Errat / MolProbity 等步骤筛选。[doi:10.1038/s41598-025-86519-5, p.6]
  - 证据：[doi:10.1038/s41598-025-86519-5, p.6]；[doi:10.1038/s41598-025-86519-5, p.7]；[doi:10.1038/s41598-025-86519-5, p.12]；[doi:10.1038/s41598-025-86519-5, p.13]
- **results：** 在平衡测试集上，ESM2 T30-150M + LightGBM 取得最佳 ACC/F1/MCC（0.857/0.854/0.715），而 ESM2 T30-150M + XGBoost 取得最佳 AUPR/AUC（0.929/0.936）；文中也指出它们优于 DeepCrystal、ATTCrys 和 CLPred。[doi:10.1038/s41598-025-86519-5, p.8]
  - 证据：[doi:10.1038/s41598-025-86519-5, p.8]；[doi:10.1038/s41598-025-86519-5, p.9]
- **results：** 在 SP_final 上，ESM2 T36-3B + LightGBM 在 ACC/F1/MCC 上最好，ProstT5 + LightGBM 在 AUPR/AUC 上最好；作者同时报告大模型普遍优于传统 sequence-based baselines。[doi:10.1038/s41598-025-86519-5, p.10]
  - 证据：[doi:10.1038/s41598-025-86519-5, p.10]
- **results：** 在 TR_final 上，ESM2 T30-150M + LightGBM 取得最佳 ACC/F1/MCC，整体 PLM-based classifiers 也优于 DeepCrystal、ATTCrys 和 CLPred。[doi:10.1038/s41598-025-86519-5, p.11]
  - 证据：[doi:10.1038/s41598-025-86519-5, p.11]
- **results：** 生成流程最终保留 5 个候选蛋白；作者给出的结构质量表明这些模型在 stereochemical quality 上较可靠，但它们仍只是 computational candidates，而非实验确认结果。[doi:10.1038/s41598-025-86519-5, p.12]
  - 证据：[doi:10.1038/s41598-025-86519-5, p.12]；[doi:10.1038/s41598-025-86519-5, p.13]；[doi:10.1038/s41598-025-86519-5, p.14]

## 页码证据

- [doi:10.1038/s41598-025-86519-5, p.1]
- [doi:10.1038/s41598-025-86519-5, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
