# Equivariant diffusion for structure-based de novo ligand generation with latent-conditioning

- **论文 ID：** `EVIW-7CF69B95D1E8B3D4`
- **期刊 / 来源：** Journal of Cheminformatics（DOI 前缀识别）
- **发表时间：** 未记录
- **DOI：** [10.1186/s13321-025-01028-x](https://doi.org/10.1186/s13321-025-01028-x)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白-配体` / `扩散/生成` / `图与几何学习` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

提出 PoLiGenX：在 EQGAT-diff 上加入由参考配体编码得到的 latent conditioning，并结合 AdaLN、MMD 正则与可选 SA importance sampling，实现可控的 structure-based de novo ligand generation。

## 创新边界

`主要新意是把 seed ligand latent 注入 pocket-conditioned diffusion，并加入 SA guidance；它更像对既有 EQGAT-diff / latent-conditioned 框架的控制增强，而不是全新口袋数据集或湿实验发现。`。这不是全球首创性检索或独立复现结论。

## 研究问题

如何在给定蛋白口袋的前提下，引入参考配体的 latent 约束，使 de novo ligand generation 同时保留种子分子的形状/化学特征、提升口袋适配性，并维持可成药性与构象质量。

## 方法

- SE(3) diffusion、latent property/shape conditioning。

## 数据与基准

- CrossDocked/PDBBind。

## 比较基线

- TargetDiff/Pocket2Mol等。

## 结果证据

- 论文报告validity/affinity/diversity；为计算。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- score proxy、无合成/实验。

## 仍未知

- 未见湿实验或 prospective binding assay，因此真实实验可迁移性仍未知。
- latent control α 与 SA-guidance 的完整消融和超参数扫描未在正文完全展开。
- 外部 prior-art 仅以参考文献形式出现，冻结材料中没有独立的先验事实核验。

## Pi 结构化证据摘录

- **baseline：** EQGAT-diff 是本文最主要的无条件 baseline，用来对照 shape/chemical similarity 的增益。
  - 证据：[doi:10.1186/s13321-025-01028-x, p.5]
- **baseline：** DiffSBDD 和 TargetDiff 是本文的主要 pose-quality baseline，用于比较 Vina、strain energy、clash count 与 H-bond recovery。
  - 证据：[doi:10.1186/s13321-025-01028-x, p.7]；[doi:10.1186/s13321-025-01028-x, p.8]
- **baseline：** SQUID 和 ShapeMol 被用作 shape-conditioned prior art，但它们不引入 protein receptor 条件，因此与 PoLiGenX 的定位不同。
  - 证据：[doi:10.1186/s13321-025-01028-x, p.2]
- **data：** 实验基于 CrossDocked2020，沿用 prior splits；测试时在 100 个口袋上评估，并对每个 target 采样 100 个 ligand。
  - 证据：[doi:10.1186/s13321-025-01028-x, p.5]
- **data：** 口袋通过 5Å cutoff 构建 pocket-ligand complex，ligand 图含 fully-connected edges 与 bond adjacency，口袋边来自 radius graph。
  - 证据：[doi:10.1186/s13321-025-01028-x, p.3]；[doi:10.1186/s13321-025-01028-x, p.4]
- **data：** 训练在 8 张 NVIDIA A100 40GB 上进行 300 epochs，batch size 每卡 8，优化器为 AdamW，学习率 2e-4、weight decay 1e-12，并做梯度裁剪。
  - 证据：[doi:10.1186/s13321-025-01028-x, p.4]
- **data：** 评估指标包括 RDKit ECFP4 Tanimoto、Gaussian shape overlap、QuickVina2/Autodock Vina、RDKit SA-score、Lipinski、PoseCheck hydrogen-bond recovery 等。
  - 证据：[doi:10.1186/s13321-025-01028-x, p.3]；[doi:10.1186/s13321-025-01028-x, p.5]；[doi:10.1186/s13321-025-01028-x, p.6]；[doi:10.1186/s13321-025-01028-x, p.7]；[doi:10.1186/s13321-025-01028-x, p.8]
- **declared_resources：** 论文使用 CrossDocked2020 及其 processed version，数据下载路径指向 Pocket2Mol repo，说明作者依赖的是既有数据资源而非新发布 benchmark。
  - 证据：[doi:10.1186/s13321-025-01028-x, p.11]；[doi:10.1186/s13321-025-01028-x, p.5]
- **declared_resources：** 代码已公开在 pfizer-open-source/e3moldiffusion/tree/poligenX，训练算力为 8×A100 40GB。
  - 证据：[doi:10.1186/s13321-025-01028-x, p.11]；[doi:10.1186/s13321-025-01028-x, p.4]
- **limitations：** 作者明确把动态蛋白构象支持列为未来工作，说明当前方法仍主要面向相对静态的 binding site。
  - 证据：[doi:10.1186/s13321-025-01028-x, p.8]
- **limitations：** 作者还提出可用更先进的 sampling techniques 去发现稀有 scaffold，暗示当前对稀有化学空间的探索仍有不足。
  - 证据：[doi:10.1186/s13321-025-01028-x, p.8]
- **limitations：** SA-score 在正文叙述和表格箭头呈现上略有不一致，因而可合成性的方向性解读需要谨慎。
  - 证据：[doi:10.1186/s13321-025-01028-x, p.6]；[doi:10.1186/s13321-025-01028-x, p.7]
- **method：** PoLiGenX 以蛋白口袋 P 为条件，在 EQGAT-diff 框架上额外引入参考配体 latent z，以同时约束口袋适配与种子相似性。
  - 证据：[doi:10.1186/s13321-025-01028-x, p.1]；[doi:10.1186/s13321-025-01028-x, p.3]
- **method：** 参考配体由 8 层 G-invariant EQGAT encoder 编成 128 维 latent，并通过 AdaLN 注入扩散主干；控制系数 α 可调节 latent 影响，α 趋近 0 时退化为无条件模型。
  - 证据：[doi:10.1186/s13321-025-01028-x, p.4]；[doi:10.1186/s13321-025-01028-x, p.8]
- **method：** 训练将连续坐标视为 Gaussian diffusion、原子/键离散类型视为 categorical diffusion，并结合加权重建损失、MMD latent 正则与逐步 reverse-KL 近似优化。
  - 证据：[doi:10.1186/s13321-025-01028-x, p.3]；[doi:10.1186/s13321-025-01028-x, p.4]；[doi:10.1186/s13321-025-01028-x, p.9]；[doi:10.1186/s13321-025-01028-x, p.10]
- **method：** 作者还引入 SA surrogate 与 importance sampling，把 synthetic accessibility 纳入采样引导。
  - 证据：[doi:10.1186/s13321-025-01028-x, p.6]
- **results：** PoLiGenX 的 mean shape similarity 达到 0.87，chemical similarity 为 0.33，显著高于 EQGAT-diff 的 0.64 和 0.12。
  - 证据：[doi:10.1186/s13321-025-01028-x, p.5]
- **results：** UMAP 可视化显示 latent embeddings 按受体形成相对清晰的簇，提示编码器捕获了 ligand-receptor context。
  - 证据：[doi:10.1186/s13321-025-01028-x, p.5]
- **results：** Docking 结果显示 PoLiGenX 的 mean QVina2 score 为 −6.88±2.12，top 10% 为 −7.77±2.61，整体与测试集水平接近。
  - 证据：[doi:10.1186/s13321-025-01028-x, p.5]；[doi:10.1186/s13321-025-01028-x, p.7]
- **results：** 与 DiffSBDD 和 TargetDiff 相比，PoLiGenX 的 raw poses 在 strain energy 和 clash count 上明显更优，并保持较好的 minimized Vina score。
  - 证据：[doi:10.1186/s13321-025-01028-x, p.7]；[doi:10.1186/s13321-025-01028-x, p.8]
- **results：** 生成分子在 Lipinski 指标上优于测试集，且 QED/logP 等总体保持相近水平，作者据此主张其 drug-likeness 更好。
  - 证据：[doi:10.1186/s13321-025-01028-x, p.7]
- **results：** PoLiGenX 的 H-bond recovery 达到 47.94% 和 50.12%，高于 DiffSBDD 的 30.84% 和 TargetDiff 的 27.5%；SA-guidance 版本还把作者报告的 mean SA 提到 0.74。
  - 证据：[doi:10.1186/s13321-025-01028-x, p.6]；[doi:10.1186/s13321-025-01028-x, p.8]；[doi:10.1186/s13321-025-01028-x, p.7]

## 页码证据

- [doi:10.1186/s13321-025-01028-x, p.1]
- [doi:10.1186/s13321-025-01028-x, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
