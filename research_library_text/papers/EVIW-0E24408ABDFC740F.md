# Cyclic peptide structure prediction and design using AlphaFold2

- **论文 ID：** `EVIW-0E24408ABDFC740F`
- **期刊 / 来源：** Nature Communications（DOI 前缀识别）
- **发表时间：** 未记录
- **DOI：** [10.1038/s41467-025-59940-7](https://doi.org/10.1038/s41467-025-59940-7)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `肽与抗菌肽` / `结构预测` / `数据集/基准`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者提出 AfCycDesign，通过在 AlphaFold2/ColabDesign 中加入 cyclic relative positional encoding，完成 cyclic peptide 的结构预测、固定骨架序列重设计、从头 hallucination，并将所得 scaffold 用于 MDM2 和 Keap1 的 binder 设计与实验验证。

## 创新边界

`边界在于对现有 AlphaFold2/ColabDesign 的环化编码改造及其在 cyclic peptide 设计上的系统应用；我未独立核验其相对全部先前工作的全球新颖性。`。这不是全球首创性检索或独立复现结论。

## 研究问题

如何让 AlphaFold2 可靠处理头尾环化的 cyclic peptide，并进一步用于结构预测、序列重设计、从头 hallucination，以及面向蛋白靶标的 cyclic peptide binder 设计。

## 方法

- cycle-aware sequence/coordinate处理，结合AF2 structure prediction、hallucination和binder design。

## 数据与基准

- 大量cyclic peptide benchmark及MDM2/Keap1 binder设计；8条设计做X-ray。

## 比较基线

- 通用AF2/小肽预测和传统cyclic peptide设计。

## 结果证据

- 8条de novo设计晶体结构均与模型RMSD<1.0 Å，并从hallucinated scaffolds获得对MDM2和Keap1纳摩尔IC50 binder。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 实验成功集中于特定设计/靶点，IC50不等同于体内效果；训练数据生成质量影响模型。

## 仍未知

- 补充图表与补充数据未逐页展开，部分阈值与全部候选序列细节仍依赖 supplement
- 未独立评估所报 cyclic peptide 的体内稳定性、药代性质与脱靶风险
- 未对全部既有 cyclic peptide design 文献做全球新颖性复核

## Pi 结构化证据摘录

- **baseline：** 与 Rosetta-based cyclic peptide design 相比，AfCycDesign 在相同 backbone 上得到更高的 pLDDT，且高置信设计数量明显更多。
  - 证据：[doi:10.1038/s41467-025-59940-7, p.4]；[doi:10.1038/s41467-025-59940-7, p.10]
- **baseline：** 作者把 AfCycDesign 与去掉 cyclic offset 的设置、单序列与 MSA 设置、以及 Type 1/2/3 offset 进行了对照，说明 cyclic encoding 对准确率有实际贡献。
  - 证据：[doi:10.1038/s41467-025-59940-7, p.3]；[doi:10.1038/s41467-025-59940-7, p.4]；[doi:10.1038/s41467-025-59940-7, p.12]
- **baseline：** 在 10-residue hallucinated backbone 上，AfCycDesign 与 ProteinMPNN 都能得到高置信序列，但两者偏好的 backbone 并不相同。
  - 证据：[doi:10.1038/s41467-025-59940-7, p.7]
- **baseline：** 作者还对比了 Rosetta 结构采样与 AfCycDesign 的计算开销，给出单个案例从 120 compute hours 和 28,042 structures 降到单 GPU 约 2 minutes 的量级差异。
  - 证据：[doi:10.1038/s41467-025-59940-7, p.4]
- **data：** 结构预测基准使用了 80 个来自 PDB 的 NMR cyclic peptide，长度均小于 40 且不在 AlphaFold2 训练集设定范围内。
  - 证据：[doi:10.1038/s41467-025-59940-7, p.2]；[doi:10.1038/s41467-025-59940-7, p.12]
- **data：** 作者为 7–10 residue 和 11–13 residue 的 cyclic peptide 各自进行了 48,000 个 hallucinated models 的大规模采样，并用 torsion-bin clustering 归类。
  - 证据：[doi:10.1038/s41467-025-59940-7, p.4]；[doi:10.1038/s41467-025-59940-7, p.7]
- **data：** MDM2 设计先从 24,104 个高置信 hallucinated scaffold 出发，再 graft p53 的 5-residue motif，随后筛得 16 个候选进入实验。
  - 证据：[doi:10.1038/s41467-025-59940-7, p.8]；[doi:10.1038/s41467-025-59940-7, p.9]
- **declared_resources：** 计算资源包含 BOINC Rosetta@Home、单 GPU 推理/设计流程，以及用于对照的 Rosetta simple_cycpep_predict。
  - 证据：[doi:10.1038/s41467-025-59940-7, p.4]；[doi:10.1038/s41467-025-59940-7, p.12]；[doi:10.1038/s41467-025-59940-7, p.15]
- **declared_resources：** 实验资源包括 X-ray crystallography、APS 24ID-C、NSLS2 AMX/FMX、CSD/CCDC 与 PDB 数据提交。
  - 证据：[doi:10.1038/s41467-025-59940-7, p.12]；[doi:10.1038/s41467-025-59940-7, p.13]；[doi:10.1038/s41467-025-59940-7, p.15]
- **declared_resources：** 代码资源在文中以 ColabDesign 示例脚本和 Rosetta software suite 的形式公开，且未见独立项目仓库说明。
  - 证据：[doi:10.1038/s41467-025-59940-7, p.13]；[doi:10.1038/s41467-025-59940-7, p.12]
- **limitations：** 作者明确指出仅做了 X-ray crystallography 验证，未排除这些 peptide 在晶体之外还存在其他未观察到的构象。
  - 证据：[doi:10.1038/s41467-025-59940-7, p.11]
- **limitations：** 文中没有测定所报设计的 protease stability 或 serum stability，因此体内稳定性仍是未知。
  - 证据：[doi:10.1038/s41467-025-59940-7, p.11]
- **limitations：** 当前版本不支持 non-canonical amino acids，相关化学多样性仍需与 physics-based methods 结合。
  - 证据：[doi:10.1038/s41467-025-59940-7, p.11]
- **limitations：** 作者也承认 11–13 residue 的大尺度 hallucination 可能仍受采样不足限制，因为每个长度只采样了 48,000 个 scaffold。
  - 证据：[doi:10.1038/s41467-025-59940-7, p.7]
- **method：** 在 AlphaFold2 的 relative positional encoding 中加入自定义 cyclic offset matrix，使头尾残基按环化关系连接，从而支持 cyclic peptide 结构预测。
  - 证据：[doi:10.1038/s41467-025-59940-7, p.2]；[doi:10.1038/s41467-025-59940-7, p.12]
- **method：** 将 cyclic offset 接入 ColabDesign 的三阶段序列优化流程，用 CCE、pLDDT、PAE 和 contact loss 进行固定骨架设计与 hallucination。
  - 证据：[doi:10.1038/s41467-025-59940-7, p.4]；[doi:10.1038/s41467-025-59940-7, p.12]
- **method：** 在 binder 设计中，作者把 cyclic offset 只施加到 peptide binder 链，并结合 motif grafting、ProteinMPNN、Rosetta energy minimization 与 AfCycDesign 复评复杂结构。
  - 证据：[doi:10.1038/s41467-025-59940-7, p.8]；[doi:10.1038/s41467-025-59940-7, p.13]
- **results：** 在 80 个 PDB cyclic peptide 上，AfCycDesign 的中位 pLDDT 为 0.92，中位 backbone RMSD 为 0.8 Å；58/80 个案例达到 pLDDT > 0.7 且 RMSD < 1.5 Å。
  - 证据：[doi:10.1038/s41467-025-59940-7, p.2]
- **results：** 作者报告 RAR13.1 的 X-ray crystal structure 与设计模型高度一致，Cα RMSD 为 0.3 Å。
  - 证据：[doi:10.1038/s41467-025-59940-7, p.4]
- **results：** 7–13 residue 的 hallucinated peptide 中，8 个经 X-ray 验证的结构都与设计模型非常接近，RMSD 均小于 1.0 Å。
  - 证据：[doi:10.1038/s41467-025-59940-7, p.7]；[doi:10.1038/s41467-025-59940-7, p.11]
- **results：** MDM2 binder RMG_14 的 IC50 为 338.4 nM，RMG_14c 通过 5 个突变进一步提升结合亲和力，约提高 10 倍。
  - 证据：[doi:10.1038/s41467-025-59940-7, p.9]；[doi:10.1038/s41467-025-59940-7, p.10]
- **results：** Keap1 方向上，KC3、KC4、KC5 中至少三条 13-residue cyclic peptide 在竞争性 FP assay 中都优于线性 Nrf2 peptide，且 KC4 最强。
  - 证据：[doi:10.1038/s41467-025-59940-7, p.10]；[doi:10.1038/s41467-025-59940-7, p.11]

## 页码证据

- [doi:10.1038/s41467-025-59940-7, p.10]
- [doi:10.1038/s41467-025-59940-7, p.1]
- [doi:10.1038/s41467-025-59940-7, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
