# Bioactivity Deep Learning for Complex Structure-Free Compound-Protein Interaction Prediction

- **论文 ID：** `EVIW-819EC6B4DDEB7DFB`
- **期刊 / 来源：** J Chem Inf Model
- **发表时间：** 2025 Sep 16
- **DOI：** [10.1021/acs.jcim.5c00741](https://doi.org/10.1021/acs.jcim.5c00741)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `语言模型` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者声称提出了 CPI2M 大规模 benchmark 数据集与 GGAP-CPI 模型：前者提供多类型 bioactivity 与 AC 标注，后者通过整合 bioactivity learning、pretrained 表征和 cross-attention 提升结构自由 CPI 预测与虚拟筛选表现。

## 创新边界

`主要是结构自由 CPI 生物活性预测与虚拟筛选评分，属于支持设计的 transfer 类方法，而非直接生成或优化候选分子。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在缺乏蛋白-配体复合物晶体结构时，如何利用大规模且异质的 bioactivity 数据进行 compound-protein interaction 预测，并缓解 activity cliff 与 assay heterogeneity 对泛化性能和虚拟筛选排序能力的影响。

## 方法

- protein LM/sequence与compound graph/SMILES融合回归。

## 数据与基准

- ChEMBL/PDBBind类bioactivity。

## 比较基线

- DeepDTA/GraphDTA/structure models。

## 结果证据

- 论文报告超过baselines；为计算。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- assay异质、随机split/无实验。

## 仍未知

- GitHub 源码仓库是否与论文描述完全一致未在本任务中核验。
- 外部 benchmark 的 soft overlap 与不同 similarity cutoff 可能影响虚拟筛选比较。
- AC 标注并非逐对精确标注，细粒度 activity cliff 结构仍有不确定性。

## Pi 结构化证据摘录

- **baseline：** 作者对比了 SVM、RF、GBM、KNN、MLP、GCN、GAT、MPNN、AFP、KANO、CNN、Transformer，以及 ECFP-ESM-RF/GBM、DeepDTA、GraphDTA、HyperAttentionDTI、PerceiverCPI、KANO-ESM 等基线。
  - 证据：[doi:10.1021/acs.jcim.5c00741, p.13]；[doi:10.1021/acs.jcim.5c00741, p.14]
- **baseline：** 文中明确指出，DeepDTA、GraphDTA、HyperAttentionDTI 和 PerceiverCPI 等既有 CPI 深度模型在内部验证中未能超过简单的 ECFP-ESM-RF。
  - 证据：[doi:10.1021/acs.jcim.5c00741, p.6]
- **baseline：** 虚拟筛选部分还对比了 AutoDock Vina、CarsiDock、RTMScore、BIND、Komet、ConPLex 等既有 scoring functions。
  - 证据：[doi:10.1021/acs.jcim.5c00741, p.8]；[doi:10.1021/acs.jcim.5c00741, p.9]
- **data：** CPI2M 的源数据来自 EquiVS 与 Papyrus，而这两者又汇总了 ChEMBL、BindingDB、PubChem、Probe&Drugs、IUPHAR/BPS、ExCAPE 和 literature datasets。
  - 证据：[doi:10.1021/acs.jcim.5c00741, p.11]
- **data：** 数据清洗包含单位与 activity type 筛选、冲突值过滤、UniProt 映射、Papyrus relation/std 过滤，以及 MolVS/RDKit 标准化和 AlphaFold2 蛋白结构生成。
  - 证据：[doi:10.1021/acs.jcim.5c00741, p.11]；[doi:10.1021/acs.jcim.5c00741, p.12]
- **data：** AC 标注以三种相似度度量为基础：all-atom fingerprint、scaffold fingerprint 和 SMILES Levenshtein；任一相似度大于 0.9 且 bioactivity 差值大于 2 log units 时标记为 AC。
  - 证据：[doi:10.1021/acs.jcim.5c00741, p.12]
- **data：** 数据拆分采用按 target 的 AC-specific spectral clustering + 80/20 stratified split；表 1 还显示 CPI2M-main 覆盖大规模训练/验证集，而 assay 少于 200 的靶点被划入 CPI2M-few。
  - 证据：[doi:10.1021/acs.jcim.5c00741, p.4]；[doi:10.1021/acs.jcim.5c00741, p.5]；[doi:10.1021/acs.jcim.5c00741, p.12]
- **declared_resources：** 公开资源包括 CPI2M processed data（Zenodo 15789422）和 GGAP-CPI / CPI2M processing code（GitHub）。
  - 证据：[doi:10.1021/acs.jcim.5c00741, p.14]
- **declared_resources：** 论文声明其外部 benchmark 来自 MoleculeACE、CASF-2016、MerckFEP、DUD-E、DEKOIS-v2 与 LIT-PCBA。
  - 证据：[doi:10.1021/acs.jcim.5c00741, p.14]
- **declared_resources：** 模型与流程依赖的外部资源还包括 KANO、ESM-2、AlphaFold2、MolVS、RDKit 与 Graphein 等现成工具或预训练表示。
  - 证据：[doi:10.1021/acs.jcim.5c00741, p.11]；[doi:10.1021/acs.jcim.5c00741, p.12]；[doi:10.1021/acs.jcim.5c00741, p.13]
- **limitations：** 作者承认其 AC 标注流程主要识别 potential ACs，而非精确的 pairwise AC annotations，因此可能低估 AC 的细粒度影响。
  - 证据：[doi:10.1021/acs.jcim.5c00741, p.10]；[doi:10.1021/acs.jcim.5c00741, p.11]
- **limitations：** Kd 子集样本规模和多样性较小，作者认为这会扭曲部分性能估计并使结果波动更大。
  - 证据：[doi:10.1021/acs.jcim.5c00741, p.6]
- **limitations：** 虚拟筛选比较仍可能受到 soft overlap、相似性阈值和不同评测流程差异的影响，因此作者只主张 comparability，而非绝对优越。
  - 证据：[doi:10.1021/acs.jcim.5c00741, p.9]
- **limitations：** 作者还提出未来需要补充 pairwise AC annotations，并进一步改进 architecture 与 training strategy，以更直接处理 activity cliff 问题。
  - 证据：[doi:10.1021/acs.jcim.5c00741, p.10]
- **method：** 作者以 EquiVS 和 Papyrus 为主源，构建了带 AC 标注的 CPI2M，并将 Ki、Kd、EC50、IC50 作为核心活动类型用于统一建模与评估。
  - 证据：[doi:10.1021/acs.jcim.5c00741, p.1]；[doi:10.1021/acs.jcim.5c00741, p.11]；[doi:10.1021/acs.jcim.5c00741, p.12]
- **method：** GGAP-CPI 由 pretrained ligand encoder KANO、protein encoder（ESM-2 residue embedding + protein GCN）、multihead cross-attention pooling 和 feed-forward decoder 组成。
  - 证据：[doi:10.1021/acs.jcim.5c00741, p.1]；[doi:10.1021/acs.jcim.5c00741, p.3]；[doi:10.1021/acs.jcim.5c00741, p.12]；[doi:10.1021/acs.jcim.5c00741, p.13]
- **method：** 训练阶段把全部训练 bioactivity 合并后做 5-fold cross-validation，训练 10 个子模型并对预测取平均，作为 integrated bioactivity learning / ensemble。
  - 证据：[doi:10.1021/acs.jcim.5c00741, p.13]
- **method：** 作者同时设置 target-specific、general CPI 与 virtual screening 三类比较，并在 internal validation、rare protein、transfer learning 和 screening 场景下统一评估。
  - 证据：[doi:10.1021/acs.jcim.5c00741, p.3]；[doi:10.1021/acs.jcim.5c00741, p.13]；[doi:10.1021/acs.jcim.5c00741, p.14]
- **results：** 在 CPI2M-main 内部验证上，GGAP-CPI 在 Ki、Kd 和 IC50 的所有指标中均列第一，EC50 也在多数指标上领先；相对次优模型的 RMSE 改善约为 7.77%、5.95% 和 9.80%。
  - 证据：[doi:10.1021/acs.jcim.5c00741, p.5]；[doi:10.1021/acs.jcim.5c00741, p.6]
- **results：** 在 CPI2M-few 外部验证上，多数基线性能明显下降，而 GGAP-CPI 几乎在所有指标与数据集上最好；其 PCC 相对次优结果的提升约为 23.45%、18.67%、78.66% 和 15.09%。
  - 证据：[doi:10.1021/acs.jcim.5c00741, p.6]；[doi:10.1021/acs.jcim.5c00741, p.7]
- **results：** 在 MoleculeACE transfer learning 上，GGAP-CPI-ft 对 Ki 和 EC50 的 RMSE 及 RMSEcliff 都优于其他基线，论文报告的 RMSE 改善约为 8.27% 和 12.02%。
  - 证据：[doi:10.1021/acs.jcim.5c00741, p.7]
- **results：** 在 CASF-2016 与 MerckFEP 上，GGAP-CPI 的 scoring/ranking performance 具有竞争力且常为最佳；在 DUD-E、DEKOIS-v2 与 LIT-PCBA 上，其 EF1% 分别报告为 41.642、23.52，并在 LIT-PCBA 上保持与其他 CPI-SFs 相当。
  - 证据：[doi:10.1021/acs.jcim.5c00741, p.9]
- **results：** 不确定性筛选可降低子集 MAE，而 cross-attention 还能富集 pocket residues；论文给出的 pocket residue enrichment factor 为 4.389 ± 4.100，且 pocket 与 nonpocket residues 的 attention 分布差异显著。
  - 证据：[doi:10.1021/acs.jcim.5c00741, p.10]

## 页码证据

- [doi:10.1021/acs.jcim.5c00741, p.1]
- [doi:10.1021/acs.jcim.5c00741, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
