# Direct prediction of intrinsically disordered protein conformational properties from sequence

- **论文 ID：** `EVIW-7B3C01E5F293C7BA`
- **期刊 / 来源：** Nat Methods
- **发表时间：** 2024 Jan 31
- **DOI：** [10.1038/s41592-023-02159-5](https://doi.org/10.1038/s41592-023-02159-5)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者声称提出了 ALBATROSS：一个基于深度学习、由 coarse-grained simulations 训练得到的 sequence-to-ensemble 预测框架，可直接从序列预测 IDR 的 radius of gyration、end-to-end distance、asphericity、scaling exponent 和 prefactor，并可扩展到 human proteome 的 IDR-ome 注释与局部子区域分析。[doi:10.1038/s41592-023-02159-5, p.1]

## 创新边界

`创新边界在于“性质预测与注释”，不是 de novo 设计、优化或排名候选分子；它能支持设计假设生成，但本身不生成新的 binder/peptide/enzyme/drug 候选。[doi:10.1038/s41592-023-02159-5, p.2]`。这不是全球首创性检索或独立复现结论。

## 研究问题

该文要解决的是：如何仅从序列直接、快速地预测 intrinsically disordered proteins/regions (IDPs/IDRs) 的构象集合性质，避免依赖耗时的模拟或实验测量；作者强调 IDRs 缺乏稳定三维结构，因此现有方法难以在蛋白组尺度上给出 ensemble 级别的几何描述。[doi:10.1038/s41592-023-02159-5, p.1]

## 方法

- 先校准 Mpipi-GG 粗粒化力场，模拟化学组成多样的合成/天然 IDR，再训练序列到集合性质的深度模型，并与 metapredict 联用做蛋白组级注释。[doi:10.1038/s41592-023-02159-5, p.2][doi:10.1038/s41592-023-02159-5, p.13]

## 数据与基准

- 合成 22,127 条、天然 19,075 条 IDR，长度 10–750 aa，覆盖电荷、疏水性、模式和组成变化。[doi:10.1038/s41592-023-02159-5, p.13]

## 比较基线

- 以 Mpipi-GG 模拟和可用实验集合数据为参照，并比较不同网络复杂度及聚合物物理基线。[doi:10.1038/s41592-023-02159-5, p.2][doi:10.1038/s41592-023-02159-5, p.9]

## 结果证据

- 论文报告 ALBATROSS 可由序列快速预测 IDR 全局尺寸并在所用模拟/实验趋势上保持准确，可把蛋白组 IDR 注释从昂贵模拟降至秒至分钟级。[doi:10.1038/s41592-023-02159-5, p.2][doi:10.1038/s41592-023-02159-5, p.9]

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 模型预测的是孤立 IDR 的基线行为，折叠结构域、配体、翻译后修饰等环境效应未被朴素预测捕获；更复杂架构可能提高精度。[doi:10.1038/s41592-023-02159-5, p.9]

## 仍未知

- 补充材料与代码仓库未在本次冻结页之外做外部核验。
- 对富 transient helicity 或强疏水 IDRs 的偏差幅度未定。
- 部分功能解释（如 compact IDR 与 RNA binding 的因果关系）仍属于作者推断。

## Pi 结构化证据摘录

- **baseline：** 相较原始 Mpipi force field，Mpipi-GG 在 137 个 SAXS radii of gyration 上略优，R2 从 0.896 提升到 0.921。[doi:10.1038/s41592-023-02159-5, p.3]
  - 证据：[doi:10.1038/s41592-023-02159-5, p.3]
- **baseline：** 作者将 ALBATROSS 与当时的 state-of-the-art Rg 预测方法比较，声称其准确度可比或更高，同时吞吐量显著更高。[doi:10.1038/s41592-023-02159-5, p.4]
  - 证据：[doi:10.1038/s41592-023-02159-5, p.4]；[doi:10.1038/s41592-023-02159-5, p.11]
- **baseline：** 与 CAL VADOS2 的 human proteome 模拟结果相比，作者报告 ALBATROSS 的一致性很高，R2=0.98、r.m.s.e.=3.68 Å，n=29,998。[doi:10.1038/s41592-023-02159-5, p.9]
  - 证据：[doi:10.1038/s41592-023-02159-5, p.9]
- **baseline：** 作者还用 AFRC 作为长度依赖的 null model 来归一化链尺寸，并据此判断偏离高斯链行为的 sequence-specific expansion 或 compaction。[doi:10.1038/s41592-023-02159-5, p.5]
  - 证据：[doi:10.1038/s41592-023-02159-5, p.5]；[doi:10.1038/s41592-023-02159-5, p.13]
- **data：** 独立测试集共 6,037 条序列，其中包含 2,306 条经 CD-HIT 去重后的 biological IDRs 与 3,731 条 synthetic IDRs；训练与测试序列都限制在 10–750 residues 范围内。[doi:10.1038/s41592-023-02159-5, p.13]
  - 证据：[doi:10.1038/s41592-023-02159-5, p.13]
- **data：** human proteome 分析聚焦长度 35–3,000 residues 的 IDRs，图中对应约 20,812 条 human IDRs，并进一步给出 normalized Rg、normalized Re 与 asphericity 的分布。[doi:10.1038/s41592-023-02159-5, p.5]
  - 证据：[doi:10.1038/s41592-023-02159-5, p.5]；[doi:10.1038/s41592-023-02159-5, p.14]
- **data：** local subregion 分析对 human proteome 中的 51-mer 片段进行了 2,146,400 次扫描，并据此识别出 1,022 个具有十个以上 expanded subwindows 的蛋白和 1,175 个具有 compact subregions 的蛋白。[doi:10.1038/s41592-023-02159-5, p.14]
  - 证据：[doi:10.1038/s41592-023-02159-5, p.14]
- **data：** yeast homologous IDR 分析从 20 个 yeast proteomes 中提取了 2,302 组同源 IDR，总计 49,335 条 IDRs，用于比较 sequence divergence 与 Re conservation。[doi:10.1038/s41592-023-02159-5, p.8]
  - 证据：[doi:10.1038/s41592-023-02159-5, p.8]；[doi:10.1038/s41592-023-02159-5, p.14]
- **declared_resources：** ALBATROSS 作为 SPARROW 的一部分发布，并提供单序列与大规模 proteome-wide 预测的 Google Colab notebook。[doi:10.1038/s41592-023-02159-5, p.14]
  - 证据：[doi:10.1038/s41592-023-02159-5, p.14]
- **declared_resources：** 作者同时给出 metapredict V2-FF，用于快速 disorder prediction，并说明其相较 metapredict V2 有 5–50× 的速度提升。[doi:10.1038/s41592-023-02159-5, p.13]
  - 证据：[doi:10.1038/s41592-023-02159-5, p.13]
- **declared_resources：** 训练与测试用的 synthetic 和 natural IDRs、SAXS comparison sequences 以及其他分析数据被共享到 GitHub，并提供 Zenodo 归档 DOI 10.5281/zenodo.10198620。[doi:10.1038/s41592-023-02159-5, p.14]
  - 证据：[doi:10.1038/s41592-023-02159-5, p.14]
- **declared_resources：** Fig. 4、Fig. 5 的 proteome-wide 结果和 Fig. 6 的同源分析文件也以 SHEPHARD-compliant datafiles 形式公开。[doi:10.1038/s41592-023-02159-5, p.14]
  - 证据：[doi:10.1038/s41592-023-02159-5, p.14]
- **limitations：** ALBATROSS 只针对孤立 IDRs 参数化，不显式建模 N/C 端 folded domains 或 ligand 作用，因此对真实体系中的 domain–domain 与分子间相互作用不能直接给出完整描述。[doi:10.1038/s41592-023-02159-5, p.9]
  - 证据：[doi:10.1038/s41592-023-02159-5, p.9]
- **limitations：** 作者明确指出模型可能低估带电残基的 solvation effect、忽略 transient secondary structure，并可能低估 aliphatic residues 的 hydrophobic effect，从而对某些 IDRs 产生偏差。[doi:10.1038/s41592-023-02159-5, p.9]
  - 证据：[doi:10.1038/s41592-023-02159-5, p.9]
- **limitations：** 对于富含 helicity 或强疏水成分的 IDRs，作者认为预测可能偏向过度 expanded，因此需要结合实验或更细粒度模拟校正。[doi:10.1038/s41592-023-02159-5, p.9]
  - 证据：[doi:10.1038/s41592-023-02159-5, p.9]
- **limitations：** 关于 Yak1、Spt2 等演化案例，文中机制解释主要仍是作者假设，尚未在此文中被直接实验验证。[doi:10.1038/s41592-023-02159-5, p.8]
  - 证据：[doi:10.1038/s41592-023-02159-5, p.8]；[doi:10.1038/s41592-023-02159-5, p.9]
- **method：** 训练数据由 GOOSE 生成的 22,127 条 synthetic IDRs 与 19,075 条天然 IDRs 组成，总计 41,202 条序列，覆盖 charge、hydropathy、charge patterning 和 amino acid composition 等特征空间。[doi:10.1038/s41592-023-02159-5, p.3]
  - 证据：[doi:10.1038/s41592-023-02159-5, p.3]；[doi:10.1038/s41592-023-02159-5, p.13]
- **method：** 作者使用 LAMMPS 运行 Mpipi-GG（并与 Mpipi 对照）的 coarse-grained molecular dynamics，在 150 mM implicit salt、300 K、NVT 条件下对短序列模拟 6 µs、长序列模拟 10 µs，并做 5 次重复以估计误差。[doi:10.1038/s41592-023-02159-5, p.13]
  - 证据：[doi:10.1038/s41592-023-02159-5, p.13]
- **method：** ALBATROSS 采用 PARROT 的 BRNN-LSTM 架构，使用 one-hot encoding 与 L1 loss，通过 fivefold cross-validation 和超参数网格搜索训练多个预测器，覆盖 Rg、Re、asphericity 以及 polymer-scaling exponent/prefactor。[doi:10.1038/s41592-023-02159-5, p.3]
  - 证据：[doi:10.1038/s41592-023-02159-5, p.3]；[doi:10.1038/s41592-023-02159-5, p.13]
- **method：** 蛋白组与局部分析依赖 metapredict V2-FF、SPARROW、SHEPHARD 和 AFRC 归一化；局部构象通过 51-residue sliding window 对 human proteome 的 51-mer 片段进行扫描。[doi:10.1038/s41592-023-02159-5, p.13]
  - 证据：[doi:10.1038/s41592-023-02159-5, p.13]；[doi:10.1038/s41592-023-02159-5, p.14]
- **results：** 在独立测试集上，ALBATROSS 对 Mpipi-GG 生成的标签表现很强：Rg 的 R2=0.995，Re 的 R2=0.986，asphericity 的 R2=0.817，scaling exponent 的 R2=0.967，prefactor 的 R2=0.930。[doi:10.1038/s41592-023-02159-5, p.4]
  - 证据：[doi:10.1038/s41592-023-02159-5, p.4]
- **results：** 作者的 human proteome 结果表明，大多数 IDRs 呈相对 expanded 状态；compact IDRs 往往富集 aromatic residues，而 expanded IDRs 更常与 net charge 和 proline 富集相关。[doi:10.1038/s41592-023-02159-5, p.5]
  - 证据：[doi:10.1038/s41592-023-02159-5, p.5]；[doi:10.1038/s41592-023-02159-5, p.7]
- **results：** 局部分析显示，compact subregions 中富集的氨基酸包括 Y/W/H/F/G/Q/R/N，而 expanded subregions 更偏向 P、E、A、V、T、K、L、M、D、I、S 等；作者据此认为局部构象与 RNA-binding 相关残基存在明显重叠。[doi:10.1038/s41592-023-02159-5, p.7]
  - 证据：[doi:10.1038/s41592-023-02159-5, p.7]
- **results：** 在 yeast 同源 IDR 的案例中，Yak1 NTD 与 Spt2 linker 都显示出跨物种序列差异较大、但 Re 变化相对受限的现象，支持 conformational buffering 的解释。[doi:10.1038/s41592-023-02159-5, p.8]
  - 证据：[doi:10.1038/s41592-023-02159-5, p.8]
- **results：** 作者报告 ALBATROSS 可在 commodity CPU 上达到每秒 30–60 条序列、在 GPU 上达到每秒数千条序列的推断速度，并可在约 8 秒内完成 human proteome 的 Rg 预测。[doi:10.1038/s41592-023-02159-5, p.2]
  - 证据：[doi:10.1038/s41592-023-02159-5, p.2]；[doi:10.1038/s41592-023-02159-5, p.14]

## 页码证据

- [doi:10.1038/s41592-023-02159-5, p.2]
- [doi:10.1038/s41592-023-02159-5, p.9]
- [doi:10.1038/s41592-023-02159-5, p.13]
- [doi:10.1038/s41592-023-02159-5, p.14]
- [doi:10.1038/s41592-023-02159-5, p.1]
- [doi:10.1038/s41592-023-02159-5, p.2]
- [doi:10.1038/s41592-023-02159-5, p.9]
- [doi:10.1038/s41592-023-02159-5, p.13]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
