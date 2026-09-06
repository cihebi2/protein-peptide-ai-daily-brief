# Combining machine learning with structure-based protein design to predict and engineer post-translational modifications of proteins

- **论文 ID：** `EVIW-83AD8E36CF545DE1`
- **期刊 / 来源：** PLoS Comput Biol
- **发表时间：** 2024 Mar 14
- **DOI：** [10.1371/journal.pcbi.1011939](https://doi.org/10.1371/journal.pcbi.1011939)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白质设计` / `结构预测`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者声称构建了可预测 18 类 PTM 的双轨神经网络，并把它封装成 Rosetta 的 PTMPredictionMetric 与 RosettaTensorflowManager，使其能与结构设计、FastRelax/FastDesign 和 Monte Carlo 优化联动，从而在 Protein A、influenza hemagglutinin 和 de novo phosphorylation switch 上演示 PTM 的预测与工程化。

## 创新边界

`主要创新在于把 PTM 预测与结构基础设计做成可复用的 Rosetta 工具链，并用案例展示其设计用途；它并未通过独立新实验证明普适生物学规律，也不是提出全新的 PTM 化学机制。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在已知或可建模的蛋白质结构上下文中，如何用同时融合序列与结构特征的机器学习模型，既预测多类 PTM 的发生概率，又把这种预测直接嵌入 Rosetta 设计流程来定向增强或抑制特定位点的修饰。

## 方法

- 融合局部序列窗口、Rosetta 结构特征和 AlphaFold2 结构信息的双轨分类器；以 TensorFlow 图加载到 Rosetta，并通过 RosettaScripts 组合预测、分析和设计协议。

## 数据与基准

- 从 dbPTM 收集实验验证位点，并引入 AlphaFold2 预测结构；N-连接糖基化还使用严格筛选的 PDB 结构数据，训练采用交叉验证与类别重采样。

## 比较基线

- 对比既有单一 PTM、主要依赖序列或同源信息的方法；糖基化部分讨论了早期结构+序列模型，论文强调其目标更偏向可设计性。

## 结果证据

- 作者报告结构信息相对仅序列特征提高多类 PTM 预测，并在若干蛋白工程案例中展示评分方向与已知现象一致；论文同时说明该任务缺少统一可用的工程基准，故不宜把个案结果泛化为普适设计成功率。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- AlphaFold2 低 pLDDT 筛选可能系统性排除无序区，而无序区恰富集某些 PTM；高质量阴性位点难以确定；模型面向局部工程而非全蛋白组筛查，且仍需用户掌握表达系统等上下文。

## 仍未知

- Protein A 例子的精确统计口径在正文中存在不一致，需回看原始代码或补充材料才能最终核对。
- 设计突变是否能在独立实验中真正改善 PTM 行为尚未知。
- 对 intrinsically disordered regions、低 pLDDT 区域和全蛋白组筛查的泛化能力未知。
- 本 job 未对 GitHub 仓库做静态复核，因此代码级可复现性未知。

## Pi 结构化证据摘录

- **baseline：** 作者把单 PTM 模型作为内部 baseline，并报告多 PTM 联训在低数据或不平衡 PTM 上普遍优于单任务模型。
  - 证据：[doi:10.1371/journal.pcbi.1011939, p.6]；[doi:10.1371/journal.pcbi.1011939, p.8]
- **baseline：** 讨论中作者把自己的方法与 sequence-only、homology-based 或仅靠细胞定位筛选的 PTM 预测器区分开，强调这些方法更适合天然蛋白筛查，而不是面向设计的局部结构上下文预测。
  - 证据：[doi:10.1371/journal.pcbi.1011939, p.12]；[doi:10.1371/journal.pcbi.1011939, p.18]
- **baseline：** 针对 N-linked glycosylation，作者还提到 2012 年已有结构+序列预测工作优于 sequence-only，而本工作在此基础上加入 AlphaFold2 结构、更多 PTM 联训和 Rosetta 设计接口。
  - 证据：[doi:10.1371/journal.pcbi.1011939, p.12]；[doi:10.1371/journal.pcbi.1011939, p.18]
- **data：** 多数 PTM 数据来自 dbPTM 非同源 benchmark；N-linked glycosylation 则单独从 PDB 中筛选真核表达蛋白，寻找已占据与未占据 sequon，并用 UniProt 注释和人工电子密度检查排除假阴性。
  - 证据：[doi:10.1371/journal.pcbi.1011939, p.5]；[doi:10.1371/journal.pcbi.1011939, p.13]
- **data：** N-linked glycosylation 的训练集规模为 2115 个 positive 和 355 个 negative；全体 PTM 数据量差异很大，phosphorylation 有 61340 datapoints，而 crotonylation 只有 145 个。
  - 证据：[doi:10.1371/journal.pcbi.1011939, p.5]；[doi:10.1371/journal.pcbi.1011939, p.6]
- **data：** deamidation 没有可公开的完整序列与结构特征，作者只能复用 Delmar et al. 的已发表数据，未能像其他 PTM 一样补充 AlphaFold2 与 PyRosetta 特征。
  - 证据：[doi:10.1371/journal.pcbi.1011939, p.5]；[doi:10.1371/journal.pcbi.1011939, p.13]
- **declared_resources：** Rosetta、RosettaScripts、FastRelax、FastDesign、SimpleMetric、GenericMonteCarloMover 和 SimpleGlycosylateMover 是这项工作的核心设计与分析基础设施。
  - 证据：[doi:10.1371/journal.pcbi.1011939, p.5]；[doi:10.1371/journal.pcbi.1011939, p.13]；[doi:10.1371/journal.pcbi.1011939, p.14]；[doi:10.1371/journal.pcbi.1011939, p.15]
- **declared_resources：** TensorFlow、Keras、TensorFlow C API 以及自建的 RosettaTensorflowManager 被用于模型训练与推理封装。
  - 证据：[doi:10.1371/journal.pcbi.1011939, p.5]；[doi:10.1371/journal.pcbi.1011939, p.7]；[doi:10.1371/journal.pcbi.1011939, p.13]；[doi:10.1371/journal.pcbi.1011939, p.14]
- **declared_resources：** 数据与案例资源包括 dbPTM、AlphaFold2 database、PDB、UniProt、Delmar et al. 的 deamidation 数据，以及 Woodall et al. 的 de novo phosphorylation switch。
  - 证据：[doi:10.1371/journal.pcbi.1011939, p.5]；[doi:10.1371/journal.pcbi.1011939, p.13]；[doi:10.1371/journal.pcbi.1011939, p.14]；[doi:10.1371/journal.pcbi.1011939, p.15]
- **limitations：** 作者明确说明没有对案例中的设计突变做新的湿实验验证，因此这些 redesign 结果只能视为计算层面的可行性展示。
  - 证据：[doi:10.1371/journal.pcbi.1011939, p.11]
- **limitations：** AlphaFold2 结构质量仍然限制特征可靠性，尤其是低 pLDDT 区域和 intrinsically disordered regions，作者承认这会削弱方法对 IDR 的适用性。
  - 证据：[doi:10.1371/journal.pcbi.1011939, p.12]
- **limitations：** N-linked glycosylation 数据可能仍含假阴性，且方法依赖用户对目标蛋白、分泌标签和表达系统的先验知识，因此不能直接替代全蛋白组筛查器。
  - 证据：[doi:10.1371/journal.pcbi.1011939, p.12]；[doi:10.1371/journal.pcbi.1011939, p.13]
- **limitations：** 作者也指出当前 benchmark 对蛋白设计任务并不充分，随着新数据出现，模型和阈值都需要重新训练或更新。
  - 证据：[doi:10.1371/journal.pcbi.1011939, p.11]；[doi:10.1371/journal.pcbi.1011939, p.12]
- **method：** 作者先从 dbPTM 非同源基准集收集多数 PTM 的正负样本，再用 AlphaFold2 结构模型并以 local/overall pLDDT > 50 过滤；随后借助 PyRosetta 计算 SASA、二面角和二级结构等结构特征。
  - 证据：[doi:10.1371/journal.pcbi.1011939, p.5]；[doi:10.1371/journal.pcbi.1011939, p.13]
- **method：** 每个单任务模型都采用双轨神经网络：序列轨道输入 -4/+4 的 8-residue window，经 embedding、global average pooling 和 dense layer；结构轨道输入目标位点及其邻位的 phi/psi、secondary structure 与 SASA，再经全连接层融合输出概率。
  - 证据：[doi:10.1371/journal.pcbi.1011939, p.14]
- **method：** 在多 PTM 设置下，作者为共享修饰氨基酸不同的 PTM 训练联合模型，并在序列轨道加入 attention、在结构轨道增加 dense layer，输出改为 softmax；训练使用 Adam、early stopping、10-fold cross validation 和不平衡采样。
  - 证据：[doi:10.1371/journal.pcbi.1011939, p.6]；[doi:10.1371/journal.pcbi.1011939, p.14]
- **method：** 作者把模型实现为 Rosetta SimpleMetric（PTMPredictionMetric），通过 RosettaTensorflowManager 和 TensorFlow C API 做推理，并用 GenericMonteCarloMover 在 Rosetta 设计中联合优化 total score 与预测的 PTM 概率。
  - 证据：[doi:10.1371/journal.pcbi.1011939, p.5]；[doi:10.1371/journal.pcbi.1011939, p.14]；[doi:10.1371/journal.pcbi.1011939, p.15]
- **results：** 单任务模型的 test MCC 从 proline hydroxylation 的 0.76 到 N-linked glycosylation 的 0.10；在数据稀缺的 PTM 上，多修饰模型通常更好，例如 crotonylation MCC 从 0.32 提高到 0.49，N-linked glycosylation 从 0.10 提高到 0.20。
  - 证据：[doi:10.1371/journal.pcbi.1011939, p.6]；[doi:10.1371/journal.pcbi.1011939, p.8]
- **results：** Protein A 例子中，作者称可识别大多数 asparagine 的 deamidation propensity，并且对 N23 邻位的突变会显著降低预测去酰胺化概率。
  - 证据：[doi:10.1371/journal.pcbi.1011939, p.7]；[doi:10.1371/journal.pcbi.1011939, p.8]
- **results：** influenza H3N2 HK68 例子中，作者称原始结构能正确分类 5 个已知 N-linked glycosylation 位点中的 4 个，而把后来获得的 4 个 glycosylation site 映射到原始结构后可正确预测其中 3 个。
  - 证据：[doi:10.1371/journal.pcbi.1011939, p.9]；[doi:10.1371/journal.pcbi.1011939, p.11]
- **results：** de novo serine-kinase driven phosphorylation switch 例子中，作者正确预测了 4 个引入的 phosphorylation sites，并通过 I89R、A92T、Q97R 将 S93 的预测概率从 0.63 提升到 0.88。
  - 证据：[doi:10.1371/journal.pcbi.1011939, p.10]；[doi:10.1371/journal.pcbi.1011939, p.11]

## 页码证据

- [doi:10.1371/journal.pcbi.1011939, p.12]
- [doi:10.1371/journal.pcbi.1011939, p.14]
- [doi:10.1371/journal.pcbi.1011939, p.1]
- [doi:10.1371/journal.pcbi.1011939, p.5]
- [doi:10.1371/journal.pcbi.1011939, p.7]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
