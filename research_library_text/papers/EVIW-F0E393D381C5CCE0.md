# SpatialPPIv2: Enhancing protein-protein interaction prediction through graph neural networks with protein language models

- **论文 ID：** `EVIW-F0E393D381C5CCE0`
- **期刊 / 来源：** Comput Struct Biotechnol J
- **发表时间：** 2025 Jan 23
- **DOI：** [10.1016/j.csbj.2025.01.022](https://doi.org/10.1016/j.csbj.2025.01.022)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `语言模型` / `图与几何学习`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者提出 SpatialPPIv2：用蛋白语言模型生成残基表示，再用图注意力网络建模蛋白内外残基关系，从而在不再依赖 AlphaFold Multimer 复杂体预测的情况下完成 PPI 预测，并在多种基线与预测结构输入上取得更好表现。

## 创新边界

`创新点主要在 PPI 二分类与鲁棒推断，不是蛋白设计、生成或优化；核心是序列表征与图注意力融合，以及摆脱对既有复杂体预测流程的依赖。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在缺乏实验结构或高质量复杂体信息时，如何利用蛋白序列与粗粒化结构图，稳健判断蛋白对是否相互作用，并兼顾大规模筛选效率。

## 方法

- 单体残基图经GAT编码，语言模型嵌入提供序列语义，两个蛋白表示密集融合后做二分类；比较实验、AF2/AF3/ESMFold结构输入。

## 数据与基准

- PINDER训练集初始含1,560,682个二聚体/42,220簇，负样本来自随机配对、Negatome 2.0和PDB-stringent，并做聚类拆分。

## 比较基线

- SpatialPPI、FoldDock、Struct2Graph、GNN-PPI、pDockQ、接触残基数/pLDDT以及one-hot/多种pLM消融。

## 结果证据

- 论文报告随机负样本测试准确率约0.940，实验注释非互作对的负类准确率从0.957降至0.878；模型在预测结构输入下仍稳健，结果均为计算分类。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 性能受机器学习训练分布和负样本定义影响；相似蛋白更容易预测，实验非互作负集上性能下降；大数据训练和预嵌入仍耗时。

## 仍未知

- 公开仓库是否可直接复现实验指标，冻结证据未核验。
- 跨家族、跨物种或完全未见蛋白对上的泛化能力未独立验证。
- 更长序列或更大复合体上的计算开销上限与稳定性未明确。

## Pi 结构化证据摘录

- **baseline：** 论文比较了 sequence-only 的 Topsy-Turvy 和 D-script，以及 structure-based 的 Struct2Graph、GNN-PPI、FoldDock 与 SpatialPPI。
  - 证据：[doi:10.1016/j.csbj.2025.01.022, p.5]；[doi:10.1016/j.csbj.2025.01.022, p.7]；[doi:10.1016/j.csbj.2025.01.022, p.8]
- **baseline：** 作者还用了 one-hot 编码、平均 interface pLDDT、接触残基数，以及 pDockQ 阈值作为简单基线。
  - 证据：[doi:10.1016/j.csbj.2025.01.022, p.5]；[doi:10.1016/j.csbj.2025.01.022, p.7]
- **baseline：** 文中指出 FoldDock 和 SpatialPPI 依赖结构预测程序，而 Topsy-Turvy、D-script、Struct2Graph、GNN-PPI 仍有各自的预处理或可用性限制。
  - 证据：[doi:10.1016/j.csbj.2025.01.022, p.7]；[doi:10.1016/j.csbj.2025.01.022, p.8]
- **data：** PINDER 是主要正例来源，原始训练池包含 1,560,682 个 dimers 和 42,220 个 clusters，作者进一步筛成 583,516 个训练正例、1,081 个验证正例和 600 个测试正例。
  - 证据：[doi:10.1016/j.csbj.2025.01.022, p.3]
- **data：** 训练与验证负例通过随机采样生成，并用 BioGRID 交叉检查以排除已知可能相互作用的蛋白对。
  - 证据：[doi:10.1016/j.csbj.2025.01.022, p.3]
- **data：** 测试负例来自 Negatome 2.0 的 manual stringent 168 对和 PDB stringent 432 对。
  - 证据：[doi:10.1016/j.csbj.2025.01.022, p.3]
- **data：** 在无结构评测中，作者还用 AlphaFold3、AlphaFold2.3.1 和 ESMFold_v1 为测试蛋白对预测复合体。
  - 证据：[doi:10.1016/j.csbj.2025.01.022, p.5]
- **declared_resources：** 论文公开了项目仓库 `https://github.com/ohuelab/SpatialPPIv2`，并声明计算实验运行在 TSUBAME 4.0 上。
  - 证据：[doi:10.1016/j.csbj.2025.01.022, p.1]；[doi:10.1016/j.csbj.2025.01.022, p.10]
- **declared_resources：** 数据与对比资源包括 PINDER、Negatome 2.0、BioGRID、RCSB PDB、AlphaFold Database，以及 AlphaFold3、AlphaFold2.3.1、ESMFold_v1。
  - 证据：[doi:10.1016/j.csbj.2025.01.022, p.2]；[doi:10.1016/j.csbj.2025.01.022, p.3]；[doi:10.1016/j.csbj.2025.01.022, p.5]
- **declared_resources：** Funding 来自 JST FOREST、JSPS KAKENHI 和 AMED BINDS。
  - 证据：[doi:10.1016/j.csbj.2025.01.022, p.10]
- **limitations：** 作者承认，若有相近参考序列，基于 similarity 的方法有时可能比机器学习更占优，而神经网络错误也较难解释。
  - 证据：[doi:10.1016/j.csbj.2025.01.022, p.9]
- **limitations：** 实验负例稀缺且带有选择性，Negatome 类负例比随机负例更难判别，因此评测难度本身较高。
  - 证据：[doi:10.1016/j.csbj.2025.01.022, p.3]；[doi:10.1016/j.csbj.2025.01.022, p.8]
- **limitations：** 当结构预测器给出不佳复合体时，性能会略降，文中也观察到 ESMFold_v1 的结果弱于 AlphaFold3 和 AlphaFold2。
  - 证据：[doi:10.1016/j.csbj.2025.01.022, p.6]；[doi:10.1016/j.csbj.2025.01.022, p.7]
- **method：** 将每个残基视为图节点，用 ProtT5、ProtBert 或 ESM-2 产生节点特征，并用同一蛋白内 Cα 距离小于 8 Å 的残基连边。
  - 证据：[doi:10.1016/j.csbj.2025.01.022, p.3]；[doi:10.1016/j.csbj.2025.01.022, p.4]
- **method：** 在两个蛋白之间加入残基全连接的虚拟边，以增强跨蛋白 message passing，并用 4 层 GAT、每层 4 个 attention heads 更新图表示。
  - 证据：[doi:10.1016/j.csbj.2025.01.022, p.4]
- **method：** 将语言模型输出与 GAT 输出做 chain mean pooling 后拼接，再接全连接层输出相互作用概率。
  - 证据：[doi:10.1016/j.csbj.2025.01.022, p.4]
- **method：** 作者还构造了 ESM-2 + ac 版本，利用 ESM-2 的 attention contact prediction 在无结构时近似生成接触图。
  - 证据：[doi:10.1016/j.csbj.2025.01.022, p.4]
- **method：** 训练采用 binary cross-entropy、Adam，学习率 0.0001，训练 10 个 epoch，batch size 为 8，并用 gradient accumulation 将有效 batch 扩到 32。
  - 证据：[doi:10.1016/j.csbj.2025.01.022, p.4]
- **results：** 在残基嵌入对比中，ProtT5 最好，ACC 为 0.910、AP 为 0.973、AUROC 为 0.972；ESM-2 接近，one-hot 明显更差。
  - 证据：[doi:10.1016/j.csbj.2025.01.022, p.6]
- **results：** 与 Topsy-Turvy、D-script、Struct2Graph、GNN-PPI、FoldDock 相比，SpatialPPIv2 取得最高 AP 0.973 和 AUROC 0.972。
  - 证据：[doi:10.1016/j.csbj.2025.01.022, p.7]；[doi:10.1016/j.csbj.2025.01.022, p.8]
- **results：** 在 AlphaFold3、AlphaFold2 和 ESMFold_v1 预测结构上，SpatialPPIv2 仍能稳定区分正负样本，并优于仅用 pLDDT 或接触残基数的简单基线。
  - 证据：[doi:10.1016/j.csbj.2025.01.022, p.6]；[doi:10.1016/j.csbj.2025.01.022, p.7]
- **results：** 在 100 万对级别的交换评估中，模型对负例、正例、同/相似蛋白正例和不同蛋白正例的 accuracy 分别达到 0.957、0.942、0.997 和 0.906。
  - 证据：[doi:10.1016/j.csbj.2025.01.022, p.8]
- **results：** 注意力可视化显示，正负样本在跨蛋白虚拟边上的 attention 分布存在明显差异，支持模型利用残基级消息传递进行判别。
  - 证据：[doi:10.1016/j.csbj.2025.01.022, p.9]

## 页码证据

- [doi:10.1016/j.csbj.2025.01.022, p.1]
- [doi:10.1016/j.csbj.2025.01.022, p.3]
- [doi:10.1016/j.csbj.2025.01.022, p.5]
- [doi:10.1016/j.csbj.2025.01.022, p.6]
- [doi:10.1016/j.csbj.2025.01.022, p.8]
- [doi:10.1016/j.csbj.2025.01.022, p.9]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
