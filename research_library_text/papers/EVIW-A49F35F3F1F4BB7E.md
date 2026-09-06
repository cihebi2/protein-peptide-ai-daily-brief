# Token-Mol 1.0: tokenized drug design with large language models

- **论文 ID：** `EVIW-A49F35F3F1F4BB7E`
- **期刊 / 来源：** Nature Communications（DOI 前缀识别）
- **发表时间：** 未记录
- **DOI：** [10.1038/s41467-025-59628-y](https://doi.org/10.1038/s41467-025-59628-y)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `语言模型` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

论文声称提出 Token-Mol 1.0：一个 token-only 的 3D drug design 预训练语言模型，把 SMILES、torsion angle、回归数值和 pocket 条件都转成 token 处理，并结合 random causal masking、GCE loss、pocket encoder/fusion block 与 RL，在构象生成、性质预测和 pocket-based 分子生成上取得更好结果。

## 创新边界

`边界在于把 2D/3D 分子信息与数值回归统一到 token-only autoregressive 框架，目标是可与通用 LLM 兼容的 drug design；它不是湿实验新药发现平台，也不证明全任务全靶点的绝对最优。`。这不是全球首创性检索或独立复现结论。

## 研究问题

现有化学语言模型很难直接处理 3D 结构信息，而图模型虽然能利用几何信息，却更偏向性质预测、生成能力和通用 LLM 兼容性都不够理想；作者要解决的是如何用统一的 token-only 框架同时覆盖 3D 分子表示、回归任务和靶点导向分子生成。

## 方法

- causal transformer decoder多任务预训练，RL进一步优化affinity/drug-likeness。

## 数据与基准

- 大规模分子与多性质/构象/设计benchmark。

## 比较基线

- Uni-Mol/分子LLM及任务模型。

## 结果证据

- 构象任务提高>10%/20%，性质相对token-only提高30%；real-world validation仍为计算/回顾性。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- token discretization和property/RL reward偏差，无合成验证。

## 仍未知

- Supplementary Information 与 Source Data 未逐项展开，部分定量细节只能依据正文摘要式描述。
- GitHub/Zenodo 链接已声明，但本次冻结页未核验仓库 commit、可运行性或训练脚本状态。
- 真实靶点评估仍以 docking 和性质过滤为主，缺少湿实验层面的命中确认。

## Pi 结构化证据摘录

- **baseline：** conformation generation 的对比基线包括 CGVAE、GraphDG、CGCF、ConfVAE、GeoMol、ConfGF、GeoDiff 和 Tora3D。
  - 证据：[doi:10.1038/s41467-025-59628-y, p.4]
- **baseline：** property prediction 的对比对象包括 XGBoost、K-Bert、Chemprop、GEM、MapLight+GNN，以及 token-only 的 RT。
  - 证据：[doi:10.1038/s41467-025-59628-y, p.5]；[doi:10.1038/s41467-025-59628-y, p.6]
- **baseline：** pocket-based generation 的主要基线是 GraphBP、Pocket2Mol、TargetDiff 和 TamGen；RL 评估还额外使用 Glide 与 Surflex-dock。
  - 证据：[doi:10.1038/s41467-025-59628-y, p.5]；[doi:10.1038/s41467-025-59628-y, p.9]；[doi:10.1038/s41467-025-59628-y, p.11]；[doi:10.1038/s41467-025-59628-y, p.12]
- **data：** 预训练数据来自 GEOM，作者清洗后得到约 8,452,080 条 conformer entry 用于 pretraining。
  - 证据：[doi:10.1038/s41467-025-59628-y, p.15]
- **data：** pocket-based molecular generation 使用 CrossDock2020 的 2000 万+ pose pairs、近 2 万个 protein-ligand complexes，并按 sequence similarity <40% 划分训练/测试，同时剔除 RMSD >2 Å 和缺少 torsion angle 的配体。
  - 证据：[doi:10.1038/s41467-025-59628-y, p.15]
- **data：** 真实靶点结构来自 RCSB PDB，参考配体来自 ChEMBL；活性分子以 Kd/Ki <1000 nM 为主，必要时补入 IC50 <1000 nM。
  - 证据：[doi:10.1038/s41467-025-59628-y, p.15]
- **data：** 性质预测共使用 12 个数据集，来自 MolecularNet 与 TDC，覆盖 6 个分类、3 个回归和 3 个 ADMET 任务。
  - 证据：[doi:10.1038/s41467-025-59628-y, p.16]
- **declared_resources：** 主要资源包括 GEOM、CrossDock2020、MoleculeNet、TDC、RCSB PDB 和 ChEMBL；论文还使用了预训练的 pocket encoder。
  - 证据：[doi:10.1038/s41467-025-59628-y, p.14]；[doi:10.1038/s41467-025-59628-y, p.15]；[doi:10.1038/s41467-025-59628-y, p.16]
- **declared_resources：** 论文正文声明代码公开在 GitHub 与 Zenodo，便于复现，但冻结页未提供仓库级执行验证。
  - 证据：[doi:10.1038/s41467-025-59628-y, p.16]
- **limitations：** 在 test set I 上 Token-Mol 的 Recall 不是第一，且随着 rotatable bonds 增多所有指标都会下降；作者还指出稀有 torsion angles 更难学，JSD 可能出现较大离群值。
  - 证据：[doi:10.1038/s41467-025-59628-y, p.4]；[doi:10.1038/s41467-025-59628-y, p.8]
- **limitations：** 尽管加入 GCE，Token-Mol 在 regression 任务上仍不如部分 GNN 方案，作者明确把 multi-task prediction 和 data augmentation 作为后续改进方向。
  - 证据：[doi:10.1038/s41467-025-59628-y, p.4]；[doi:10.1038/s41467-025-59628-y, p.6]
- **limitations：** pocket-based generation 的 binding pose 和 target-specific interactions 仍受 docking 算法与 pocket 使用方式限制，文中也承认并未完全复现关键相互作用。
  - 证据：[doi:10.1038/s41467-025-59628-y, p.10]；[doi:10.1038/s41467-025-59628-y, p.11]
- **limitations：** 论文只评估了 3 类代表性 downstream tasks，预训练数据多样性有限，且模型参数量比一些专家模型更大。
  - 证据：[doi:10.1038/s41467-025-59628-y, p.13]
- **method：** Token-Mol 的核心骨架是 12 层 Transformer decoder，采用 autoregressive 生成，并把 SMILES 与 torsion angle token 化来表达 2D/3D 分子结构。
  - 证据：[doi:10.1038/s41467-025-59628-y, p.2]；[doi:10.1038/s41467-025-59628-y, p.13]
- **method：** 作者把回归任务改写为 Gaussian cross-entropy (GCE) 加权的 token 预测，使模型对连续数值及其邻近关系更敏感。
  - 证据：[doi:10.1038/s41467-025-59628-y, p.13]；[doi:10.1038/s41467-025-59628-y, p.14]
- **method：** 训练阶段使用 random causal masking 做 in-filling；在 pocket-based generation 中加入冻结的 pocket encoder 和 multi-head condition-attention fusion block；优化阶段再用 REINVENT 式 RL 调整 Vina 与 QED 约束。
  - 证据：[doi:10.1038/s41467-025-59628-y, p.3]；[doi:10.1038/s41467-025-59628-y, p.14]；[doi:10.1038/s41467-025-59628-y, p.15]
- **results：** 在 molecular conformation generation 上，Token-Mol 在 test set II 的 COV-P 和 MAT-P 都是最优；在 test set I 上它的 COV-P 优于 Tora3D，但 Recall 略低于 GeoDiff 和 Tora3D。
  - 证据：[doi:10.1038/s41467-025-59628-y, p.4]
- **results：** 在 molecular property prediction 上，Token-Mol 的分类任务平均 ROC-AUC 为 0.829，回归任务相对 RT 平均提升约 30%，但作者也承认它在部分 regression 场景仍落后于 GNN 方法。
  - 证据：[doi:10.1038/s41467-025-59628-y, p.5]；[doi:10.1038/s41467-025-59628-y, p.6]
- **results：** 在 pocket-based generation 上，Token-Mol 生成分子中约 47.2% 的 Vina score 优于原始配体，并在 QED 与 SA 上比 graph-based baseline 高约 5%~10%；其生成速度相对几何深度学习模型约快 35 倍。
  - 证据：[doi:10.1038/s41467-025-59628-y, p.6]；[doi:10.1038/s41467-025-59628-y, p.7]；[doi:10.1038/s41467-025-59628-y, p.8]
- **results：** 在 8 个真实靶点上，Token-Mol 约有 20% 的分子同时满足 Vina/QED/SA 标准，且 6/8 靶点达到最优或次优比例。
  - 证据：[doi:10.1038/s41467-025-59628-y, p.9]
- **results：** 引入 RL 后，在 CDK2 与 ARA2A 上 Vina score 从约 -8 优化到约 -9.5，QED 先升后收敛，SA 始终低于 5。
  - 证据：[doi:10.1038/s41467-025-59628-y, p.11]；[doi:10.1038/s41467-025-59628-y, p.12]

## 页码证据

- [doi:10.1038/s41467-025-59628-y, p.1]
- [doi:10.1038/s41467-025-59628-y, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
