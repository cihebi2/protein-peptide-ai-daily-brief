# SpatialPPI: Three-dimensional space protein-protein interaction prediction with AlphaFold Multimer

- **论文 ID：** `EVIW-EFFF07329F054B3F`
- **期刊 / 来源：** Comput Struct Biotechnol J
- **发表时间：** 2024 Mar 15
- **DOI：** [10.1016/j.csbj.2024.03.009](https://doi.org/10.1016/j.csbj.2024.03.009)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `结构预测`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者提出 SpatialPPI：先用 AlphaFold Multimer 为蛋白对生成复合体结构，再将结构渲染为 3D tensor，结合 DenseNet3D/ResNet3D 做二分类 PPI 预测，并在自建基准和独立数据集上优于若干现有方法。

## 创新边界

`创新点主要在结构表征与分类管线，不是蛋白候选生成。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在仅有蛋白序列、缺少实验结构时，如何利用 AlphaFold Multimer 预测的三维复合体结构，更准确地判定两条蛋白是否发生相互作用。

## 方法

- 先运行AlphaFold-Multimer生成蛋白复合物，原子类型/空间密度体素化后输入3D ResNet/DenseNet式分类器。

## 数据与基准

- 公开正负PPI对及AlphaFold-Multimer预测结构，按作者协议训练测试。

## 比较基线

- SpeedPPI、D-SCRIPT、DeepTrio、PEPPI及3D CNN架构/体素设置。

## 结果证据

- 论文报告超过SpeedPPI、D-SCRIPT、DeepTrio和PEPPI；属于依赖预测复合物的计算分类。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 对每对蛋白运行AF-M成本高，64³网格受算力限制；错误复合物结构可传播到分类器，不能替代PPI实验。

## 仍未知

- 未独立复现论文结果，也未核验 GitHub 仓库是否与冻结版本完全一致。
- 方法在非 human PPI、跨物种 PPI 或更大规模真实筛选中的泛化能力不清楚。
- AlphaFold Multimer 预测误差和负样本构造方式可能共同影响最终性能。

## Pi 结构化证据摘录

- **baseline：** 主对照为 DeepTrio、SpeedPPI、D-script（origin/Topsy-Turvy）和 PEPPI；额外数据集上则比较了 DeepTrio、SpeedPPI 和 D-script Topsy-Turvy。
  - 证据：[doi:10.1016/j.csbj.2024.03.009, p.7]；[doi:10.1016/j.csbj.2024.03.009, p.8]
- **baseline：** 论文还用 Rosetta docking score、平均 interface pLDDT、接触残基数和序列长度等指标分析 AlphaFold Multimer 输出，以解释与基于结构置信度的 baseline 的差异。
  - 证据：[doi:10.1016/j.csbj.2024.03.009, p.8]
- **data：** 主数据集来自 BioGRID v4.4.206 的正例与 Negatome 2.0 的负例，清理冲突、重复和自相互作用后得到 1200 对样本（600 正、600 负），来自 375 个 Homo sapiens 蛋白。
  - 证据：[doi:10.1016/j.csbj.2024.03.009, p.2]；[doi:10.1016/j.csbj.2024.03.009, p.3]
- **data：** 每对样本用 AlphaFold Multimer v2.3.1 生成 5 个复合体模型，总计 6000 个 PDB 文件。
  - 证据：[doi:10.1016/j.csbj.2024.03.009, p.2]
- **data：** 额外验证集来自 DeepTrio，包含 571 个不重复的人类正例及其打乱序列生成的负例，且与标准数据集的最大序列同一性为 25%。
  - 证据：[doi:10.1016/j.csbj.2024.03.009, p.8]
- **declared_resources：** SpatialPPI 代码在 GitHub 上公开，论文页内声明其使用 Apache-2.0 license。
  - 证据：[doi:10.1016/j.csbj.2024.03.009, p.1]
- **declared_resources：** 结构预测依赖 AlphaFold Multimer v2.3.1，并使用 jackhmmer/HMMER3、Uniref90、UniProt、MGnify、Big Fantastic Database、UniRef30 和 HHblits。
  - 证据：[doi:10.1016/j.csbj.2024.03.009, p.2]
- **declared_resources：** 数据资源包括 BioGRID v4.4.206 和 Negatome 2.0；评估时还用到了 MMseqs2 easy-cluster。
  - 证据：[doi:10.1016/j.csbj.2024.03.009, p.2]；[doi:10.1016/j.csbj.2024.03.009, p.3]；[doi:10.1016/j.csbj.2024.03.009, p.6]
- **declared_resources：** 计算实验在 Tokyo Institute of Technology 的 TSUBAME 3.0 supercomputer 上完成。
  - 证据：[doi:10.1016/j.csbj.2024.03.009, p.11]
- **limitations：** 作者明确指出，若把随机打乱得到的理论负例与实验负例比较，很多方法会表现更好；因此结果对负样本构造方式敏感，不能直接等同于真实筛选场景的难度。
  - 证据：[doi:10.1016/j.csbj.2024.03.009, p.8]
- **limitations：** AlphaFold Multimer 的不同模型之间平均 RMSD 约 19 Å，说明同一蛋白对的预测结构差异较大，且平均 interface pLDDT 或 Rosetta docking score 并不能清晰区分正负例。
  - 证据：[doi:10.1016/j.csbj.2024.03.009, p.8]
- **limitations：** 论文承认长的无序区会在预测结构中缠绕到接口附近，所以需要删除低置信度或无序片段；这说明方法对界面定义和预处理较敏感。
  - 证据：[doi:10.1016/j.csbj.2024.03.009, p.4]；[doi:10.1016/j.csbj.2024.03.009, p.9]
- **limitations：** 作者将张量尺寸固定为 64×64×64×8，并称更细分辨率会显著增加计算成本，提示该方法在算力与分辨率之间存在权衡。
  - 证据：[doi:10.1016/j.csbj.2024.03.009, p.4]
- **method：** 先把两条单链序列送入 AlphaFold Multimer 预测复合体结构，再把结构文件转成 3D tensor 作为 CNN 输入。
  - 证据：[doi:10.1016/j.csbj.2024.03.009, p.1]；[doi:10.1016/j.csbj.2024.03.009, p.2]；[doi:10.1016/j.csbj.2024.03.009, p.4]
- **method：** 作者比较了 one-hot、volume、distance 三种 tensorization，其中 distance encoding 以 12 Å 为上限、以界面为中心并保留更稠密的空间信息。
  - 证据：[doi:10.1016/j.csbj.2024.03.009, p.4]；[doi:10.1016/j.csbj.2024.03.009, p.5]
- **method：** 网络主体采用修改后的 3D ResNet 或 3D DenseNet，包含 4 个 block、每块 4 个 3D convolution 层，并配合 dropout、batch normalization、global max pooling 和 softmax。
  - 证据：[doi:10.1016/j.csbj.2024.03.009, p.6]
- **method：** 评估时使用 MMseqs2 聚类后做 5-fold cross-validation，并在训练时对每对蛋白使用 5 个 AlphaFold 模型，测试时只用第一个模型。
  - 证据：[doi:10.1016/j.csbj.2024.03.009, p.6]
- **results：** 在主 5-fold 实验中，DenseNet3D+distance encoding 取得最佳成绩：ACC 0.818、AUC 0.892、precision 0.832、recall 0.796。
  - 证据：[doi:10.1016/j.csbj.2024.03.009, p.7]
- **results：** 与 DeepTrio、SpeedPPI、D-script 和 PEPPI 相比，SpatialPPI 在主基准上获得最高 ACC、AUC 和 recall。
  - 证据：[doi:10.1016/j.csbj.2024.03.009, p.7]
- **results：** 在额外数据集上，SpatialPPI 达到 ACC 0.835、AUC 0.920、precision 0.845、recall 0.828；CASP14 测试中，RMSD<5 Å 的 13 例里正确 11 例，RMSD>5 Å 的 4 例里正确 2 例。
  - 证据：[doi:10.1016/j.csbj.2024.03.009, p.8]；[doi:10.1016/j.csbj.2024.03.009, p.9]

## 页码证据

- [doi:10.1016/j.csbj.2024.03.009, p.1]
- [doi:10.1016/j.csbj.2024.03.009, p.2]
- [doi:10.1016/j.csbj.2024.03.009, p.4]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
