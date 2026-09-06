# DDAffinity: predicting the changes in binding affinity of multiple point mutations using protein 3D structure

- **论文 ID：** `EVIW-B067DEF24DEA2110`
- **期刊 / 来源：** Bioinformatics
- **发表时间：** 2024 Jun 28
- **DOI：** [10.1093/bioinformatics/btae232](https://doi.org/10.1093/bioinformatics/btae232)
- **范围标签：** `Pi 已解析` / `核心相关` / `有静态审计仓库` / `蛋白-配体`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者提出 DDAffinity：一个基于 k-nearest neighbor residue graph 的空间-序列双通道 message passing 模型，结合 residue centrality normalization 与两步 additive Gaussian noising，用于多点突变 ΔΔG 预测，并在多个基准和案例中取得更优结果。

## 创新边界

`新意主要在结构表征与打分模型，不是新蛋白生成或实验优化平台。`。这不是全球首创性检索或独立复现结论。

## 研究问题

如何利用蛋白质3D结构，准确预测多个点突变导致的蛋白-蛋白结合亲和力变化（ΔΔG），并克服现有方法主要面向单点突变、难以系统刻画局部与全局协同 epistasis 的问题。

## 方法

- kNN残基图、Invariant Point Attention/序列模块编码WT与mutant，局部几何加噪迫使学习全局拓扑，再回归ΔΔG。

## 数据与基准

- SKEMPI2训练/验证，多点突变内部测试和外部验证集。

## 比较基线

- mCSM-PPI2、GeoPPI、RDE类mutation-effect模型及组件消融。

## 结果证据

- 论文报告多点突变各指标优于端到端和预训练基线；均为回顾性ΔΔG预测。

## 可用资源与代码关系

- [https://github.com/ak422/DDAffinity](https://github.com/ak422/DDAffinity)
  - 固定 commit：`2055bc50f9a4d2920dfcb00635ecef886f927a84`
  - 静态复用层级：B_static_partial_shape
  - 许可证边界：license_identified_Apache-2.0_terms_require_review

## 已知限制

- 依赖正确WT/MT三维结构，SKEMPI多点样本有限；ΔΔG预测不等于实验亲和力。

## 仍未知

- 未见新的 wet-lab 实验，外部验证均为 in silico。
- 未核验 GitHub 仓库中的实现、训练脚本与论文是否完全一致。
- 模型对 FoldX 生成突变结构误差的敏感性未被单独拆分评估。

## Pi 结构化证据摘录

- **baseline：** 对比基线覆盖 energy function、sequence based、end-to-end 和 pre-trained 四类，具体包括 FoldX、Rosetta、flex ddG、ESM-1v、ESM-IF、DDGPred、RDE-Network 与 DiffAffinity。
  - 证据：[doi:10.1093/bioinformatics/btae232, p.8]
- **baseline：** complex-level 对比还包含 GeoPPI、TopGBT 和 UniBind；盲测对比包含 Discovery Studio 与 mmCSM-PPI。
  - 证据：[doi:10.1093/bioinformatics/btae232, p.8]
- **data：** 训练与验证数据来自 SKEMPI2，共 345 个 complexes 和 7805 个 point mutations，且 3D 结构来自 PDB。
  - 证据：[doi:10.1093/bioinformatics/btae232, p.3]
- **data：** 作者使用 S1131（1131 个非冗余 interface single mutations）、M1707（1707 个 multiple mutations，含 reverse mutations）以及过滤后的盲测集 M1340/M595。
  - 证据：[doi:10.1093/bioinformatics/btae232, p.3]
- **data：** 外部案例数据包含 Wuhan-Hu-1 RBD（PDB 6M0J）的 285 个单点突变，以及 SARS-CoV-2 RBD（PDB 7FAE）的 494 个单点突变。
  - 证据：[doi:10.1093/bioinformatics/btae232, p.3]
- **declared_resources：** 论文声明使用的 datasets 均为公开资源，来源包括 SKEMPI2、PDB 结构及其衍生 benchmark/validation 集。
  - 证据：[doi:10.1093/bioinformatics/btae232, p.3]；[doi:10.1093/bioinformatics/btae232, p.9]
- **declared_resources：** 作者声明 data 和 source code 可在 GitHub 的 https://github.com/ak422/DDAffinity 获取。
  - 证据：[doi:10.1093/bioinformatics/btae232, p.9]
- **declared_resources：** 经费来自 NSFC 项目 [62350004, U22A2041, 62072473]、湖南省杰青项目 2023JJ10080，并使用了 Central South University HPC Center 资源。
  - 证据：[doi:10.1093/bioinformatics/btae232, p.9]
- **limitations：** 作者把融合 sequence/structure pre-training 与更高效的 residue burial 加权函数列为未来工作，说明当前表示与加权设计仍有改进空间。
  - 证据：[doi:10.1093/bioinformatics/btae232, p.9]
- **limitations：** 作者也明确提到希望引入更多 protein complex context，因为当前工作主要围绕 mutation site 的 neighborhood message passing 展开。
  - 证据：[doi:10.1093/bioinformatics/btae232, p.9]
- **limitations：** 突变体结构依赖 FoldX 的 BuildModel/Optimize 生成；论文未单独证明该结构生成流程不会影响下游 ΔΔG 评估。
  - 证据：[doi:10.1093/bioinformatics/btae232, p.3]；[doi:10.1093/bioinformatics/btae232, p.6]
- **method：** 作者将 WT/MT 的残基级 3D 结构表示为 k-nearest neighbor residue graph，并分别引入 spatial、sequential 与 long-range 邻域做 message passing；默认参数为 k1=16、k2=3、k3=7。
  - 证据：[doi:10.1093/bioinformatics/btae232, p.2]；[doi:10.1093/bioinformatics/btae232, p.3]；[doi:10.1093/bioinformatics/btae232, p.6]
- **method：** 结构编码器以 ProteinMPNN 为骨架，采用 node/edge 双通道更新、残差连接、LayerNorm/FFN 与融合层，并在 WT 与 MT 之间共享参数。
  - 证据：[doi:10.1093/bioinformatics/btae232, p.4]；[doi:10.1093/bioinformatics/btae232, p.5]
- **method：** 边特征由 distance、direction、orientation、amino acid pair 和 position 组成；节点特征由 backbone/sidechain 二面角与理化性质共同构成。
  - 证据：[doi:10.1093/bioinformatics/btae232, p.5]；[doi:10.1093/bioinformatics/btae232, p.6]
- **method：** 作者提出 residue centrality normalization，并在读出阶段对 WT 与 MT 表征做差，再施加 anti-symmetry 约束，训练时使用 MSE loss。
  - 证据：[doi:10.1093/bioinformatics/btae232, p.5]；[doi:10.1093/bioinformatics/btae232, p.6]
- **method：** 训练阶段仅在输入坐标与 backbone 原子坐标上施加两步 additive Gaussian noise（std=0.2Å），且只在训练时使用。
  - 证据：[doi:10.1093/bioinformatics/btae232, p.6]
- **results：** 在 SKEMPI2 的 10-fold cross-validation 中，DDAffinity 在 multiple subset 上取得 r=0.693、q=0.640、RMSE=1.944、MAE=1.496、AUROC=0.812。
  - 证据：[doi:10.1093/bioinformatics/btae232, p.8]
- **results：** 在 complex-level 的 S1131 与 M1707 上，DDAffinity 的 r 都达到 0.80，优于表中列出的 GeoPPI、RDE-Network、DiffAffinity、UniBind、DDGPred 等方法。
  - 证据：[doi:10.1093/bioinformatics/btae232, p.8]
- **results：** 在非冗余盲测集 M595 上，DDAffinity 达到 r=0.74、q=0.70、RMSE=1.91、AUROC=0.83，优于 FoldX、Discovery Studio 和 mmCSM-PPI。
  - 证据：[doi:10.1093/bioinformatics/btae232, p.8]
- **results：** 在 SARS-CoV-2 RBD 变体任务上，DDAffinity 的 r=0.456 高于 FoldX、RDE-Network 和 DiffAffinity；在人抗体优化任务上，Hits@50=0.6，且将 5 个有利突变中的 3 个排进前 50%。
  - 证据：[doi:10.1093/bioinformatics/btae232, p.8]
- **results：** 消融实验表明，移除 RC、SI、LR、IA、BA 或 DO 都会带来不同程度的性能下降，说明各模块均有贡献。
  - 证据：[doi:10.1093/bioinformatics/btae232, p.9]

## 页码证据

- [doi:10.1093/bioinformatics/btae232, p.1]
- [doi:10.1093/bioinformatics/btae232, p.2]
- [doi:10.1093/bioinformatics/btae232, p.8]
- [doi:10.1093/bioinformatics/btae232, p.9]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
