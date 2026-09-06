# Reliability of AI Methods in Drug Discovery: Evaluation of Boltz-2 for Structure and Binding Affinity Prediction

- **论文 ID：** `EVIW-D12CA6E5603A8D3C`
- **期刊 / 来源：** J Chem Theory Comput
- **发表时间：** 2026 Jul 29
- **DOI：** [10.1021/acs.jctc.6c01334](https://doi.org/10.1021/acs.jctc.6c01334)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白-配体`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者声称对 3CLPro 与 TNKS2 的大规模化合物库进行了系统基准测试，联合比较 Boltz-2 的结构输出、亲和力预测、top-100 排名与 BindingDB 实验数据，以检验其作为高通量虚拟筛选工具的可靠性。

## 创新边界

`这是一项对既有模型 Boltz-2 的经验性 benchmark，不是新算法、新分子生成流程或新的 wet-lab 发现。`。这不是全球首创性检索或独立复现结论。

## 研究问题

评估 Boltz-2 在大规模药物发现场景中能否可靠预测蛋白-配体结构与结合亲和力，并判断其是否足以替代或逼近传统 docking 与物理自由能方法作为筛选依据。

## 方法

- Boltz-2 inference与experimental structures/affinities对照，按target/data novelty分层。

## 数据与基准

- protein-ligand complex和binding affinity test sets。

## 比较基线

- AF3/传统docking/affinity models。

## 结果证据

- 论文报告可靠性边界；为计算benchmark。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 模型版本/训练污染、confidence不等于accuracy。

## 仍未知

- BindingDB 中 B2 样本与 Boltz-2 训练集的真实重叠程度未在本任务中逐条核验。
- top-100 无相关性究竟主要来自方差塌缩还是模型机制失配，冻结证据只能支持现象，不能独立证明原因。
- 部分 Boltz-2 预测到的替代结合位点是否具有真实生物学意义仍不明确。

## Pi 结构化证据摘录

- **baseline：** 本文的核心比较基线是传统 docking 与 physics-based ESMACS，而不是只看 AI 模型自身分数；作者据此判断 Boltz-2 在局部精细排序上不如物理法稳健。
  - 证据：[doi:10.1021/acs.jctc.6c01334, p.3]；[doi:10.1021/acs.jctc.6c01334, p.8]；[doi:10.1021/acs.jctc.6c01334, p.12]
- **baseline：** 作者还用 ESMACS 的不同初始结构来源互相比对，得到约 0.45–0.60 的中等相关，作为物理方法内部一致性的参照。
  - 证据：[doi:10.1021/acs.jctc.6c01334, p.8]；[doi:10.1021/acs.jctc.6c01334, p.9]
- **baseline：** 对实验基线，作者直接采用 BindingDB 公共测量，并通过多测量抽样得到 TNKS2 的实验内部相关约 r=0.56、标准差约 0.25。
  - 证据：[doi:10.1021/acs.jctc.6c01334, p.10]
- **data：** 主数据集共 38,482 个化合物，其中 3CLPro 为 16,780 个、TNKS2 为 21,702 个；约 0.7% 的样本因 MD 或自由能计算失败而被剔除。
  - 证据：[doi:10.1021/acs.jctc.6c01334, p.3]
- **data：** top-100 分析对应 200 个 protein-ligand complexes，并分别以 docking、Boltz-2 直接补氢、以及按 SMILES 规则重建补氢的初始构型进入 FG-ESMACS。
  - 证据：[doi:10.1021/acs.jctc.6c01334, p.3]
- **data：** BindingDB 验证集包含 3CLPro 的 59 个化合物和 TNKS2 的 1,137 个化合物；另有 271 个 TNKS2 化合物被用来评估实验重复测量噪声。
  - 证据：[doi:10.1021/acs.jctc.6c01334, p.3]；[doi:10.1021/acs.jctc.6c01334, p.10]
- **data：** 作者声明全部生成数据已存入 Zenodo，包含 Boltz-2 结构、亲和力、概率以及 ESMACS 结果。
  - 证据：[doi:10.1021/acs.jctc.6c01334, p.12]
- **declared_resources：** 推理与大规模筛选使用 Isambard-AI（5448 个 GH200 superchips），而 FG-ESMACS 在 Frontier 上并行执行，作者报告约 5,000 个 GPU 同时参与。
  - 证据：[doi:10.1021/acs.jctc.6c01334, p.3]；[doi:10.1021/acs.jctc.6c01334, p.4]
- **declared_resources：** 论文声明使用并提及的工具与资源包括 NAMD、Amber、AmberTools、OpenEye、FRED、OMEGA、FixpKa、UniRef90 和 REINVENT。
  - 证据：[doi:10.1021/acs.jctc.6c01334, p.3]；[doi:10.1021/acs.jctc.6c01334, p.4]；[doi:10.1021/acs.jctc.6c01334, p.12]；[doi:10.1021/acs.jctc.6c01334, p.13]
- **declared_resources：** 作者还注明获得 OpenEye 学术许可支持，并将结果数据公开到 Zenodo。
  - 证据：[doi:10.1021/acs.jctc.6c01334, p.12]
- **limitations：** Boltz-2 在全库层面只表现为弱到中等相关，而在 top-100 精细排序中相关性塌缩，说明它不适合作为 hit-to-lead 阶段的可靠打分器。
  - 证据：[doi:10.1021/acs.jctc.6c01334, p.7]；[doi:10.1021/acs.jctc.6c01334, p.8]；[doi:10.1021/acs.jctc.6c01334, p.12]
- **limitations：** 作者报告了系统性的 saturation/protonation 偏差，包括环系过度不饱和与脂肪链过度饱和，这会直接影响形状、电荷和自由能。
  - 证据：[doi:10.1021/acs.jctc.6c01334, p.8]
- **limitations：** BindingDB 数据本身噪声很大，同一 ligand 在不同实验中可相差高达 5.1 kcal/mol，因此公开数据库并不等同于严格的 ground truth。
  - 证据：[doi:10.1021/acs.jctc.6c01334, p.9]；[doi:10.1021/acs.jctc.6c01334, p.10]；[doi:10.1021/acs.jctc.6c01334, p.11]
- **limitations：** 作者只使用默认预训练权重且未施加空间约束，因此结论主要反映 out-of-the-box 性能，不能排除训练截止前后的记忆或近邻重叠影响。
  - 证据：[doi:10.1021/acs.jctc.6c01334, p.3]；[doi:10.1021/acs.jctc.6c01334, p.10]；[doi:10.1021/acs.jctc.6c01334, p.11]
- **method：** 采用既有的 3CLPro 与 TNKS2 化合物库作为主测试集，并以 Boltz-2 默认预训练权重、输入蛋白序列和 ligand SMILES，在 Isambard-AI 上执行推理。
  - 证据：[doi:10.1021/acs.jctc.6c01334, p.3]
- **method：** 将传统 docking 作为结构基线，并用 coarse-grained ESMACS 评估全库结合自由能；对 Boltz-2 的 top-100 进一步用 fine-grained ESMACS 及不同补氢/质子化方案做精细比较。
  - 证据：[doi:10.1021/acs.jctc.6c01334, p.3]；[doi:10.1021/acs.jctc.6c01334, p.4]；[doi:10.1021/acs.jctc.6c01334, p.8]
- **method：** 结构质量通过 protein/ligand RMSD 与 LDDT 评价，亲和力关系通过 Pearson 与 Spearman 相关系数衡量，并用 SMA 回归处理两侧都有误差的比较。
  - 证据：[doi:10.1021/acs.jctc.6c01334, p.4]；[doi:10.1021/acs.jctc.6c01334, p.7]
- **method：** 实验验证部分从 BindingDB 提取 3CLPro 与 TNKS2 的已知测量，并将 TNKS2 的多来源实验值做 bootstrap 抽样，以估计公开数据库噪声。
  - 证据：[doi:10.1021/acs.jctc.6c01334, p.3]；[doi:10.1021/acs.jctc.6c01334, p.9]；[doi:10.1021/acs.jctc.6c01334, p.10]
- **results：** 结构上，3CLPro 的 Boltz-2 蛋白构象与 X-ray 结构接近，RMSD 约 0.4 Å；TNKS2 则出现多峰分布，主峰约 1.0 Å，并延伸到约 1.8 Å。
  - 证据：[doi:10.1021/acs.jctc.6c01334, p.5]
- **results：** 配体姿势方面，3CLPro 的 ligand RMSD 主要集中在 10 Å 以下但有 22–50 Å 平台；TNKS2 呈双峰分布且两峰都在 10 Å 以下，整体上比 3CLPro 更接近 docking 参考。
  - 证据：[doi:10.1021/acs.jctc.6c01334, p.5]
- **results：** LDDT 结果显示 TNKS2 多数样本低于 5 Å，而 3CLPro 约 11.3% 的配体 LDDT 高于 6 Å，提示部分预测偏离实验口袋。
  - 证据：[doi:10.1021/acs.jctc.6c01334, p.5]
- **results：** Boltz-2 的 confidence score 明显压缩，均值约为 0.946 和 0.944，所有 ligand 都高于 0.8，约 90% 高于 0.9；只有在更严格阈值下才呈现一定区分度。
  - 证据：[doi:10.1021/acs.jctc.6c01334, p.6]
- **results：** 全库亲和力相关性仅为弱到中等：3CLPro 的 Pearson r=0.24、Spearman ρ=0.25，TNKS2 的 r=0.45、ρ=0.46；而重复推理稳定性较高，相关系数可达 r=0.913/0.962 与 ρ=0.897/0.954。
  - 证据：[doi:10.1021/acs.jctc.6c01334, p.7]
- **results：** top-100 子集里，Boltz-2 与 FG-ESMACS 不再呈现有效相关；作者同时观察到饱和/质子化状态偏差，且 docking 起始结构往往给出更有利的 ESMACS 自由能。
  - 证据：[doi:10.1021/acs.jctc.6c01334, p.8]；[doi:10.1021/acs.jctc.6c01334, p.9]
- **results：** 在 TNKS2 的 BindingDB 验证中，Boltz-2 与实验值相关性较强（r=0.77, ρ=0.78），而 ESMACS 仅为 r=0.23、ρ=0.23；3CLPro 的实验相关性则较弱。
  - 证据：[doi:10.1021/acs.jctc.6c01334, p.9]；[doi:10.1021/acs.jctc.6c01334, p.10]

## 页码证据

- [doi:10.1021/acs.jctc.6c01334, p.1]
- [doi:10.1021/acs.jctc.6c01334, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
