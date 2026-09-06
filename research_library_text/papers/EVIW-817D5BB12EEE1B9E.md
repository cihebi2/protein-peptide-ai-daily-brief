# Multimodal learning in clinical proteomics: enhancing antimicrobial resistance prediction models with chemical information

- **论文 ID：** `EVIW-817D5BB12EEE1B9E`
- **期刊 / 来源：** Bioinformatics
- **发表时间：** 2023 Nov 24
- **DOI：** [10.1093/bioinformatics/btad717](https://doi.org/10.1093/bioinformatics/btad717)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `论文声明资源` / `肽与抗菌肽`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者提出一个把 MALDI-TOF mass spectra 与 antimicrobial chemical fingerprints 联合建模的多模态框架，覆盖 drug recommendation 和 generalized resistance prediction 两类任务，并声称相较于 single-drug / single-species 方法取得了更好的性能与泛化能力。

## 创新边界

`新意主要在多模态联合建模、跨药物知识迁移和排序式推荐；没有新的 wet-lab 实验，也不是新分子生成方法。`。这不是全球首创性检索或独立复现结论。

## 研究问题

现有基于 clinical proteomics 的 AMR 预测通常把每个 antimicrobial 与 pathogen species 作为独立任务训练，难以利用 chemical knowledge transfer，也很难推广到未见药物或未见组合；作者试图用 MALDI-TOF spectra 加上药物化学信息来缓解这一问题。

## 方法

- 病原质谱profile与药物指纹/嵌入形成双视图，Siamese或残差MLP学习匹配和耐药分类，同时输出药物排序。

## 数据与基准

- 公开临床病原质谱-耐药结果数据；按物种、药物和OOD设置拆分，代码不产生新数据。

## 比较基线

- 单药/单物种模型、kNN/物种基线、Siamese、ResMLP及模态消融。

## 结果证据

- 多模态模型显著超过单药/单物种方法；OOD拆分性能明显下降，top-k邻居对未检测药物无法评估precision。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 分布外药物/物种仍困难；临床检测缺失导致评价不完整，预测推荐不是治疗效果。

## 仍未知

- 未核验 GitHub 仓库中的实际实现、许可证与可复现性细节。
- 未见论文对 DRIAMS 以外数据集的外部跨站点验证。
- drug recommendation 仅是排序与筛选现有 antimicrobial，并不生成新分子。
- 补充材料中的超参数与更多消融细节未在主文中完全展开。

## Pi 结构化证据摘录

- **baseline：** 作者将 multi-drug ResMLP 与 Weis 2022 中的 single-species single-drug LightGBM 和 MLP baselines 对比，并在多数指标上取得更好结果。
  - 证据：[doi:10.1093/bioinformatics/btad717, p.6]
- **baseline：** 推荐任务的无模型基线包括 random baseline、baseline species 与 spectrum similarity，它们主要依赖训练样本的邻近性和频率投票。
  - 证据：[doi:10.1093/bioinformatics/btad717, p.3]；[doi:10.1093/bioinformatics/btad717, p.5]
- **baseline：** AMR prediction 的学习基线还包括 PCA+LR 和 Siamese+LR，分别代表降维线性分类与联合嵌入后再分类。
  - 证据：[doi:10.1093/bioinformatics/btad717, p.4]；[doi:10.1093/bioinformatics/btad717, p.7]
- **data：** DRIAMS 数据集包含 303,195 个 mass spectra、768,300 个 AMR labels、803 个 pathogen species，覆盖 2016–2018 年四个 Swiss diagnostic labs。
  - 证据：[doi:10.1093/bioinformatics/btad717, p.2]；[doi:10.1093/bioinformatics/btad717, p.3]
- **data：** drug recommendation 只在 DRIAMS-B 上评估，训练集为 1907 个样本、测试集为 477 个样本，并要求测试集中每个 spectrum 至少对应一个 resistant 和一个 sensitive outcome。
  - 证据：[doi:10.1093/bioinformatics/btad717, p.3]
- **data：** 由于某些 treatment 是 compound mixtures，作者无法为其分配单一 fingerprint，因此将这类样本从分析中移除。
  - 证据：[doi:10.1093/bioinformatics/btad717, p.3]
- **declared_resources：** 论文声明代码已公开在 GitHub：https://github.com/BorgwardtLab/MultimodalAMR。
  - 证据：[doi:10.1093/bioinformatics/btad717, p.1]；[doi:10.1093/bioinformatics/btad717, p.9]
- **declared_resources：** 论文声明 DRIAMS 数据集可在 Dryad 获取，并给出 DOI 10.5061/dryad.bzkh1899q。
  - 证据：[doi:10.1093/bioinformatics/btad717, p.9]
- **declared_resources：** 作者同时说明本研究没有生成新的数据，结果完全建立在已有公开数据与分析流程之上。
  - 证据：[doi:10.1093/bioinformatics/btad717, p.9]
- **limitations：** top-k recommendation 只能在候选 drugs 出现在邻居集合时计算 precision，因此对未被覆盖的 drugs 存在评估盲区。
  - 证据：[doi:10.1093/bioinformatics/btad717, p.5]
- **limitations：** resistance recommendation 比 sensitivity 更难，且测试集中 resistant drugs 平均只有 3.2 个、sensitive drugs 平均 12.3 个，导致指标更易受类别不平衡影响。
  - 证据：[doi:10.1093/bioinformatics/btad717, p.5]
- **limitations：** drug zero-shot 的结果方差很大，作者将其归因于不同 held-out drug 的 class imbalance 与测试切分异质性，并且没有观察到 drug similarity 与性能之间的相关性。
  - 证据：[doi:10.1093/bioinformatics/btad717, p.7]
- **limitations：** 作者在讨论中明确指出，cross-site generalizability 仍然需要进一步评估，因此当前证据主要是 DRIAMS 内部的 retrospective benchmark。
  - 证据：[doi:10.1093/bioinformatics/btad717, p.8]
- **method：** 使用 DRIAMS 的 MALDI-TOF spectra 作为临床样本表示，并以 6000D binned mass spectra 向量作为输入特征。
  - 证据：[doi:10.1093/bioinformatics/btad717, p.2]；[doi:10.1093/bioinformatics/btad717, p.3]
- **method：** 对 antimicrobial drugs 提取 MACCS、PubChemFP 和 1024-bit Morgan fingerprints，借助 RDKit 与 PubChemPy 生成化学表征，混合药物样本被排除。
  - 证据：[doi:10.1093/bioinformatics/btad717, p.3]
- **method：** 在 drug recommendation 任务中比较 random baseline、baseline species、spectrum similarity、Siamese networks 与 ResMLP，并用 Precision、P@n 和 mAP@n 评估。
  - 证据：[doi:10.1093/bioinformatics/btad717, p.3]；[doi:10.1093/bioinformatics/btad717, p.5]
- **method：** 在 generalized AMR prediction 中比较 PCA+LR、Siamese+LR 与 ResMLP，并设计 random、species-drug zero-shot 和 drug zero-shot 三种 split，使用 AUPRC、balanced accuracy 和 MCC 评价，还用 SHAP 做特征解释。
  - 证据：[doi:10.1093/bioinformatics/btad717, p.4]；[doi:10.1093/bioinformatics/btad717, p.7]
- **results：** 模型无关的 recommendation 基线显示，top-k similar samples 的 precision 在 k 约 15–30 后趋于稳定，因此后续采用 k=30；random baseline 最弱，而 baseline species 与 spectrum similarity 表现接近。
  - 证据：[doi:10.1093/bioinformatics/btad717, p.5]
- **results：** 在 recommendation 任务里，sensitivity 的 precision 整体高于 resistance；当目标是 resistance 时，ResMLP 的 mAP@n 在 n≥2 时优于其他方法，说明化学特征有助于更稳定地识别 resistant drugs。
  - 证据：[doi:10.1093/bioinformatics/btad717, p.5]
- **results：** 与 Weis et al. 2022 的 12 个 drug–species pairings 比较时，ResMLP 的 AUROC 平均提升约 0.12、AUPRC 平均提升约 0.25，并且 Wilcoxon signed-rank test 在 Bonferroni 校正后仍显著。
  - 证据：[doi:10.1093/bioinformatics/btad717, p.6]
- **results：** 在 DRIAMS B 的 direct prediction 中，ResMLP 在 random split 上达到 AUPRC 0.87、balanced accuracy 0.90、MCC 0.79；在 species-drug zero-shot 与 drug zero-shot 场景中也优于 PCA+LR、Siamese+LR 和 Sp-ResMLP。
  - 证据：[doi:10.1093/bioinformatics/btad717, p.7]
- **results：** SHAP 分析表明 spectra 与 chemical fingerprints 都贡献了最终预测，且 beta-lactam ring、amine 或 alcohol groups 等特征与已知 resistance mechanisms 一致。
  - 证据：[doi:10.1093/bioinformatics/btad717, p.7]

## 页码证据

- [doi:10.1093/bioinformatics/btad717, p.1]
- [doi:10.1093/bioinformatics/btad717, p.4]
- [doi:10.1093/bioinformatics/btad717, p.5]
- [doi:10.1093/bioinformatics/btad717, p.7]
- [doi:10.1093/bioinformatics/btad717, p.9]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
