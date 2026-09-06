# An image-based protein-ligand binding representation learning framework via multi-level flexible dynamics trajectory pre-training

- **论文 ID：** `EVIW-50596DE988BFF9EC`
- **期刊 / 来源：** Bioinformatics
- **发表时间：** 2025 Sep 24
- **DOI：** [10.1093/bioinformatics/btaf535](https://doi.org/10.1093/bioinformatics/btaf535)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白-配体` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

提出 ImagePLB：将 ligand 表示为多视图 3D image、protein 表示为几何图，并通过 BRL 融合跨模态交互；再用 MLNTP 与 trajectory regularization 在 MISATO 轨迹上预训练成 ImagePLB-P，以提升 downstream 预测。

## 创新边界

`创新边界主要是表征学习与预训练框架，不是候选分子的生成或优化；作者声称首次用图像增强 PLB 表征，但本次冻结证据未独立核验该“first”主张。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在蛋白-配体结合预测中，如何在标注稀缺且图模型对原子长度敏感的情况下，学习更稳健、更高质量的 PLB 表征，用于亲和力与效能预测。

## 方法

- 配体表示学习器读取多视角3D图像，蛋白表示学习器读取图结构，结合表示学习器融合二者；预训练加入轨迹正则以利用柔性动力学变化。

## 数据与基准

- 在PDBBind的30%/60%序列同一性和scaffold拆分上评估亲和力，并在LEP等效力分类任务上评估；轨迹用于预训练。

## 比较基线

- DeepDTA、TAPE、ProtTrans、MaSIF、3DCNN、ProtMD、LEFTNet、Uni-Mol、DrugCLIP及无轨迹正则消融。

## 结果证据

- ImagePLB-P在PDBBind-30上RMSE 1.352、Pearson 0.606、Spearman 0.601；论文报告相对非预训练方法的LEP分类AUROC/AUPR改善15.8%/30.6%，相对预训练方法改善5.5%/13.8%。均为计算结果。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 依赖生成多视图图像和动力学轨迹，预计算成本与结构质量会限制应用；部分拆分上不是所有指标都最优，未给出湿实验验证。

## 仍未知

- 代码与数据可用性仅据论文声明，未实际拉取验证
- 独立 prior-art 与“first”主张未核验
- MISATO 与下游基准的完整复现链未在本次审阅中执行

## Pi 结构化证据摘录

- **baseline：** 非预训练 baselines 包括 DeepDTA、SSA、TAPE、ProtTrans、MaSIF、3DCNN、IEConv、HoloProt、ProtMD、LEFTNet。
  - 证据：[doi:10.1093/bioinformatics/btaf535, p.5]；[doi:10.1093/bioinformatics/btaf535, p.6]
- **baseline：** 预训练 baselines 包括 SSM-DTA、GeoSSL-DDM、ProtMD-P、Uni-Mol、DrugCLIP；LEP 额外比较了 3DGCN、Cormorant、SchNet、PaiNN、Equiformer。
  - 证据：[doi:10.1093/bioinformatics/btaf535, p.5]；[doi:10.1093/bioinformatics/btaf535, p.6]
- **data：** 预训练数据集是 MISATO，作者描述其包含约 20,000 个实验蛋白-配体复合体及累计超过 170 μs 的 molecular dynamics simulations。
  - 证据：[doi:10.1093/bioinformatics/btaf535, p.5]
- **data：** 下游任务使用 PDBbind-30、PDBbind-60、PDBbind-scaffold，以及 LEP；PDBbind splits 来自 PDBbind v2019。
  - 证据：[doi:10.1093/bioinformatics/btaf535, p.5]
- **data：** 他们还构造了 PDBbind-30-nonoverlap，训练/验证/测试集分别为 3313/461/490 个 complexes，且蛋白与配体都不重叠。
  - 证据：[doi:10.1093/bioinformatics/btaf535, p.7]
- **declared_resources：** 代码与数据公开在 GitHub 和 figshare；paper 同时给出 ImagePLB 仓库与 figshare DOI。
  - 证据：[doi:10.1093/bioinformatics/btaf535, p.1]；[doi:10.1093/bioinformatics/btaf535, p.9]
- **declared_resources：** 实现细节使用 ResNet18 + EGNN，实验在 Ubuntu 18.04、AMD EPYC 7542、8× RTX 4090、512 GB RAM 上完成。
  - 证据：[doi:10.1093/bioinformatics/btaf535, p.5]
- **declared_resources：** Ligand images 由 PyMol 生成，ImageNet 预训练权重用于 ResNet18 初始化。
  - 证据：[doi:10.1093/bioinformatics/btaf535, p.3]；[doi:10.1093/bioinformatics/btaf535, p.5]
- **limitations：** 作者在结论中只把更大分子、polypeptides 和 proteins 作为未来工作，说明当前版本仍主要验证在小分子-蛋白体系与既有基准上。
  - 证据：[doi:10.1093/bioinformatics/btaf535, p.8]
- **limitations：** 论文没有在页内给出独立湿实验验证，性能主张主要来自 benchmark 和 ablation，因此外部可迁移性仍需进一步验证。
  - 证据：[doi:10.1093/bioinformatics/btaf535, p.1]；[doi:10.1093/bioinformatics/btaf535, p.5]；[doi:10.1093/bioinformatics/btaf535, p.7]；[doi:10.1093/bioinformatics/btaf535, p.8]
- **method：** 作者把 PLB 重新定义为 image-ligand 与 geometric-graph-protein 之间的跨模态匹配问题，并用 Enc_L、Enc_P、Enc_F 形成 binding representation。
  - 证据：[doi:10.1093/bioinformatics/btaf535, p.2]；[doi:10.1093/bioinformatics/btaf535, p.3]
- **method：** LRL 通过 PyMol 生成 4 个视角的 3D ligand images，再用 ImageNet 初始化的 ResNet18 提取特征并做平均池化。
  - 证据：[doi:10.1093/bioinformatics/btaf535, p.3]
- **method：** PRL 先按 ligand 周围 6 Å 选 pocket，再用 α-C atom 几何图与 EGNN 编码，且实现中最大 atom length 设为 100。
  - 证据：[doi:10.1093/bioinformatics/btaf535, p.3]；[doi:10.1093/bioinformatics/btaf535, p.5]
- **method：** BRL 用双向 cross-attention 和 fusion enhancement 将 ligand 与 protein/pocket 信息互相增强，得到 refined features。
  - 证据：[doi:10.1093/bioinformatics/btaf535, p.3]
- **method：** MLNTP 在 10 ns dynamics trajectory 上做 next-trajectory prediction，丢弃前 2 ns 作为平衡期，并在 ligand、protein、complex 三个层次用 L1 loss 学习时序变化。
  - 证据：[doi:10.1093/bioinformatics/btaf535, p.4]
- **method：** TR 用指数形式的 trajectory regularization 约束相邻轨迹不要塌缩为近似相同表示，并和 NTP loss 按 λ 加权形成 pre-training loss。
  - 证据：[doi:10.1093/bioinformatics/btaf535, p.4]
- **results：** 在 PDBbind-30/60/scaffold 上，ImagePLB 优于全部 non-pretrained baselines，ImagePLB-P 进一步提升并在 PDBbind 上整体领先 pretrained baselines。
  - 证据：[doi:10.1093/bioinformatics/btaf535, p.5]；[doi:10.1093/bioinformatics/btaf535, p.6]
- **results：** 在 LEP 上，ImagePLB 达到 0.758 ACC、0.806 AUROC、0.781 AUPRC；ImagePLB-P 达到 0.755 ACC、0.819 AUROC、0.790 AUPRC。
  - 证据：[doi:10.1093/bioinformatics/btaf535, p.6]
- **results：** 在 PDBbind-30-nonoverlap 上，ImagePLB-P 取得最佳 RMSE 1.350、Pearson 0.598、Spearman 0.590。
  - 证据：[doi:10.1093/bioinformatics/btaf535, p.7]
- **results：** Ligand image ablation 显示，把 ligand graph 换成 image 后，PDBbind-30/60 的平均 RMSE、Pearson、Spearman 分别改善 3.6%、5.0%、4.7%。
  - 证据：[doi:10.1093/bioinformatics/btaf535, p.7]
- **results：** Trajectory regularization 的消融表明，去掉 TR 会出现近似 collapse；加入 TR 后，ImagePLB-P 的预训练 loss 更合理且测试表现更好。
  - 证据：[doi:10.1093/bioinformatics/btaf535, p.7]；[doi:10.1093/bioinformatics/btaf535, p.8]

## 页码证据

- [doi:10.1093/bioinformatics/btaf535, p.1]
- [doi:10.1093/bioinformatics/btaf535, p.2]
- [doi:10.1093/bioinformatics/btaf535, p.5]
- [doi:10.1093/bioinformatics/btaf535, p.6]
- [doi:10.1093/bioinformatics/btaf535, p.7]
- [doi:10.1093/bioinformatics/btaf535, p.9]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
