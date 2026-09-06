# PROSTATA: a framework for protein stability assessment using transformers

- **论文 ID：** `EVIW-DE65F63CDC81659C`
- **期刊 / 来源：** Bioinformatics
- **发表时间：** 2023 Nov 3
- **DOI：** [10.1093/bioinformatics/btad671](https://doi.org/10.1093/bioinformatics/btad671)
- **范围标签：** `Pi 已解析` / `核心相关` / `有静态审计仓库`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

提出 PROSTATA：一个基于预训练蛋白语言模型 ESM-2 的转移学习框架，结合多种回归头与集成策略，对单点突变的蛋白稳定性变化进行预测，并在作者构建的数据集和多个基准上报告了优于或不逊于现有神经网络方法的表现。

## 创新边界

`创新主要在于稳定性 ΔΔG 回归、预训练表示融合、数据整理与回归头设计；它不生成蛋白候选，也未在冻结材料中验证全球新颖性。`。这不是全球首创性检索或独立复现结论。

## 研究问题

预测单点氨基酸替换引起的蛋白稳定性变化（ΔΔG），并尽量只依赖序列与突变信息，减少对显式结构或手工特征的依赖。

## 方法

- 以 ESM-2 650M 表示突变前后序列/局部信息，再训练 Transformer/回归头预测稳定性变化，并用聚类折分五折交叉验证。[doi:10.1093/bioinformatics/btad671, p.4]

## 数据与基准

- 使用新整理训练集，并在 Q3488、Ssym、Ssym-r 等稳定性集合及按蛋白簇划分的交叉验证上评估。[doi:10.1093/bioinformatics/btad671, p.4]

## 比较基线

- PoPMuSiC、ProS-GNN、不同 PLM/回归头和数据集消融。[doi:10.1093/bioinformatics/btad671, p.1][doi:10.1093/bioinformatics/btad671, p.4]

## 结果证据

- 作者报告 PROSTATA 优于所比较神经网络方案，提升同时来自模型架构和新训练数据；摘要未给出单一可代表所有集合的统一数值。[doi:10.1093/bioinformatics/btad671, p.1]

## 可用资源与代码关系

- [https://github.com/AIRI-Institute/PROSTATA](https://github.com/AIRI-Institute/PROSTATA)
  - 固定 commit：`81b109f155ddde67b778fec169d1048e6a060213`
  - 静态复用层级：C_license_or_component_gaps
  - 许可证边界：license_identified_Apache-2.0_terms_require_review

## 已知限制

- 稳定性数据集存在测量条件差异、同源性和正负突变不对称；模型预测 ΔΔG 不等于表达、功能或体内适应度。[doi:10.1093/bioinformatics/btad671, p.1][doi:10.1093/bioinformatics/btad671, p.4]

## 仍未知

- 冻结材料未提供独立的全球新颖性证据。
- 未在冻结材料中实际访问 GitHub/网站以验证代码可用性。
- 没有湿实验或外部复现实验来确认预测提升的实际生物学收益。

## Pi 结构化证据摘录

- **baseline：** 作者在 S669 上与 INPS-Seq、ACDC-NN-Seq、DDGun、PremPS、ThermoNet、Rosetta、DynaMut、INPS3D、SDM、PoPMuSiC、MAESTRO、DUET 等方法比较。
  - 证据：[doi:10.1093/bioinformatics/btad671, p.6]
- **baseline：** 还在对应训练集与测试集上比较 ThermoNet、ACDC-NN、ACDC-NN-Seq 和 ProS-GNN，强调与原论文设置的一致性。
  - 证据：[doi:10.1093/bioinformatics/btad671, p.5]
- **baseline：** 文中指出 ThermoNet 依赖 Rosetta 预计算特征，ACDC-NN/ACDC-NN-Seq 需要 sequence profile，而 PROSTATA 仅需序列与突变信息。
  - 证据：[doi:10.1093/bioinformatics/btad671, p.5]；[doi:10.1093/bioinformatics/btad671, p.6]
- **data：** 作者从 VariBench 等来源合并并人工检查数据，按 PDB ID、链与突变编码聚合后，对 pH 和温度做分组平均，得到 5196 条样本。
  - 证据：[doi:10.1093/bioinformatics/btad671, p.2]；[doi:10.1093/bioinformatics/btad671, p.3]
- **data：** 随后又并入 mega dataset，并对每个 WT 序列最多保留 70 个样本，最终额外扩展 5251 条记录。
  - 证据：[doi:10.1093/bioinformatics/btad671, p.3]
- **data：** 训练集还加入了反向突变样本，以缓解对 destabilizing mutations 的类别偏置。
  - 证据：[doi:10.1093/bioinformatics/btad671, p.3]
- **data：** 构建了 Hemoglobin、oligomerization、mini_natural 和 mini_denovo 等专门测试集，用于检验困难场景。
  - 证据：[doi:10.1093/bioinformatics/btad671, p.3]
- **data：** 比较实验中还使用了 Q3421、Q3488、S2648、Ssym、S669、p53 和 Myoglobin 等公开基准集。
  - 证据：[doi:10.1093/bioinformatics/btad671, p.2]；[doi:10.1093/bioinformatics/btad671, p.5]；[doi:10.1093/bioinformatics/btad671, p.6]
- **declared_resources：** 论文声明代码与在线服务可在 GitHub 和网站获取：AIRI-Institute/PROSTATA 与 prostata.airi.net。
  - 证据：[doi:10.1093/bioinformatics/btad671, p.1]
- **declared_resources：** 方法依赖预训练蛋白语言模型 ESM-2 650M 作为表示来源。
  - 证据：[doi:10.1093/bioinformatics/btad671, p.4]
- **declared_resources：** 作者使用 BLAST 进行同源过滤，属于数据清洗与去泄漏所需的外部工具。
  - 证据：[doi:10.1093/bioinformatics/btad671, p.3]
- **limitations：** 模型没有显式输入蛋白-蛋白相互作用或 oligomerization 信息，因此在 interface 位点表现较弱。
  - 证据：[doi:10.1093/bioinformatics/btad671, p.7]
- **limitations：** 对 solvent-exposed residues 的误差更高，作者将其归因于缺少外部相互作用上下文。
  - 证据：[doi:10.1093/bioinformatics/btad671, p.7]
- **limitations：** binding site 位置未被显式编码，因此 ligand-binding 相关突变的预测也更具挑战。
  - 证据：[doi:10.1093/bioinformatics/btad671, p.7]
- **limitations：** 作者也承认更大的 ESM-2 版本可能更好，但会带来更长的训练与推理时间。
  - 证据：[doi:10.1093/bioinformatics/btad671, p.4]
- **method：** 采用 transfer learning：先用预训练的蛋白语言模型提取 WT 与 MT 序列表示，再将两者组合后进行 ΔΔG 回归。
  - 证据：[doi:10.1093/bioinformatics/btad671, p.3]；[doi:10.1093/bioinformatics/btad671, p.4]
- **method：** 以 ESM-2 650M 作为 backbone，输出每个残基的 1280 维嵌入，并在回归头中比较 position/CLS 的多种融合方式。
  - 证据：[doi:10.1093/bioinformatics/btad671, p.4]
- **method：** 训练时使用 ADAM、batch size 1、3 epochs，并对 5 个不同回归头的模型做平均集成以提升稳定性。
  - 证据：[doi:10.1093/bioinformatics/btad671, p.4]
- **method：** 通过蛋白 cluster 进行 5-fold cross-validation，确保同一 cluster 不会同时出现在训练折与测试折中。
  - 证据：[doi:10.1093/bioinformatics/btad671, p.4]
- **method：** 对训练集做 BLAST 同源过滤，去除与测试集序列相似度高于 30% 且 E-value < 0.05 的样本，以减少数据泄漏。
  - 证据：[doi:10.1093/bioinformatics/btad671, p.3]
- **results：** 5-fold CV 中，ensemble 的表现最好，达到 Pearson r 0.69、RMSE 1.57、MAE 1.03。
  - 证据：[doi:10.1093/bioinformatics/btad671, p.4]
- **results：** 线性融合类回归头在对称性学习上更稳健；outer product 和 concatenation 在训练偏置反转时会出现明显退化。
  - 证据：[doi:10.1093/bioinformatics/btad671, p.5]
- **results：** 在 S669 上，PROSTATA 对 direct 与 reverse mutations 都取得 r=0.49，优于大多数 sequence-based 工具，并与 structure-based 工具相当。
  - 证据：[doi:10.1093/bioinformatics/btad671, p.6]
- **results：** 在 buried residues 上相关性更高，在 beta-strand 区域表现最好；对 solvent-exposed residues 的性能较弱。
  - 证据：[doi:10.1093/bioinformatics/btad671, p.7]
- **results：** 在 oligomerization interface 和 ligand-binding interface 处的预测更困难，而 hemoglobin 相关蛋白上则显示出相对较好的表现。
  - 证据：[doi:10.1093/bioinformatics/btad671, p.7]

## 页码证据

- [doi:10.1093/bioinformatics/btad671, p.1]
- [doi:10.1093/bioinformatics/btad671, p.4]
- [doi:10.1093/bioinformatics/btad671, p.1]
- [doi:10.1093/bioinformatics/btad671, p.4]
- [doi:10.1093/bioinformatics/btad671, p.4]
- [doi:10.1093/bioinformatics/btad671, p.1]
- [doi:10.1093/bioinformatics/btad671, p.1]
- [doi:10.1093/bioinformatics/btad671, p.4]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
