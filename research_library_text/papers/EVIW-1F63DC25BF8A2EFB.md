# Target-aware 3D molecular generation based on guided equivariant diffusion

- **论文 ID：** `EVIW-1F63DC25BF8A2EFB`
- **期刊 / 来源：** Nature Communications（DOI 前缀识别）
- **发表时间：** 未记录
- **DOI：** [10.1038/s41467-025-63245-0](https://doi.org/10.1038/s41467-025-63245-0)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `肽与抗菌肽` / `扩散/生成` / `图与几何学习` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者提出DiffGui，把bond diffusion与property guidance引入target-conditioned E(3)-equivariant diffusion，在PDBbind和CrossDocked上展示更好的几何分布、分子有效性和性质指标，并进一步用于de novo设计、lead optimization和湿实验验证。

## 创新边界

`创新主要在组合式guided diffusion与bond-level建模，核心仍建立在现有pocket-conditioned 3D diffusion范式之上。`。这不是全球首创性检索或独立复现结论。

## 研究问题

给定蛋白口袋，如何直接生成兼具高结合亲和力、合理3D几何结构和可接受drug-like属性的分子，同时减少atom-bond不一致、畸变环和碎片化生成。

## 方法

- SE(3)-equivariant diffusion生成atom types/coordinates，target encoder与guidance steer sampling。

## 数据与基准

- CrossDocked/PDBBind类complexes及virtual screening。

## 比较基线

- Pocket2Mol、TargetDiff、DiffSBDD等。

## 结果证据

- 论文报告3D validity/affinity/target specificity提升；均为计算。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- guidance受评分器/结构质量限制，无实验。

## 仍未知

- GitHub/Zenodo仓库内容未在本次冻结页之外核验，无法确认代码可运行性与复现细节。
- Supplementary materials 只见论文引用，未逐项外部核验。
- 湿实验只覆盖少量化合物，外推到更广靶点和化学空间的程度不明。

## Pi 结构化证据摘录

- **baseline：** 对比基线包括ResGen、PocketFlow、GCDM、TargetDiff、DiffSBDD和PMDM；作者在de novo实验中排除了GCDM，因为其三项Vina分数都较差。
  - 证据：[doi:10.1038/s41467-025-63245-0, p.7]；[doi:10.1038/s41467-025-63245-0, p.8]；[doi:10.1038/s41467-025-63245-0, p.15]
- **baseline：** CrossDocked对比时，作者同时使用PDBbind重训的baselines与原始CrossDocked训练版本，避免把训练数据差异误当作方法优势。
  - 证据：[doi:10.1038/s41467-025-63245-0, p.15]
- **data：** PDBbind 2020版被拆分为17.3K训练、1.8K验证和0.1K测试；CrossDocked仅用于测试，作者不在其上训练DiffGui，因为没有affinity标签。
  - 证据：[doi:10.1038/s41467-025-63245-0, p.15]
- **data：** CrossDocked评估时，作者同时使用PDBbind重训的baselines与原始CrossDocked版本并列对照，以观察泛化能力。
  - 证据：[doi:10.1038/s41467-025-63245-0, p.15]
- **data：** 案例研究覆盖1w51、3ctj、7ew4、8ju6、4b5d、5ni7、5ywy、3l13、6e23和7rpz等靶点。
  - 证据：[doi:10.1038/s41467-025-63245-0, p.8]；[doi:10.1038/s41467-025-63245-0, p.9]；[doi:10.1038/s41467-025-63245-0, p.10]；[doi:10.1038/s41467-025-63245-0, p.11]；[doi:10.1038/s41467-025-63245-0, p.12]
- **declared_resources：** 原始结构数据来自PDBbind、CrossDocked和PDB，论文还附有Source Data与Supplementary Video 1。
  - 证据：[doi:10.1038/s41467-025-63245-0, p.15]
- **declared_resources：** 处理后的数据与源代码公开在GitHub和Zenodo；论文也说明依托ECNU的HPC平台完成计算。
  - 证据：[doi:10.1038/s41467-025-63245-0, p.16]
- **limitations：** 作者自己指出当前diffusion方法仍容易产生七元环，DiffGui也有较高的七元环比例，因此提出fragment-scale diffusion可能更合适。
  - 证据：[doi:10.1038/s41467-025-63245-0, p.7]
- **limitations：** fragment conditioning若不专门重训会有训练-采样不一致问题，作者明确说它不宜直接使用。
  - 证据：[doi:10.1038/s41467-025-63245-0, p.12]
- **limitations：** CrossDocked缺少affinity标签，DiffGui不能在其上训练，因此该数据集结果只反映测试泛化而非充分适配后的性能。
  - 证据：[doi:10.1038/s41467-025-63245-0, p.4]；[doi:10.1038/s41467-025-63245-0, p.15]
- **method：** 前向扩散为atom coordinates使用Gaussian噪声、为atom types和bond types使用吸收式categorical噪声，并对键与原子设定不同噪声日程以减弱atom-bond不一致。
  - 证据：[doi:10.1038/s41467-025-63245-0, p.13]；[doi:10.1038/s41467-025-63245-0, p.14]
- **method：** 反向过程使用SE(3)-equivariant GNN联合预测位置、原子类型与键类型，并保持旋转、平移等变性。
  - 证据：[doi:10.1038/s41467-025-63245-0, p.14]
- **method：** 属性指导采用classifier-free guidance，将affinity、QED、SA、LogP、TPSA作为条件，并通过γ在采样时调节conditional与unconditional分数。
  - 证据：[doi:10.1038/s41467-025-63245-0, p.3]；[doi:10.1038/s41467-025-63245-0, p.14]
- **method：** lead optimization另外定义fragment denoising和fragment conditioning，用于fragment growing、linking和merging。
  - 证据：[doi:10.1038/s41467-025-63245-0, p.11]；[doi:10.1038/s41467-025-63245-0, p.15]
- **results：** 在PDBbind上，DiffGui的bond/angle/dihedral JS divergence整体最优或接近最优，且C-C bond distance与all-atom pairs distance分布更贴近reference ligands。
  - 证据：[doi:10.1038/s41467-025-63245-0, p.3]；[doi:10.1038/s41467-025-63245-0, p.4]；[doi:10.1038/s41467-025-63245-0, p.5]；[doi:10.1038/s41467-025-63245-0, p.6]
- **results：** 在PDBbind上，DiffGui在atom stability、molecular stability、PB-validity、RDKit-validity、interaction similarity，以及Vina Score/Vina Min/Vina Dock/QED上整体优于基线。
  - 证据：[doi:10.1038/s41467-025-63245-0, p.7]
- **results：** 湿实验中，RSK4的Compound 1/2分别达到约215.0 nM和111.1 nM，DHODH的Compound 3/4分别把IC50从8.02 μM降到4.27 μM、从32.20 nM降到10.45 nM。
  - 证据：[doi:10.1038/s41467-025-63245-0, p.10]；[doi:10.1038/s41467-025-63245-0, p.12]

## 页码证据

- [doi:10.1038/s41467-025-63245-0, p.1]
- [doi:10.1038/s41467-025-63245-0, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
