# PPI-Graphomer: enhanced protein-protein affinity prediction using pretrained and graph transformer models

- **论文 ID：** `EVIW-D5826B6BE45CEB6A`
- **期刊 / 来源：** BMC Bioinformatics（DOI 前缀识别）
- **发表时间：** 未记录
- **DOI：** [10.1186/s12859-025-06123-2](https://doi.org/10.1186/s12859-025-06123-2)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `结构预测` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者提出 PPI-Graphomer：结合 ESM2 与 ESM-IF1 的序列/结构表征，再用带界面偏置的 Graphormer 聚合跨链接触信息，以提升结合亲和力预测。

## 创新边界

`新意主要在界面偏置编码与预训练特征融合；它仍是监督式 affinity 回归，不是生成或优化候选分子。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在标注稀缺的 PPI 场景中，如何更准确地预测蛋白-蛋白结合亲和力，并补足现有预训练模型对界面热点残基与跨链相互作用信息的建模不足。

## 方法

- sequence/inverse-folding embeddings与interface graph transformer回归。

## 数据与基准

- 多个PPI affinity benchmark。

## 比较基线

- 传统energy/深度PPI affinity方法。

## 结果证据

- 论文报告优于现有方法并具泛化；为计算。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 界面结构、数据规模和assay异质。

## 仍未知

- Code of PPI-Graphomer 的具体仓库 URL 未在正文给出。
- Rosetta、FoldX、ColabFold 的具体版本与参数设置未完整展开。
- 去除长序列后的评估，未必能代表更长或更复杂多链体系的泛化表现。

## Pi 结构化证据摘录

- **baseline：** 与 PRODIGY、DFIRE、CP_PIE、ISLAND、PPI-Affinity 比较时，Test set 1 上 PRODIGY 的 PCC/MAE 最好，但本文模型在 Test set 2 与 combined set 上居首。
  - 证据：[doi:10.1186/s12859-025-06123-2, p.11]
- **baseline：** 与 Rosetta-InterfaceAnalyzer、FoldX-AnalyseComplex、ColabFold-iPAE 的 binary 子集比较表明，本文模型相关性更高；但这些方法只能在 binary complexes 上直接运行，因此比较范围被缩小。
  - 证据：[doi:10.1186/s12859-025-06123-2, p.12]
- **data：** 主训练数据来自 PDBbind 2020，共 2,852 个复合物；原始 Kd、Ki、IC50 标签被统一换算为 Gibbs free energy。
  - 证据：[doi:10.1186/s12859-025-06123-2, p.8]
- **data：** 为避免泄漏，作者用 BLAST 按相似度大于 0.65 且重叠长度大于 80% 从训练集中移除近似样本，最终训练集为 2,376 个；5-fold CV 数据集经 CD-HIT 以 0.75 阈值去重后为 2,085 个。
  - 证据：[doi:10.1186/s12859-025-06123-2, p.9]
- **data：** 外部测试集沿用两个 benchmark：Test set 1 由 79 个样本缩减到 75 个，Test set 2 由 90 个样本缩减到 87 个；作者还复核了更新版 Affinity Benchmark Version 2 的 188 个样本集合。
  - 证据：[doi:10.1186/s12859-025-06123-2, p.8]；[doi:10.1186/s12859-025-06123-2, p.11]
- **declared_resources：** 数据资源包括 PDBbind 2020、structure-based benchmark database for protein-protein binding affinity、PPI-Affinity benchmark 以及 Affinity Benchmark Version 2；作者还说明 PDBbind 数据来自 PDBbind 下载。
  - 证据：[doi:10.1186/s12859-025-06123-2, p.8]；[doi:10.1186/s12859-025-06123-2, p.13]
- **declared_resources：** 模型资源包括 ESM2 650M、ESM-IF1、Biopython 和作者实现的两层 PPI-Graphormer；ESM2 取第 33 层输出并降到 64 维，ESM-IF1 降到 32 维。
  - 证据：[doi:10.1186/s12859-025-06123-2, p.9]
- **declared_resources：** 算力资源是单张 A40 GPU 训练 20 个 epoch，作者还声称 4GB 显存 GPU 即可推理。
  - 证据：[doi:10.1186/s12859-025-06123-2, p.9]
- **declared_resources：** 作者声明 code、data 和 model parameters 已开源于 Code of PPI-Graphomer，但正文未给出可核验的直接 URL。
  - 证据：[doi:10.1186/s12859-025-06123-2, p.13]
- **limitations：** 作者在消融与结论中都暗示 ESM-IF1 只带来有限增益，可能因为其预训练数据规模较小、复杂体信息不足；模型主要收益来自 ESM2。
  - 证据：[doi:10.1186/s12859-025-06123-2, p.12]；[doi:10.1186/s12859-025-06123-2, p.13]
- **limitations：** 界面建模被限定为 7 Å 内的跨链相互作用，并且只显式编码 hydrogen bond、halogen bond、disulfide bond、salt bridge 和 π-π stacking，物理细节较为简化。
  - 证据：[doi:10.1186/s12859-025-06123-2, p.6]；[doi:10.1186/s12859-025-06123-2, p.7]
- **limitations：** 长于 2000 residues 的样本被剔除，且部分对比只能在 binary complex 子集上完成，说明评估覆盖面并不完全统一。
  - 证据：[doi:10.1186/s12859-025-06123-2, p.8]；[doi:10.1186/s12859-025-06123-2, p.12]
- **method：** 先用 ESM2 提取序列表征，并将多链复合体用 25 个 glycine linker 串接为单链；再用 ESM-IF1 提取结构表征，去掉 linker 位点后与序列表征拼接输入后续模块。
  - 证据：[doi:10.1186/s12859-025-06123-2, p.3]；[doi:10.1186/s12859-025-06123-2, p.5]；[doi:10.1186/s12859-025-06123-2, p.9]
- **method：** PPI-Graphomer 是两层 graph transformer：把 amino acid pair type、intermolecular interaction force 和 interface mask 写入 attention bias，并乘以距离权重；仅保留跨链且距离不超过 7 Å 的界面注意力。
  - 证据：[doi:10.1186/s12859-025-06123-2, p.6]；[doi:10.1186/s12859-025-06123-2, p.7]
- **method：** 界面输出再与原始输入做 skip-connection 式拼接，随后经 MLP 回归 affinity；训练损失采用预测值与标签之间的平均绝对误差形式。
  - 证据：[doi:10.1186/s12859-025-06123-2, p.4]；[doi:10.1186/s12859-025-06123-2, p.7]
- **results：** 5-fold cross-validation 上，模型达到 PCC 0.581、MAE 1.63。
  - 证据：[doi:10.1186/s12859-025-06123-2, p.10]
- **results：** 在 Test set 1 上，模型 PCC 0.641、MAE 1.64；在 Test set 2 上 PCC 0.625、MAE 1.51；合并集上 PCC 0.633、MAE 1.57。
  - 证据：[doi:10.1186/s12859-025-06123-2, p.10]；[doi:10.1186/s12859-025-06123-2, p.11]
- **results：** 在 binary complex 子集上，模型 PCC 为 0.708 和 0.633，作者报告其优于 Rosetta-InterfaceAnalyzer、FoldX-AnalyseComplex 和 ColabFold-iPAE 的对应结果。
  - 证据：[doi:10.1186/s12859-025-06123-2, p.12]
- **results：** 消融实验显示，去掉 PPI-Graphomer、去掉 ESM2 或去掉 ESM-IF1 都会降低 PCC 并抬高 MAE，说明三部分均有贡献。
  - 证据：[doi:10.1186/s12859-025-06123-2, p.12]；[doi:10.1186/s12859-025-06123-2, p.13]

## 页码证据

- [doi:10.1186/s12859-025-06123-2, p.1]
- [doi:10.1186/s12859-025-06123-2, p.3]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
