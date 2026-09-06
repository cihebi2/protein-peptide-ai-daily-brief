# VISH-Pred: an ensemble of fine-tuned ESM models for protein toxicity prediction

- **论文 ID：** `EVIW-A2E8C5BC0F97026E`
- **期刊 / 来源：** Brief Bioinform
- **发表时间：** 2024 Jun 6
- **DOI：** [10.1093/bib/bbae270](https://doi.org/10.1093/bib/bbae270)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `论文声明资源` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者提出 VISH-Pred：基于 ESM2 的微调模型、欠采样、LightGBM/XGBoost 特征分类器与集成平均的蛋白毒性预测框架，并声称在三个独立测试集上优于既有方法。

## 创新边界

`冻结证据只支持其为相对已引述工作的组合式方法创新；未见独立 prior-art 证据，不能据此确认全球首创。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在高度类别不平衡的蛋白/肽数据上，仅凭序列准确预测 toxic 与 non-toxic，以支持蛋白/肽治疗候选的安全筛选。

## 方法

- ESM embeddings/fine-tuning与ensemble。

## 数据与基准

- venom/toxin/non-toxin protein datasets。

## 比较基线

- 传统features/PLM。

## 结果证据

- 论文报告超过toxicity baselines；为计算。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- toxin标签/物种偏差、解释非因果。

## 仍未知

- 补充材料中的完整超参数表与部分图表未在主文中展开，无法逐项复核。
- 在线 web server 的当前可达性与版本冻结状态未在冻结页之外验证。
- docking 案例没有实验验证，不能据此判断真实抑制效应。

## Pi 结构化证据摘录

- **baseline：** 在小型独立测试集上，对照方法包括 CSM-Toxin、Toxify、ToxIBTL、ToxinPred2、ToxinPred3、ToxClassifier 等；VISH-Pred 在 F1 和 MCC 上被作者描述为相对最优提升，较次优方法有超过 10% 的改进。[doi:10.1093/bib/bbae270, p.8]
  - 证据：[doi:10.1093/bib/bbae270, p.8]
- **baseline：** 在大型 blind test set 上，ToxClassifier 取得最高 ACC/precision，ToxinPred2 取得最高 recall，但牺牲了另一侧指标，说明各基线在 precision-recall 之间存在明显权衡。[doi:10.1093/bib/bbae270, p.10]
  - 证据：[doi:10.1093/bib/bbae270, p.10]
- **baseline：** 在 bacterial test set 上，多数既有方法的 MCC 很低，作者指出 ToxinPred3(ET) 偏高 recall、ToxITBL 偏高 precision，而 VISH-Pred 在 F1、AUC、ACC、MCC 上整体更稳健。[doi:10.1093/bib/bbae270, p.11]
  - 证据：[doi:10.1093/bib/bbae270, p.11]
- **data：** 经 curation 后，主数据集规模为 2015 个 toxic 与 182,561 个 non-toxic 样本，并按 80%/20% 划分训练集与验证集。[doi:10.1093/bib/bbae270, p.4]
  - 证据：[doi:10.1093/bib/bbae270, p.4]
- **data：** 作者报告的小型独立测试集包含 202 个 toxic 与 2160 个 non-toxic 蛋白，且已去除长度大于 1024 aa 的条目。[doi:10.1093/bib/bbae270, p.4]
  - 证据：[doi:10.1093/bib/bbae270, p.4]
- **data：** 作者报告的大型 blind test set 包含 222 个 positive 与 20,329 个 negative 样本，类不平衡约为 1:91。[doi:10.1093/bib/bbae270, p.4]
  - 证据：[doi:10.1093/bib/bbae270, p.4]
- **data：** 独立 bacterial dataset 来自 DBAASP，共 2170 条肽，分为 1071 条 non-toxic 与 1099 条 toxic，长度约 4–119 aa，且与训练集序列相似性较低。[doi:10.1093/bib/bbae270, p.4]
  - 证据：[doi:10.1093/bib/bbae270, p.4]
- **declared_resources：** 训练与基准数据来源于 UniProt release 2022_04；作者还给出 CSM-Toxin 的数据处理 Bitbucket 路径，并公开了 VISH-Pred web server 供在线测试。[doi:10.1093/bib/bbae270, p.3][doi:10.1093/bib/bbae270, p.12]
  - 证据：[doi:10.1093/bib/bbae270, p.3]；[doi:10.1093/bib/bbae270, p.12]
- **declared_resources：** 实现依赖 HuggingFace 上的 ESM2、Python 版 xgboost 1.7.6 与 lightgbm 4.0.0，并在单卡 Nvidia RTX A6000 48GB 上完成微调。[doi:10.1093/bib/bbae270, p.5][doi:10.1093/bib/bbae270, p.6]
  - 证据：[doi:10.1093/bib/bbae270, p.5]；[doi:10.1093/bib/bbae270, p.6]
- **declared_resources：** 对接案例使用 AlphaFold 结构、ChEMBL 约 1000 个抗菌相关化合物以及 Schrödinger Glide/OPLS 体系；作者还提供了可下载示例 bacterial proteins 供网页推理。[doi:10.1093/bib/bbae270, p.7][doi:10.1093/bib/bbae270, p.10]
  - 证据：[doi:10.1093/bib/bbae270, p.7]；[doi:10.1093/bib/bbae270, p.10]
- **limitations：** 作者明确将 ESM2 的适用序列长度限制在 1024 aa 以内，因此所有更长蛋白都被剔除，方法覆盖范围受限。[doi:10.1093/bib/bbae270, p.4]
  - 证据：[doi:10.1093/bib/bbae270, p.4]
- **limitations：** 文中的 docking 案例只能说明可能结合，作者也承认真正的 antidote 还需要选择性、药代、安全性、剂量和临床验证，不能把对接结果直接等同为治疗结论。[doi:10.1093/bib/bbae270, p.10]
  - 证据：[doi:10.1093/bib/bbae270, p.10]
- **limitations：** 作者指出 bacterial test set 的短肽长度分布与训练集差异较大、序列相似性也较低，这导致所有方法在该集合上的性能明显下降。[doi:10.1093/bib/bbae270, p.9][doi:10.1093/bib/bbae270, p.11]
  - 证据：[doi:10.1093/bib/bbae270, p.9]；[doi:10.1093/bib/bbae270, p.11]
- **method：** 作者从 UniProt release 2022_04 采集已审校蛋白，将带有 keyword:KW-0800 的条目标为毒性正样本、无 KW-0800 且无 KW-0200 的条目标为非毒性负样本，并用 CD-HIT 0.7 去冗余；随后为适配 ESM2 又删除了长度大于 1024 aa 的序列。[doi:10.1093/bib/bbae270, p.3][doi:10.1093/bib/bbae270, p.4]
  - 证据：[doi:10.1093/bib/bbae270, p.3]；[doi:10.1093/bib/bbae270, p.4]
- **method：** 作者把剩余负样本随机分成 10 份，固定正样本不变，构造 10 个约 1:9 的欠采样子集分别训练 10 个 ESM2 模型，以缓解原始约 1:91 的极端类别不平衡。[doi:10.1093/bib/bbae270, p.4]
  - 证据：[doi:10.1093/bib/bbae270, p.4]
- **method：** ESM2 微调采用带分类头的端到端训练、weighted binary cross-entropy、Adam、学习率 1e-4、weight decay 0.01、最多 10 个 epoch、batch size 4、gradient accumulation 4，并以验证集 MCC 早停。[doi:10.1093/bib/bbae270, p.5]
  - 证据：[doi:10.1093/bib/bbae270, p.5]
- **method：** 作者把最佳微调 ESM2 的最后层 embedding 作为特征，分别训练 LightGBM 与 XGBoost，再将最佳 ESM2、LightGBM、XGBoost 的预测分数取平均作为最终 VISH-Pred 输出。[doi:10.1093/bib/bbae270, p.6][doi:10.1093/bib/bbae270, p.7]
  - 证据：[doi:10.1093/bib/bbae270, p.6]；[doi:10.1093/bib/bbae270, p.7]
- **results：** 在小型独立测试集上，VISH-Pred 取得 F1=0.759、ACC=0.956、MCC=0.737、AUC=0.891，作者将其描述为总体最佳或并列最佳表现。[doi:10.1093/bib/bbae270, p.8]
  - 证据：[doi:10.1093/bib/bbae270, p.8]
- **results：** 在大型 blind test set 上，VISH-Pred 报告 AUC=0.964、ACC=0.991、MCC=0.716、F1=0.696，作者强调其在不平衡条件下仍保持最优或近最优综合表现。[doi:10.1093/bib/bbae270, p.10]
  - 证据：[doi:10.1093/bib/bbae270, p.10]
- **results：** 在 bacterial test set 上，VISH-Pred 报告 F1=0.713、AUC=0.644、ACC=0.647、MCC=0.322，明显优于其他基线在综合指标上的表现。[doi:10.1093/bib/bbae270, p.11]
  - 证据：[doi:10.1093/bib/bbae270, p.11]
- **results：** 作者还报告随着 ESM2 模型规模增大，验证集指标整体提升，但训练耗时也显著增加，体现出模型大小与成本之间的权衡。[doi:10.1093/bib/bbae270, p.7]
  - 证据：[doi:10.1093/bib/bbae270, p.7]

## 页码证据

- [doi:10.1093/bib/bbae270, p.1]
- [doi:10.1093/bib/bbae270, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
