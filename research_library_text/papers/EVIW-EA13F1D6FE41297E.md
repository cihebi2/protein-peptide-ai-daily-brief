# Hybrid protein-ligand binding residue prediction with protein language models: does the structure matter?

- **论文 ID：** `EVIW-EA13F1D6FE41297E`
- **期刊 / 来源：** Bioinformatics
- **发表时间：** 2025 Jul 31
- **DOI：** [10.1093/bioinformatics/btaf431](https://doi.org/10.1093/bioinformatics/btaf431)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白-配体` / `语言模型`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

提出一个残基级混合框架：先用 pLM 产生节点表示，再把蛋白 3D 结构转为图并用 GCN/GAT 做 binding residue 预测；同时系统比较不同 pLM、cutoff 和图结构对性能的影响。

## 创新边界

`新意主要在 pLM+GNN 融合与结构增益分析，不在候选分子生成、对接或 wet-lab 发现。`。这不是全球首创性检索或独立复现结论。

## 研究问题

如何把蛋白语言模型（pLM）与蛋白三维结构融合起来，提升 protein-ligand binding residue prediction 的准确率，并量化结构信息到底带来多大增益。

## 方法

- 以实验蛋白结构构建残基图，节点特征分别使用AAIndex、SeqVec、ProtBERT、ESM-2和ProtT5；GAT8经五折交叉验证与只用序列的分类头比较。

## 数据与基准

- 覆盖多种小分子/离子/辅因子结合残基的基准数据集；拆分、预训练模型和权重在Zenodo发布。

## 比较基线

- 序列分类基线、GCN、GAT变体、AAIndex/SeqVec/ProtBERT/ESM-2/ProtT5以及若干既有位点预测器。

## 结果证据

- GAT8对多数配体在绝对性能上超过序列基线，ProtT5-GAT8在所有配体的MCC和多数ROC-AUC上最好；但pLM越强，显式结构的相对增益越小，部分复杂架构仍略优。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 依赖实验或可靠预测结构；结构增益随pLM复杂度下降，未证明在低质量结构、构象变化或新化学类型上稳定。

## 仍未知

- 公开的 GitHub/Zenodo 资源在本次审阅中未实际复现，代码与数据的可重现性未知。
- 论文未给出完整的运行时、显存占用或部署成本对比，工程代价仍不清楚。
- 对 attention 热图的机制解释仍是定性观察，是否能稳定解释因果贡献未知。
- 多链 binding pocket 和跨链相互作用未被纳入主实验，外推到该场景的效果未知。
- global novelty 未做独立 prior-art 验证，只能依据冻结稿内证据判断。

## Pi 结构化证据摘录

- **baseline：** 论文把单层 512-unit、dropout 0.1 的 MLP 作为 sequence baseline；RF 和 SVM 只用于辅助比较和超参筛选。
  - 证据：[doi:10.1093/bioinformatics/btaf431, p.5]；[doi:10.1093/bioinformatics/btaf431, p.6]
- **baseline：** Yu benchmark 的外部 sequence baselines 采用了 TargetS、EC-RUS、SXGBsite 的最佳已发表版本，作为主比较对象。
  - 证据：[doi:10.1093/bioinformatics/btaf431, p.8]；[doi:10.1093/bioinformatics/btaf431, p.9]
- **baseline：** 在 nucleic-acid 场景中，作者还把自己的方法与 GraphBind、GraphSite、GeoBind、EquiPNAS 作为参考基线做了横向比较。
  - 证据：[doi:10.1093/bioinformatics/btaf431, p.8]
- **data：** 主数据集是 Yu benchmark，覆盖 12 类 ligand：5 个 nucleotide、DNA、HEME 和 5 种 ion；作者从 BioLip/PDB 重建对应 3D 结构，并说明 ProtT5 只在训练集中缺失了 31 条序列的图。
  - 证据：[doi:10.1093/bioinformatics/btaf431, p.4]；[doi:10.1093/bioinformatics/btaf431, p.5]
- **data：** PDBBind 部分使用 2020 refined set 的 5316 个复合物，过滤到单链口袋后得到 3465 条标注链，并最终构建 2516 个 single-chain complexes，再做 5 组 train/validation/test 切分。
  - 证据：[doi:10.1093/bioinformatics/btaf431, p.11]；[doi:10.1093/bioinformatics/btaf431, p.12]
- **data：** 为对照 nucleic-acid binding 文献，作者还引用并比较了 GraphBind、GraphSite、GeoBind、EquiPNAS 所用的公开基准与结果。
  - 证据：[doi:10.1093/bioinformatics/btaf431, p.8]
- **declared_resources：** 数据集、预训练模型和源代码都公开在 Zenodo；源代码同时提供了 GitHub 仓库。
  - 证据：[doi:10.1093/bioinformatics/btaf431, p.1]；[doi:10.1093/bioinformatics/btaf431, p.12]
- **declared_resources：** 论文声明使用了 e-INFRA CZ 与 ELIXIR CZ 计算资源，并注明 Czech Science Foundation 资助。
  - 证据：[doi:10.1093/bioinformatics/btaf431, p.12]
- **limitations：** 蛋白图只是对 3D 结构的近似，依赖 Cα cutoff，不能直接表达完整几何；作者也承认预测结构的小误差可能影响 docking，但未必严重影响残基预测。
  - 证据：[doi:10.1093/bioinformatics/btaf431, p.4]；[doi:10.1093/bioinformatics/btaf431, p.12]
- **limitations：** cutoff 选择没有一致最优趋势，8 Å 只是经验上的轻量折中，而不是由理论或独立验证唯一确定的最优值。
  - 证据：[doi:10.1093/bioinformatics/btaf431, p.7]
- **limitations：** PDBBind 实验只保留单链口袋，跨链 binding pocket 被排除，因此对多链复合物的泛化能力仍未知。
  - 证据：[doi:10.1093/bioinformatics/btaf431, p.11]
- **limitations：** 作者对 attention 的解释主要停留在可视化层面，并明确说需要更 quantitative 的分析才能得出更强结论。
  - 证据：[doi:10.1093/bioinformatics/btaf431, p.7]
- **limitations：** ProtT5 embeddings 在部分训练序列上生成失败，导致 31 条 protein graphs 缺失；作者声称不影响测试结果，但这仍是数据处理风险。
  - 证据：[doi:10.1093/bioinformatics/btaf431, p.5]
- **method：** 整体流水线是：pLM 为每个残基生成 embedding，蛋白 3D 结构被转成 residue graph，随后由 GCN/GAT 输出逐残基的 binding probability；sequence baseline 仅使用 embedding 加 MLP。
  - 证据：[doi:10.1093/bioinformatics/btaf431, p.3]；[doi:10.1093/bioinformatics/btaf431, p.4]
- **method：** 图构建采用 Cα 距离阈值连边，测试了 4 Å、6 Å、8 Å、10 Å，并额外用多数投票做 cutoff ensemble；GNN 主体比较的是 GCN 与 GAT。
  - 证据：[doi:10.1093/bioinformatics/btaf431, p.4]；[doi:10.1093/bioinformatics/btaf431, p.6]；[doi:10.1093/bioinformatics/btaf431, p.7]
- **method：** 节点特征来自 ProtBERT-BFD、ProtT5-XL-UniRef50、SeqVec、ESM-2 的最后一层 encoder embedding；AAIndex 的 566 维特征被用作 context-independent 对照。
  - 证据：[doi:10.1093/bioinformatics/btaf431, p.3]；[doi:10.1093/bioinformatics/btaf431, p.4]
- **method：** 训练与实现使用 DGL-LifeSci 和 PyTorch，损失函数为 weighted binary cross-entropy，优化器为 AdamW，训练 2000 epochs、batch size 32，并以 validation MCC 做早停。
  - 证据：[doi:10.1093/bioinformatics/btaf431, p.5]；[doi:10.1093/bioinformatics/btaf431, p.6]
- **method：** 序列基线先比较 MLP、RF、SVM，并在 ADP 的 5-fold CV 上选择单层 512-unit、dropout 0.1 的 MLP 作为后续主基线。
  - 证据：[doi:10.1093/bioinformatics/btaf431, p.5]；[doi:10.1093/bioinformatics/btaf431, p.6]
- **results：** 增加 GCN 层数通常没有收益，很多 ligand 上性能持平或下降，因此作者采用单层 GNN，并用 oversmoothing 作为解释。
  - 证据：[doi:10.1093/bioinformatics/btaf431, p.6]
- **results：** 在 cutoff 比较中，GAT8 作为轻量代理与 cutoff ensemble 接近且通常优于 GCN8，平均 MCC 也最好，因此被选为后续主模型。
  - 证据：[doi:10.1093/bioinformatics/btaf431, p.7]
- **results：** 在 Yu benchmark 上，GAT8+ProtT5 的平均 MCC 为 0.60，高于 sequence baseline 的 0.55，并在 MCC 上超过 TargetS、EC-RUS、SXGBsite 对所有 ligand；ROC-AUC 也在多数 ligand 上领先。
  - 证据：[doi:10.1093/bioinformatics/btaf431, p.8]；[doi:10.1093/bioinformatics/btaf431, p.9]；[doi:10.1093/bioinformatics/btaf431, p.10]
- **results：** 结构增益随 embedding 复杂度上升而减弱：AAIndex、SeqVec、ProtBERT 的相对提升更大，而 ProtT5 与 ESM-2 的相对提升更小；多数 t-test 结果显著。
  - 证据：[doi:10.1093/bioinformatics/btaf431, p.9]；[doi:10.1093/bioinformatics/btaf431, p.10]
- **results：** 用随机图替代原始图后，多数 embedding 的 MCC 下降，说明真实的 graph topology 确实提供了正向结构信息，而不只是随机信息传播。
  - 证据：[doi:10.1093/bioinformatics/btaf431, p.10]；[doi:10.1093/bioinformatics/btaf431, p.11]
- **results：** 在更严格控制序列与 ligand 相似性的 PDBBind 切分上，SeqVec 仍有显著结构增益，但 ESM-2 的增益接近于零且不显著，说明“结构增益随 pLM 复杂度下降”的趋势可复现。
  - 证据：[doi:10.1093/bioinformatics/btaf431, p.11]；[doi:10.1093/bioinformatics/btaf431, p.12]

## 页码证据

- [doi:10.1093/bioinformatics/btaf431, p.12]
- [doi:10.1093/bioinformatics/btaf431, p.1]
- [doi:10.1093/bioinformatics/btaf431, p.4]
- [doi:10.1093/bioinformatics/btaf431, p.7]
- [doi:10.1093/bioinformatics/btaf431, p.8]
- [doi:10.1093/bioinformatics/btaf431, p.9]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
