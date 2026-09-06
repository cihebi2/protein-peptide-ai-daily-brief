# RNA-EFM: energy-based flow matching for protein-conditioned RNA sequence-structure co-design

- **论文 ID：** `EVIW-F532E27CA97BDB0E`
- **期刊 / 来源：** Bioinform Adv
- **发表时间：** 2025 Oct 22
- **DOI：** [10.1093/bioadv/vbaf258](https://doi.org/10.1093/bioadv/vbaf258)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `有静态审计仓库` / `扩散/生成` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

提出 RNA-EFM：把 flow matching、idempotent 迭代精炼以及 Lennard-Jones 与 sequence-derived free energy 的能量约束结合起来，用于 protein-conditioned RNA sequence-structure co-design。

## 创新边界

`创新边界在于本文自述的“能量约束 + flow matching”组合；是否为全球首次未由冻结材料独立验证。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在蛋白条件下联合生成 RNA 序列与三维主链，并让生成结果同时满足几何匹配与热力学/物理稳定性。

## 方法

- 流匹配从高斯RNA骨架映射到目标构象，联合序列预测；第二阶段以结构误差、Lennard-Jones和序列自由能做迭代能量精修。

## 数据与基准

- PDBBind 2020蛋白-RNA复合物，沿用RNAFlow预处理；RF2NA隔离拆分和序列相似性拆分，每个复合物生成50个样本。

## 比较基线

- RNAFlow-Base、RNAFlow-Traj、RNAFlow-Base+Rescore、Conditional MMDiff、LSTM和随机序列。

## 结果证据

- RF2NA拆分RMSD 10.00、lDDT 0.60，优于RNAFlow-Base的12.85/0.51；序列相似性拆分RMSD 13.00、lDDT 0.60，序列恢复0.35；结合能改善和新颖性来自PyRosetta/计算指标，不是实验结合。

## 可用资源与代码关系

- [https://github.com/abrarrahmanabir/RNA-EFM](https://github.com/abrarrahmanabir/RNA-EFM)
  - 固定 commit：`975b407d5ef9b56a4af4b2d70fdd567ce79e7eeb`
  - 静态复用层级：C_license_or_component_gaps
  - 许可证边界：license_not_found_reuse_blocked

## 已知限制

- 数据规模和结构域有限；能量由近似势和PyRosetta评估，不能替代实验；未验证真实RNA表达、折叠、稳定性与结合。

## 仍未知

- 补充材料中的超参数与更完整的消融细节未在冻结正文中展开。
- 代码仓库与 dataset 仅有链接，冻结材料未核验仓库内容、可运行性或复现实验脚本。
- 作者的全球首创性表述未经过外部文献检索验证。

## Pi 结构化证据摘录

- **baseline：** 结构生成对比对象包括 Conditional MMDiff、RNAFlow-Base、RNAFlow-Traj 及其两种 rescore 变体。
  - 证据：[doi:10.1093/bioadv/vbaf258, p.5]；[doi:10.1093/bioadv/vbaf258, p.6]
- **baseline：** 序列生成对比对象包括 Random、LSTM、Conditional MMDiff 以及 RNAFlow 的各个变体。
  - 证据：[doi:10.1093/bioadv/vbaf258, p.6]
- **baseline：** 新颖性与案例比较中还使用了 MMDiff 和 RNAFlow 作为主要参照。
  - 证据：[doi:10.1093/bioadv/vbaf258, p.7]；[doi:10.1093/bioadv/vbaf258, p.8]
- **data：** 实验数据沿用 RNAFlow 的 2020 版 PDBBind protein-RNA complexes，并按同一预处理方案构建。
  - 证据：[doi:10.1093/bioadv/vbaf258, p.5]
- **data：** RF2NA-aware split 的规模为 1059/117/16，对应 train/validation/test。
  - 证据：[doi:10.1093/bioadv/vbaf258, p.5]
- **data：** sequence similarity split 先用 CD-HIT 按 80% identity 聚类，再划分为 1015/105/72。
  - 证据：[doi:10.1093/bioadv/vbaf258, p.5]
- **declared_resources：** 论文页内给出源代码仓库 https://github.com/abrarrahmanabir/RNA-EFM 。
  - 证据：[doi:10.1093/bioadv/vbaf258, p.1]；[doi:10.1093/bioadv/vbaf258, p.9]
- **declared_resources：** 作者同时声明 dataset 也可在同一 GitHub 仓库中获取。
  - 证据：[doi:10.1093/bioadv/vbaf258, p.9]
- **declared_resources：** 实验在 NVIDIA RTX A4500 上完成，训练约 14 小时，推理约 11 秒/样本。
  - 证据：[doi:10.1093/bioadv/vbaf258, p.5]
- **declared_resources：** 资金来源为 NSF AWARD 2319522。
  - 证据：[doi:10.1093/bioadv/vbaf258, p.8]
- **limitations：** 作者明确承认所用 coarse-grained Lennard-Jones potential 不能捕捉全部原子相互作用，因此物理建模仍是简化近似。
  - 证据：[doi:10.1093/bioadv/vbaf258, p.4]
- **limitations：** 结论把 multi-protein binding 和 small-molecule aptamer design 只作为未来方向，说明当前方法尚未覆盖这些任务。
  - 证据：[doi:10.1093/bioadv/vbaf258, p.8]
- **method：** 本文把蛋白与 RNA 都表示为 3-bead coarse-grained 骨架，并在蛋白条件下联合生成 RNA 序列与主链结构。
  - 证据：[doi:10.1093/bioadv/vbaf258, p.1]；[doi:10.1093/bioadv/vbaf258, p.2]
- **method：** Flow matching 先将高斯先验 RNA 主链与目标主链做 Kabsch 对齐，再通过线性插值学习向量场，并用对齐后的 MSE 训练。
  - 证据：[doi:10.1093/bioadv/vbaf258, p.3]
- **method：** 能量化精炼把预测结构放入条件分布并最小化几何误差与物理能量，能量项包含 Lennard-Jones potential 和 sequence-derived free energy。
  - 证据：[doi:10.1093/bioadv/vbaf258, p.4]
- **method：** 训练时在 flow matching 与 refinement 两个阶段间各占约 50%，序列部分用 Noise-to-Seq 和 RF2NA 生成，并以 cross entropy 监督。
  - 证据：[doi:10.1093/bioadv/vbaf258, p.5]
- **results：** 在 RF2NA-aware split 上，RNA-EFM 的 structure 结果为 RMSD 10.00、lDDT 0.60，优于 RNAFlow-Base+Rescore 的 10.61/0.53。
  - 证据：[doi:10.1093/bioadv/vbaf258, p.6]
- **results：** 在 sequence similarity split 上，RNA-EFM 的 structure 结果为 RMSD 13.00、lDDT 0.60，优于 RNAFlow-Base+Rescore 的 14.60/0.56。
  - 证据：[doi:10.1093/bioadv/vbaf258, p.6]
- **results：** Sequence recovery 分别达到 0.40 和 0.35，均高于对应 split 的最佳 baseline。
  - 证据：[doi:10.1093/bioadv/vbaf258, p.6]
- **results：** IMP 在两个 split 上分别达到 64% 和 61%，高于次优方法的 56% 和 55%。
  - 证据：[doi:10.1093/bioadv/vbaf258, p.6]
- **results：** 新颖性分析显示 sequence novelty 最高可到 0.72、structure novelty 最高可到 0.76。
  - 证据：[doi:10.1093/bioadv/vbaf258, p.7]
- **results：** 案例研究中，PDB 2ZNI 与 8H1B 上 RNA-EFM 的 RMSD、sequence recovery 和 IMP 也都优于 RNAFlow 与 MMDiff。
  - 证据：[doi:10.1093/bioadv/vbaf258, p.8]
- **results：** 去掉 iterative refinement、LJ potential 或 SDFE 都会明显拉低 IMP，其中去掉 refinement 约造成 5 个百分点的绝对下降。
  - 证据：[doi:10.1093/bioadv/vbaf258, p.7]；[doi:10.1093/bioadv/vbaf258, p.8]

## 页码证据

- [doi:10.1093/bioadv/vbaf258, p.1]
- [doi:10.1093/bioadv/vbaf258, p.5]
- [doi:10.1093/bioadv/vbaf258, p.6]
- [doi:10.1093/bioadv/vbaf258, p.7]
- [doi:10.1093/bioadv/vbaf258, p.8]
- [doi:10.1093/bioadv/vbaf258, p.9]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
