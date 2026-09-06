# Guided diffusion for molecular generation with interaction prompt

- **论文 ID：** `EVIW-CD8D2F4D209CDB2C`
- **期刊 / 来源：** Brief Bioinform
- **发表时间：** 2024 Apr 21
- **DOI：** [10.1093/bib/bbae174](https://doi.org/10.1093/bib/bbae174)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `扩散/生成`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者提出 InterDiff：一种把残基 interaction prompts 注入 3D diffusion generative model 的方法，用可学习 prompt embedding 和 cross-attention 指导分子生成，并在 benchmark 与真实靶点上展示可控相互作用生成能力。

## 创新边界

`边界在于“残基级 interaction prompt + diffusion-based SBDD”这一组合；但证据仅限 in silico，且“first study” 属于作者自述，未在冻结材料中独立验证。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在 3D structure-based drug design 中，现有分子生成模型虽然能在蛋白口袋内生成候选分子，但往往忽略 ligand–protein 的原子级相互作用信息，因而难以按 hotspot 残基定制结合模式。

## 方法

- 蛋白口袋和相互作用提示共同条件化每个去噪步骤，跨注意力结合原子距离；支持氢键、卤键、pi-pi和cation-pi提示，并扩展为片段生成。

## 数据与基准

- CrossDocked2020过滤后100,000训练样本和100测试样本；BINANA2标注相互作用；DOCKSTRING作为外部验证，含58个靶点且每靶点超过260,000个对接分子。

## 比较基线

- 重新评估GraphBP、Pocket2Mol、3D-SBDD、TargetDiff和DiffSBDD，并在八项通用指标和交互恢复任务上比较。

## 结果证据

- InterDiff在指定作用恢复率上领先，并能在两个真实靶点重现药物关键作用；但通用指标中TargetDiff/DiffSBDD的Vina更好，Pocket2Mol的QED、SA和Lipinski更好，InterDiff优势主要在交互可控性而非全面质量。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 生成分子的QED与SA低于部分基线；无提示时作用恢复显著下降；作者把子结构药物性和可合成性优化列为未来工作，真实靶点验证仍主要是计算。

## 仍未知

- 补充材料中的完整表格、统计检验与额外图示未逐项核验。
- GitHub 仓库的当前可用性与可执行复现未在本次冻结材料中验证。
- prompt 选择策略的自动化程度与对不同靶点的泛化上限仍不清楚。

## Pi 结构化证据摘录

- **baseline：** 主比较基线包括 GraphBP、Pocket2Mol、3D-SBDD、TargetDiff 和 DiffSBDD；文中同时报告了 CrossDocked2020 与 DOCKSTRING 上的对比。
  - 证据：[doi:10.1093/bib/bbae174, p.4]
- **baseline：** 作者还做了 InterDiff-r 消融，去掉 cross-attention 后，若干 interaction 数量下的恢复准确率下降，说明该模块有贡献。
  - 证据：[doi:10.1093/bib/bbae174, p.10]
- **baseline：** InterDiff_noprompt 作为无 interaction prompt 的对照，显示 prompt 信息对 interaction 恢复是必要的。
  - 证据：[doi:10.1093/bib/bbae174, p.5]
- **data：** 主训练与测试数据来自 CrossDocked2020，源自 PDB；按文中准则得到 100000 个训练样本和 100 个测试样本，并用 BINANA2 标注相互作用。
  - 证据：[doi:10.1093/bib/bbae174, p.2]
- **data：** 作者排除了同一残基被检测出多于一种 interaction 的复合物，因此只保留单一 interaction 标签的样本进入 prompt 设定。
  - 证据：[doi:10.1093/bib/bbae174, p.2]
- **data：** 外部验证使用 DOCKSTRING，文中写明其为每个蛋白提供超过 260000 个分子的 docking poses，并覆盖 58 个临床相关靶点。
  - 证据：[doi:10.1093/bib/bbae174, p.2]
- **data：** 真实场景演示选用 mAChR 与 KRAS，并使用 PDB 结构 6oik、3uon、8azx 和 8azv 作为参考靶标/构象。
  - 证据：[doi:10.1093/bib/bbae174, p.6]；[doi:10.1093/bib/bbae174, p.11]
- **declared_resources：** 资金来源包括 NSFC Tianyuan Fund 12326610、NSFC 61931024/92359202、Shenzhen Engineering Research Center XMHT20220104016 和 Shenzhen Science and Technology Program JCYJ20220818100015031。
  - 证据：[doi:10.1093/bib/bbae174, p.11]
- **declared_resources：** 作者公开了 CrossDocked2020 地址、4 个 PDB 结构（6oik、3uon、8azx、8azv）以及 GitHub 仓库 `https://github.com/zephyrdhb/InterDiff`，并声明 source code、sampling conformers 和 notebook 可获得。
  - 证据：[doi:10.1093/bib/bbae174, p.11]
- **limitations：** 作者明确承认生成结果中仍会出现难以合成的结构，这被归因于分子重建算法缺陷，并计划引入 chemical bond 信息改善 drug-likeness 和 synthetic accessibility。
  - 证据：[doi:10.1093/bib/bbae174, p.8]
- **limitations：** π-π interaction 表现较差，原因包括几何约束更复杂、类别不平衡，以及后处理时 aromatic ring 重建依赖性强。
  - 证据：[doi:10.1093/bib/bbae174, p.5]；[doi:10.1093/bib/bbae174, p.8]
- **limitations：** inpainting 模式比 pocket-conditional 更弱，因为模型同时要估计蛋白与配体原子；作者还指出 anchor point 信息可能有助于改进。
  - 证据：[doi:10.1093/bib/bbae174, p.7]
- **limitations：** interaction prompt 的选择目前仍依赖参考配体或药物化学经验，作者把其列为后续改进方向。
  - 证据：[doi:10.1093/bib/bbae174, p.8]
- **method：** 作者以 Guan 等人的 3D equivariant diffusion 框架为基础，把蛋白-配体复合物表示为带坐标与类别特征的点云，并在前向扩散中对坐标加入高斯噪声、对原子类型做分类扩散。
  - 证据：[doi:10.1093/bib/bbae174, p.9]
- **method：** InterDiff 为残基引入两类 interaction prompts：one-hot 离散编码与可学习连续 embedding，覆盖 cation-π、halogen、hydrogen bond 和 π-π 四种相互作用。
  - 证据：[doi:10.1093/bib/bbae174, p.1]；[doi:10.1093/bib/bbae174, p.9]
- **method：** 模型由六个 equivariant block 组成，每层先更新节点特征，再更新 ligand 坐标，并用 cross-attention 融合 ligand–protein 长程信息与距离编码。
  - 证据：[doi:10.1093/bib/bbae174, p.9]
- **method：** 作者另外构造了 unconditional diffusion 版本用于 fragment inpainting，通过固定 scaffold 和 pocket 上下文，仅重采样未知片段。
  - 证据：[doi:10.1093/bib/bbae174, p.7]
- **results：** 在 CrossDocked2020 测试集上，InterDiff 达到 96.70% validity、100% novelty、99.87% uniqueness，且 diversity 为 0.769±0.06。
  - 证据：[doi:10.1093/bib/bbae174, p.4]
- **results：** 在 interaction 恢复任务中，InterDiff 在不同 interaction 数量下总体优于其他方法；去掉 interaction prompt 后，恢复准确率明显下降。
  - 证据：[doi:10.1093/bib/bbae174, p.4]；[doi:10.1093/bib/bbae174, p.5]
- **results：** 与 baseline 相比，InterDiff 在 mAChR 的 active 与 inactive state 中都能复现 xanomeline 的关键相互作用，并生成更好的 docking score；在 KRAS 上能部分复现 BI-2865 的结合模式，但分数仍逊于原配体。
  - 证据：[doi:10.1093/bib/bbae174, p.6]
- **results：** 在 fragment growing/inpainting 任务中，InterDiff 能基于 scaffold 生成新片段并保留部分目标相互作用，但其精度低于 pocket-conditional 模式。
  - 证据：[doi:10.1093/bib/bbae174, p.7]

## 页码证据

- [doi:10.1093/bib/bbae174, p.11]
- [doi:10.1093/bib/bbae174, p.2]
- [doi:10.1093/bib/bbae174, p.4]
- [doi:10.1093/bib/bbae174, p.8]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
