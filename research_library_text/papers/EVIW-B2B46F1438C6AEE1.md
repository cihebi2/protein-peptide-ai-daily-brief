# A Folding-Docking-Affinity framework for protein-ligand binding affinity prediction

- **论文 ID：** `EVIW-B2B46F1438C6AEE1`
- **期刊 / 来源：** Communications Chemistry（DOI 前缀识别）
- **发表时间：** 未记录
- **DOI：** [10.1038/s42004-025-01506-1](https://doi.org/10.1038/s42004-025-01506-1)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白-配体` / `结构预测`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者提出 Folding-Docking-Affinity (FDA) 框架，把蛋白折叠、配体对接和亲和力预测串成可替换组件的流程，并声称可在 kinase 数据集上达到与 SOTA docking-free 方法相当的表现，还能借助 pose augmentation 进一步提升性能。

## 创新边界

`主要创新在系统集成与工作流重组，而非新的 folding、docking 或 affinity backbone。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在缺少高分辨率共晶结构时，如何利用 protein folding 与 molecular docking 生成的三维结合构象，提升 protein-ligand binding affinity prediction 的可用性、泛化性与可解释性。

## 方法

- 折叠protein、docking ligand、interaction GNN回归。

## 数据与基准

- Davis/KIBA，both-new/new-drug/new-protein/sequence identity splits。

## 比较基线

- docking-free DTA和docking-based方法。

## 结果证据

- 与SOTA docking-free相当；为计算预测。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 初始结构/apo-holo差异和docking误差传播。

## 仍未知

- 方法在非 kinase、非酶类靶点上的外推性能未知。
- ColabFold/DiffDock 与评测集的训练集重叠对指标的实际影响仍不清楚。
- 噪声为何有时提升 affinity prediction 的机制尚未解释清楚。

## Pi 结构化证据摘录

- **baseline：** 对照方法主要包括 KronRLS、DeepDTA、GraphDTA、DGraphDTA、MGraphDTA，以及在 kinase 场景下的 KDBNet。
  - 证据：[doi:10.1038/s42004-025-01506-1, p.2]；[doi:10.1038/s42004-025-01506-1, p.8]
- **baseline：** 作者明确指出 KDBNet 借助预定义的 kinase pocket，因此与不依赖固定 pocket 的一般方法并不完全同类。
  - 证据：[doi:10.1038/s42004-025-01506-1, p.2]
- **baseline：** ablation 里还用 GraphDTA 与 MGraphDTA 作为 docking-free baseline 来比较不同 folding/docking 组合。
  - 证据：[doi:10.1038/s42004-025-01506-1, p.3]；[doi:10.1038/s42004-025-01506-1, p.4]
- **data：** 主 benchmark 使用 DAVIS 与 KIBA，并按 both-new、new-drug、new-protein 和 sequence-identity 四种 split 评估。
  - 证据：[doi:10.1038/s42004-025-01506-1, p.2]；[doi:10.1038/s42004-025-01506-1, p.7]
- **data：** 处理后的 DAVIS 包含 226 个 proteins、64 个 ligands 和 14,464 个 binding affinity measurements；KIBA 包含 160 个 proteins、2,086 个 ligands 和 89,957 个 measurements。
  - 证据：[doi:10.1038/s42004-025-01506-1, p.7]
- **data：** ablation 训练数据来自 PDBBind(2016) 的 general 与 refined sets，最终训练集 11,637 对、验证集 975 对；DAVIS 中 102 对具备晶体结构的样本被筛到 53 对 DAVIS-53 测试集。
  - 证据：[doi:10.1038/s42004-025-01506-1, p.7]；[doi:10.1038/s42004-025-01506-1, p.8]
- **data：** 作者还使用 PubChem、PDB/RCSB FASTA/MOL2、AlphaFold/ColabFold 结构，以及 DiffDock 生成的构象作为输入和中间资源。
  - 证据：[doi:10.1038/s42004-025-01506-1, p.7]；[doi:10.1038/s42004-025-01506-1, p.8]
- **declared_resources：** 作者声明 processed data 可从 Zenodo 获取，其中包含 ColabFold-generated apo protein structures、DiffDock-generated ligand poses，以及 ablation 用的三种 complex structures。
  - 证据：[doi:10.1038/s42004-025-01506-1, p.8]
- **declared_resources：** 作者声明 source code 位于 GitHub 仓库 https://github.com/ZhiGroup/FDA。
  - 证据：[doi:10.1038/s42004-025-01506-1, p.8]
- **declared_resources：** 方法实现依赖 ColabFold v1.5.5、DiffDock v1.0、GIGN git hash ef514d3，以及 PDBBind、DAVIS、KIBA、PubChem 和 RCSB/PDB 等外部资源。
  - 证据：[doi:10.1038/s42004-025-01506-1, p.7]；[doi:10.1038/s42004-025-01506-1, p.8]
- **limitations：** 作者承认该方法尚未在非 kinase 蛋白上充分验证，缺少更广泛的多蛋白类型 benchmark。
  - 证据：[doi:10.1038/s42004-025-01506-1, p.6]
- **limitations：** ColabFold 与 DiffDock 训练集可能与 DAVIS/KIBA 存在重叠，论文给出 protein-level 与 pair-level overlap，提示评估结果可能被高估。
  - 证据：[doi:10.1038/s42004-025-01506-1, p.6]
- **limitations：** 计算开销较高，作者报告 protein folding 约 540 秒、docking 约 12 秒，而 affinity prediction 本身仅约 0.01 秒。
  - 证据：[doi:10.1038/s42004-025-01506-1, p.6]；[doi:10.1038/s42004-025-01506-1, p.7]
- **limitations：** 论文还未系统评估不同 selection criteria、以及 AlphaFold、ESMFold、RosettaFold、Vina、TANKBind 等替代 backbone 对结果的影响。
  - 证据：[doi:10.1038/s42004-025-01506-1, p.6]
- **method：** FDA 将 folding、docking 和 affinity prediction 组合成三步流程，并允许各模块替换以适配快速演进的方法生态。
  - 证据：[doi:10.1038/s42004-025-01506-1, p.1]；[doi:10.1038/s42004-025-01506-1, p.2]；[doi:10.1038/s42004-025-01506-1, p.7]
- **method：** 实现上使用 ColabFold 生成 apo protein structure，使用 DiffDock 为每个 protein-ligand pair 采样 10 个 binding poses，再用 GIGN 对 top-ranked pose 做 affinity prediction。
  - 证据：[doi:10.1038/s42004-025-01506-1, p.7]
- **method：** ablation study 训练并比较三种设置：Crystal-Crystal、Crystal-DiffDock 与 ColabFold-DiffDock，然后在 DAVIS-53 上评估。
  - 证据：[doi:10.1038/s42004-025-01506-1, p.3]；[doi:10.1038/s42004-025-01506-1, p.7]；[doi:10.1038/s42004-025-01506-1, p.8]
- **method：** pose augmentation 通过使用 DiffDock 前 5/10 个 poses，或结合 ColabFold 前 2/3 个 protein conformers，扩增训练集。
  - 证据：[doi:10.1038/s42004-025-01506-1, p.4]；[doi:10.1038/s42004-025-01506-1, p.5]
- **results：** 在 both-new split 上，FDA 在 DAVIS 的 Rp 为 0.29、在 KIBA 的 Rp 为 0.51，整体上与 SOTA docking-free 方法相当。
  - 证据：[doi:10.1038/s42004-025-01506-1, p.2]
- **results：** KDBNet 作为 kinase-specific baseline，凭借预定义的 kinase binding pocket，在四种 split 上都强于 FDA 和其他 docking-free 方法。
  - 证据：[doi:10.1038/s42004-025-01506-1, p.2]
- **results：** ablation 中，ColabFold-DiffDock 组合经常优于 Crystal-Crystal 与 Crystal-DiffDock，说明更“接近晶体”的构象并不总带来更好 affinity 预测。
  - 证据：[doi:10.1038/s42004-025-01506-1, p.3]；[doi:10.1038/s42004-025-01506-1, p.4]
- **results：** pose augmentation 在多数场景提升性能，例如 F-5D-A 使 DAVIS 的 Rp 提升 12.86%，KIBA 的 Rp 提升 6.41%；但随着加入更多 poses，收益会饱和甚至回落。
  - 证据：[doi:10.1038/s42004-025-01506-1, p.4]；[doi:10.1038/s42004-025-01506-1, p.5]
- **results：** 作者观察到噪声似乎有助于泛化：ColabFold 生成的 apo 结构和 DiffDock 生成的 poses 虽引入偏差，却可能让模型学到更平滑的 affinity landscape。
  - 证据：[doi:10.1038/s42004-025-01506-1, p.6]

## 页码证据

- [doi:10.1038/s42004-025-01506-1, p.1]
- [doi:10.1038/s42004-025-01506-1, p.2]
- [doi:10.1038/s42004-025-01506-1, p.6]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
