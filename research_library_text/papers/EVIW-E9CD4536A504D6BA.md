# A scalable reinforcement learning approach for screening large peptide libraries for bioactive peptide discovery

- **论文 ID：** `EVIW-E9CD4536A504D6BA`
- **期刊 / 来源：** Nat Commun
- **发表时间：** 2025 Nov 27
- **DOI：** [10.1038/s41467-025-66748-y](https://doi.org/10.1038/s41467-025-66748-y)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `肽与抗菌肽`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者提出 TARSA/PepSce：先把肽库映射到低维可导航空间，再结合 reinforcement learning、posterior sampling 与 oracle proxy 做热点优先筛选，最终在 PDB 螺旋肽库中找出并实验验证出对 MDA-MB-231 有活性的候选肽。

## 创新边界

`创新边界主要在于把 RL+MCMC 用于有限肽库的高效排序与筛选，而不是从头生成新序列；核心贡献是超大库的优先级搜索和体外验证闭环。`。这不是全球首创性检索或独立复现结论。

## 研究问题

论文要解决的是：在超大规模肽库中，如何以可承受的计算成本筛出具备抗癌/膜裂解活性的候选肽，并尽量兼顾选择性与后续体外验证可行性。

## 方法

- surrogate/oracle迭代posterior sampling 3600万helical peptide库，top candidates合成测试。

## 数据与基准

- 3600万PDB-derived helical peptides，top100中实验筛选。

## 比较基线

- exhaustive/random/standard active learning。

## 结果证据

- 15/100对breast cancer cells有cytotoxicity，3 leads对healthy human cells不毒；为明确in vitro实验。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- oracle在MCF10A毒性泛化失败，训练集中需加入cell-specific negative controls；未体内验证。

## 仍未知

- 补充材料中的超参数、数据切分与实现细节未在正文完整展开。
- 代码仓库与 Zenodo 归档未在本任务中做静态核验，无法确认与正文完全一致。
- TARSA 的真实增益有多少来自 RL、多少来自 MCMC、多少来自 2D-PCA 压缩，正文没有做严格消融分解。
- 更广泛细胞系上的可迁移性仍不清楚，尤其是对非血液系正常细胞的选择性。

## Pi 结构化证据摘录

- **baseline：** 作者把 TARSA 放在既有 ACP/QSAR/ML 文献背景中，指出先前方法多停留在小规模或纯预测层面，而超大库筛选仍受计算代价限制。
  - 证据：[doi:10.1038/s41467-025-66748-y, p.2]；[doi:10.1038/s41467-025-66748-y, p.16]
- **baseline：** 在同一数据上，RF/XGBoost/MLP 的比较显示 MLP 优于树模型，而 Modlamp 与 iFeatures 明显优于 AutoEncoder/ESM 的数据驱动表征。
  - 证据：[doi:10.1038/s41467-025-66748-y, p.4]
- **baseline：** 与其他 ML 筛选方法相比，作者主张 TARSA 更快、平均预测抑制率更高，但该比较主要来自文内实验而非独立复现基准。
  - 证据：[doi:10.1038/s41467-025-66748-y, p.6]
- **data：** 训练数据包含 Mastoparan MDA-MB231 与 Mastoparan PBMC 两个各 210 条的连续数据集，以及 590 条 CancerPPD 二分类数据。
  - 证据：[doi:10.1038/s41467-025-66748-y, p.4]
- **data：** 筛选数据包括 PDB12mer 1.36M、PDB_large 36M、GEN12mer 30M；其中 PDB 片段来自结构中经 DSSP 标注的螺旋段。
  - 证据：[doi:10.1038/s41467-025-66748-y, p.2]；[doi:10.1038/s41467-025-66748-y, p.4]
- **data：** 实验材料包括 105 条 SPOT 合成肽、其中 15 条高纯度合成肽，以及 MCF10A、MCF7、MDA-MB-231、TamR3、PBMC 和 RBC 的体外测定。
  - 证据：[doi:10.1038/s41467-025-66748-y, p.9]；[doi:10.1038/s41467-025-66748-y, p.15]
- **declared_resources：** 三名健康志愿者的静脉血用于 PBMC/RBC 测定，研究已获 UBC Research Ethics Board 批准（H21-01910）。
  - 证据：[doi:10.1038/s41467-025-66748-y, p.13]；[doi:10.1038/s41467-025-66748-y, p.15]
- **declared_resources：** MCF10A、MCF7、MDA-MB-231 来自 ATCC，TamR3 由 Euphemia Leung 提供；细胞均在 RPMI 条件下培养。
  - 证据：[doi:10.1038/s41467-025-66748-y, p.15]
- **declared_resources：** 105 条肽由 Kinexus 采用 cellulose support 的 SPOT synthesis 制备，随后切下并回收为游离肽。
  - 证据：[doi:10.1038/s41467-025-66748-y, p.14]
- **declared_resources：** 高纯度肽购自 Peptide 2.0，并通过 HPLC 与 mass spectrometry 质控；体外筛选使用 PrestoBlue、LDH 和 hemolysis assay。
  - 证据：[doi:10.1038/s41467-025-66748-y, p.14]；[doi:10.1038/s41467-025-66748-y, p.15]
- **declared_resources：** 代码以 MIT license 公开在 GitHub，并有 Zenodo 归档；GEN12mer rollout 使用 14 张 Tesla V100 GPU。
  - 证据：[doi:10.1038/s41467-025-66748-y, p.15]；[doi:10.1038/s41467-025-66748-y, p.14]
- **limitations：** 训练集高度偏向 210 条 Mastoparan 衍生物，组成相对同质，作者自己也承认这限制了泛化。
  - 证据：[doi:10.1038/s41467-025-66748-y, p.10]；[doi:10.1038/s41467-025-66748-y, p.12]
- **limitations：** 2D-PCA 会损失高维 ESM 嵌入的大量信息，且容易出现点重叠，使不同肽难以区分。
  - 证据：[doi:10.1038/s41467-025-66748-y, p.13]
- **limitations：** 模型只在 MDA-MB-231 与 PBMC 上训练，因而对 MCF10A 的毒性泛化不足，提示需要加入更多阴性与细胞系特异数据。
  - 证据：[doi:10.1038/s41467-025-66748-y, p.10]；[doi:10.1038/s41467-025-66748-y, p.13]
- **limitations：** 作者也指出，现阶段结果仍以第一轮候选发现为主，后续需要更大、更异质的数据集与迭代优化来提升选择性。
  - 证据：[doi:10.1038/s41467-025-66748-y, p.12]；[doi:10.1038/s41467-025-66748-y, p.13]
- **method：** 作者先用 Mastoparan 相关连续活性数据训练 oracle proxy，并比较 Modlamp、iFeatures、inductive、AutoEncoder 与 ESM 等表征；随后用融合 MLP+CNN 的回归器作为后续筛选的活性预测器。
  - 证据：[doi:10.1038/s41467-025-66748-y, p.3]；[doi:10.1038/s41467-025-66748-y, p.4]
- **method：** TARSA 将 ESM 嵌入降到 2D-PCA 空间，把肽筛选建模为 MDP，再用 PPO 优化策略，并通过 MCMC 后验采样动态选择 activity cliffs / hotspot。
  - 证据：[doi:10.1038/s41467-025-66748-y, p.13]；[doi:10.1038/s41467-025-66748-y, p.14]
- **method：** 作者用 PDB_large 作为超大搜索空间，先以 200 万随机肽训练策略，再对剩余库做分批并行 rollout；GEN12mer 也按 14 个 batch、14 张 Tesla V100 GPU 执行筛选。
  - 证据：[doi:10.1038/s41467-025-66748-y, p.2]；[doi:10.1038/s41467-025-66748-y, p.14]
- **method：** 在 PepSce 的后续阶段，作者用 CancerPPD/非 ACP 二分类模型做共识过滤，并按 PBMC 毒性阈值继续缩小候选集，最后选出 105 条肽进入 SPOT 合成与体外测试。
  - 证据：[doi:10.1038/s41467-025-66748-y, p.3]；[doi:10.1038/s41467-025-66748-y, p.9]
- **results：** TARSA 在 PDB_large 上 14 天完成筛选，得到 320 万个预测抑制率 >40% 的唯一 motif，并识别出 450 万条平均预测抑制率 45.2% 的肽。
  - 证据：[doi:10.1038/s41467-025-66748-y, p.4]
- **results：** 在 GEN12mer 上，算法发现 350 万条平均预测抑制率 44.8% 的肽，把搜索空间压缩了 92.5%；在 PDB12mer 上，发现集的平均抑制率 44.9% 高于随机集的 29.8%。
  - 证据：[doi:10.1038/s41467-025-66748-y, p.4]；[doi:10.1038/s41467-025-66748-y, p.6]
- **results：** 105 条合成肽里有 15 条在 25 μM 下使 MDA-MB-231 存活率下降超过 60%；其中 7 条对 MDA-MB-231 的 IC50 低于 30 μM，LLQWLLKRLKAK、IILKKLLDFILK、TLLTAIVKLFLK 对 PBMC/RBC 至少 5.5 倍选择性。
  - 证据：[doi:10.1038/s41467-025-66748-y, p.9]
- **results：** AA-MD 结果显示三条 lead 在 1 μs 内与膜接触数上升并更深插入膜；但它们对 MCF10A/MCF7/TamR3 并未表现出理想的癌-正常细胞线选择性。
  - 证据：[doi:10.1038/s41467-025-66748-y, p.10]；[doi:10.1038/s41467-025-66748-y, p.12]

## 页码证据

- [doi:10.1038/s41467-025-66748-y, p.10]
- [doi:10.1038/s41467-025-66748-y, p.13]
- [doi:10.1038/s41467-025-66748-y, p.1]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
