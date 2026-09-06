# PLiSAGE: enhancing protein-ligand interaction prediction with multimodal surface and geometry encoding

- **论文 ID：** `EVIW-7B3BB7FC1C77330C`
- **期刊 / 来源：** Bioinformatics
- **发表时间：** 2025 Nov 9
- **DOI：** [10.1093/bioinformatics/btaf608](https://doi.org/10.1093/bioinformatics/btaf608)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白-配体` / `结构预测` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者提出 PLiSAGE：用 GVP 编码结构、用 patch-based Transformer 编码表面，并通过 contrastive pretraining、point cloud reconstruction 与 adaptive fusion 联合学习 protein representation；作者还声称这是首次联合编码 3D structure 与 surface features 的 self-supervised 方案。

## 创新边界

`新意主要在 multimodal surface-geometry encoding 与 joint self-supervised pretraining；它是预测/表征模型，不是候选分子生成或直接 docking 优化。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在标注数据有限的情况下，如何把 protein 3D structure、surface geometry 和 ligand graph 有效融合，以更准确地预测 binding affinity 与 protein-ligand interaction。

## 方法

- GVP编码蛋白原子/残基图，表面被分割为点云patch；通过对比学习与点云重建联合预训练，再以自注意/交叉注意编码器-解码器融合配体与蛋白表示。

## 数据与基准

- 亲和力任务使用PDBBind v2020；分类任务使用BIOSNAP、DAVIS和BindingDB，论文还比较AlphaFold2结构输入。

## 比较基线

- GraphDTA、MolTrans、DrugBAN、TankBind、SIGN、GNINA、dMaSIF、ESM-2、MPRL以及单模态/无预训练消融。

## 结果证据

- 论文报告PDBBind上RMSE 1.345、MAE 1.047、Pearson 0.675、Spearman 0.672；BindingDB上AUROC 0.935±0.002、AUPRC 0.681±0.004。均为计算基准结果。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 仍依赖蛋白结构/预测结构质量和预处理得到的表面；标签数据集分布与结构重叠可能影响泛化，尚未通过前瞻实验验证新配体。

## 仍未知

- 论文未提供外部独立复现结果。
- “first” 主张缺乏本次证据之外的先前工作核验。
- 分类任务使用 AlphaFold2 预测结构，实验结构与预测结构的差异未单独分析。

## Pi 结构化证据摘录

- **baseline：** affinity 任务比较了 sequence-based、structure-based、surface-based 和 multimodal baselines，包括 GraphDTA、MolTrans、DrugBAN、TankBind、dMaSIF、Pafnucy、MPRL、MFE 等。
  - 证据：[doi:10.1093/bioinformatics/btaf608, p.6]；[doi:10.1093/bioinformatics/btaf608, p.7]
- **baseline：** interaction classification 任务比较了 DeepConv-DTI、MolTrans、Kang et al.、MoDTI、DLM-DTI、MPRL、MFE 等方法。
  - 证据：[doi:10.1093/bioinformatics/btaf608, p.6]；[doi:10.1093/bioinformatics/btaf608, p.7]
- **data：** 预训练数据来自 AlphaFold v2 Protein Structure Database 的 Swiss-Prot subset，规模约 54 万个蛋白结构。
  - 证据：[doi:10.1093/bioinformatics/btaf608, p.6]；[doi:10.1093/bioinformatics/btaf608, p.11]
- **data：** affinity 评估使用 PDBbind v2020 的 General Set 与 Refined Set，外部测试用 CASF-2016 的 285 个复合物，且训练、验证和测试集没有重叠。
  - 证据：[doi:10.1093/bioinformatics/btaf608, p.6]
- **data：** interaction classification 评估使用 BIOSNAP、DAVIS、BindingDB；作者按 MolTrans 流程生成负样本，并用 AlphaFold2 为这些数据集补全蛋白结构。
  - 证据：[doi:10.1093/bioinformatics/btaf608, p.6]
- **data：** 论文给出完整源代码、数据预处理脚本与训练脚本的公开 GitHub 仓库。
  - 证据：[doi:10.1093/bioinformatics/btaf608, p.1]；[doi:10.1093/bioinformatics/btaf608, p.11]
- **declared_resources：** AlphaFold Protein Structure Database 作为预训练资源公开可得，并标注 CC-BY 4.0。
  - 证据：[doi:10.1093/bioinformatics/btaf608, p.11]
- **declared_resources：** PDBbind v2020 来自官方站点，BIOSNAP、DAVIS、BindingDB 来自 MolTrans 的公开数据仓库。
  - 证据：[doi:10.1093/bioinformatics/btaf608, p.11]
- **declared_resources：** PLiSAGE 的完整源代码公开在 GitHub，论文还说明包含 data preprocessing 和 training scripts。
  - 证据：[doi:10.1093/bioinformatics/btaf608, p.1]；[doi:10.1093/bioinformatics/btaf608, p.11]
- **limitations：** 作者在展望中仍需解决 multimeric protein interactions 的 subunit interface 区分问题。
  - 证据：[doi:10.1093/bioinformatics/btaf608, p.10]
- **limitations：** 把模型扩展到 molecular dynamics conformational ensembles 会带来明显的计算开销和多 snapshot 聚合难题。
  - 证据：[doi:10.1093/bioinformatics/btaf608, p.10]
- **limitations：** 作者还指出 evolutionary data 与 binding kinetics（kon/koff）目标仍未纳入当前框架。
  - 证据：[doi:10.1093/bioinformatics/btaf608, p.10]
- **method：** 先把蛋白表面从原子点云中采样出来：筛选主要原子类型，借助 smoothed distance function 在 r=1Å 的 level set 上取点，并为每个 surface point 提取近邻原子、normal、mean/Gaussian curvature 等特征。
  - 证据：[doi:10.1093/bioinformatics/btaf608, p.2]；[doi:10.1093/bioinformatics/btaf608, p.3]
- **method：** 把蛋白内部结构表示成 residue graph：以 Cα 近邻构边，每个节点和边都使用 scalar/vector features，再交给 GVP-GNN 做几何感知消息传递。
  - 证据：[doi:10.1093/bioinformatics/btaf608, p.3]；[doi:10.1093/bioinformatics/btaf608, p.4]
- **method：** 将 surface point cloud 通过 FPS + KNN 划分为 patch tokens，再用 Transformer 编码局部与全局依赖，形成 surface-level protein representation。
  - 证据：[doi:10.1093/bioinformatics/btaf608, p.4]
- **method：** 预训练阶段同时最小化 surface-structure contrastive loss 与 masked surface reconstruction loss，其中重建项使用 Chamfer distance 约束。
  - 证据：[doi:10.1093/bioinformatics/btaf608, p.5]
- **method：** 下游任务里，ligand 由 MPNN 编码，protein 的 structure/surface embedding 经 Transformer-based adaptive fusion 后再与 ligand embedding 拼接，最后用 MLP 做 affinity regression 或 binary classification。
  - 证据：[doi:10.1093/bioinformatics/btaf608, p.5]；[doi:10.1093/bioinformatics/btaf608, p.6]
- **results：** 在 PDBbind v2020 上，PLiSAGE 取得表中最佳或并列最佳的 RMSE 1.345、MAE 1.047、r2m 0.422 和 CI 0.743。
  - 证据：[doi:10.1093/bioinformatics/btaf608, p.6]；[doi:10.1093/bioinformatics/btaf608, p.7]
- **results：** 在 BIOSNAP、DAVIS、BindingDB 上，PLiSAGE 分别达到 AUROC/AUPRC 0.924/0.921、0.911/0.529、0.935/0.681。
  - 证据：[doi:10.1093/bioinformatics/btaf608, p.6]；[doi:10.1093/bioinformatics/btaf608, p.7]
- **results：** 消融实验显示 surface、structure 与 pretraining 都有互补贡献；其中去掉 contrastive loss 的性能下降比去掉 reconstruction loss 更明显。
  - 证据：[doi:10.1093/bioinformatics/btaf608, p.8]；[doi:10.1093/bioinformatics/btaf608, p.9]
- **results：** 案例分析把 SARS-CoV Mpro 的 binding pocket 定位到 CYS-145、HIS-163、GLU-166、GLN-189 等关键残基。
  - 证据：[doi:10.1093/bioinformatics/btaf608, p.9]；[doi:10.1093/bioinformatics/btaf608, p.10]

## 页码证据

- [doi:10.1093/bioinformatics/btaf608, p.10]
- [doi:10.1093/bioinformatics/btaf608, p.11]
- [doi:10.1093/bioinformatics/btaf608, p.1]
- [doi:10.1093/bioinformatics/btaf608, p.2]
- [doi:10.1093/bioinformatics/btaf608, p.5]
- [doi:10.1093/bioinformatics/btaf608, p.6]
- [doi:10.1093/bioinformatics/btaf608, p.7]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
