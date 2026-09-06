# Structure prediction of protein-ligand complexes from sequence information with Umol

- **论文 ID：** `EVIW-9BE8411A125E7FEF`
- **期刊 / 来源：** bioRxiv preprint（DOI 前缀识别）
- **发表时间：** 未记录
- **DOI：** [10.1101/2023.11.03.565471](https://doi.org/10.1101/2023.11.03.565471)
- **范围标签：** `Pi 已解析` / `核心相关` / `有静态审计仓库` / `蛋白-配体` / `结构预测` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者提出 Umol：一个基于 Evoformer 的 protein-ligand co-folding 网络，可从序列信息、口袋标注和 ligand 化学图直接生成复合物结构，并在 PoseBusters 上达到较强的 docking 结果，优于多数 AI 基线并接近或部分超过传统方法。

## 创新边界

`本文的核心新意是 sequence-only 的蛋白-配体共折叠与 pocket-aware 结构生成；但冻结证据没有提供独立 prior-art 核验，因此不把“全球首创”当作已证事实。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在只给定蛋白序列、MSA、口袋位点和 ligand SMILES 的条件下，直接预测全原子 protein-ligand 复合物三维结构，并尽量替代依赖已知蛋白结构的 docking 流程。

## 方法

- AF2式protein trunk加ligand graph/pair modules，联合预测全复合物。

## 数据与基准

- PDBBind2020训练、PoseBusters和<30% identity unseen测试。

## 比较基线

- RoseTTAFold-AA、DiffDock类与经典docking。

## 结果证据

- 论文报告高精度unseen超过RoseTTAFold-AA，部分条件超过已知结构的经典docking；RAM/缺atom导致104例失败。

## 可用资源与代码关系

- [https://github.com/patrickbryant1/Umol](https://github.com/patrickbryant1/Umol)
  - 固定 commit：`4c0c72484b853a3d0cf2a2226284ac0fd8cb9a0b`
  - 静态复用层级：C_license_or_component_gaps
  - 许可证边界：license_not_found_reuse_blocked

## 已知限制

- 成功率仍有限，RAM/输入atom问题；为预印本，无实验。

## 仍未知

- 冻结证据未独立核验 GitHub 仓库中的权重、训练脚本和许可证是否足以直接复现。
- 未进行外部 prior-art 搜索，因此不把“全球首创”当作已验证事实。
- PoseBusters 与 PDBbind 的预处理细节主要依赖论文自述，冻结页外没有进一步核验。

## Pi 结构化证据摘录

- **baseline：** 论文把 AutoDock Vina、Gold、DiffDock、Uni-Mol、DeepDock、TankBind、EquiBind 和 RFAA 作为主要对照方法。
  - 证据：[doi:10.1101/2023.11.03.565471, p.5]；[doi:10.1101/2023.11.03.565471, p.16]；[doi:10.1101/2023.11.03.565471, p.17]
- **baseline：** 作者强调，Vina、Gold 等传统 docking 依赖 native holo protein structure，而 Umol 和 RFAA 试图在未知结构条件下预测蛋白-配体复合物；RFAA 还使用模板与 steric 信息，并不显式定义 pocket。
  - 证据：[doi:10.1101/2023.11.03.565471, p.2]；[doi:10.1101/2023.11.03.565471, p.16]
- **data：** 训练集来自 PDBbind 2019 处理版本，共得到 17936 个可生成特征的 protein-ligand complexes，并按 20% sequence identity 聚类后划分为 16420 个 train、845 个 valid、671 个 calibration 样本。
  - 证据：[doi:10.1101/2023.11.03.565471, p.10]
- **data：** 主评测使用 PoseBusters benchmark，共 428 个不在 PDBbind 2020 中的复合物，并按与训练集的 sequence identity 分层分析。
  - 证据：[doi:10.1101/2023.11.03.565471, p.11]；[doi:10.1101/2023.11.03.565471, p.7]
- **data：** 亲和力分析只保留 PDB 中高置信的 Kd(<1000 nM) 样本，共 45 个，其中 13 个的亲和力低于 10 nM。
  - 证据：[doi:10.1101/2023.11.03.565471, p.11]
- **declared_resources：** 训练使用 8×NVIDIA A100 GPU，batch size 为 24，训练约 13 天；单次推理蛋白-配体结构约 182 秒。
  - 证据：[doi:10.1101/2023.11.03.565471, p.13]；[doi:10.1101/2023.11.03.565471, p.15]
- **declared_resources：** 作者公开了 Umol 的 GitHub 仓库，以及用于计算图中指标的预测结构和训练输入特征的 Zenodo 记录。
  - 证据：[doi:10.1101/2023.11.03.565471, p.18]；[doi:10.1101/2023.11.03.565471, p.2]
- **declared_resources：** 方法链路显式使用 HHblits/HH-suite、MMseqs2、RDKit、OpenMM、JAX 和 Optax 等外部工具。
  - 证据：[doi:10.1101/2023.11.03.565471, p.10]；[doi:10.1101/2023.11.03.565471, p.12]；[doi:10.1101/2023.11.03.565471, p.13]；[doi:10.1101/2023.11.03.565471, p.15]
- **limitations：** 作者明确指出 2 Å 成功阈值是任意的，且很多样本只略高于阈值，说明评分可能需要更灵活的标准。
  - 证据：[doi:10.1101/2023.11.03.565471, p.5]；[doi:10.1101/2023.11.03.565471, p.9]
- **limitations：** 较大且更复杂的 ligand 更容易出现错误朝向；此外，部分样本因 >1000 residues 的内存限制被裁剪到 500 residues，可能影响评测。
  - 证据：[doi:10.1101/2023.11.03.565471, p.7]；[doi:10.1101/2023.11.03.565471, p.8]；[doi:10.1101/2023.11.03.565471, p.11]
- **limitations：** OpenMM relaxation 能减少 clash，但不会改善 ligand RMSD，且会把整体 SR 下降约 2%。
  - 证据：[doi:10.1101/2023.11.03.565471, p.15]
- **limitations：** 评分时作者默认预测与原生 ligand 的 atom order 相同，不做 symmetry correction，因此少量对称交换样本可能被低估。
  - 证据：[doi:10.1101/2023.11.03.565471, p.17]
- **method：** Umol 把蛋白表示为 MSA，把 ligand 表示为 SMILES 与 bond matrix，并通过 pocket 信息偏置 Evoformer 与 structure module 直接输出复合物三维结构，且不依赖模板或 native protein structure。
  - 证据：[doi:10.1101/2023.11.03.565471, p.4]；[doi:10.1101/2023.11.03.565471, p.12]
- **method：** 网络采用 AlphaFold2 风格的改造架构，包括 48 个 Evoformer blocks、8 个 structure blocks，以及 1–3 次 recycling；推理时固定做 3 次 recycling。
  - 证据：[doi:10.1101/2023.11.03.565471, p.4]；[doi:10.1101/2023.11.03.565471, p.12]；[doi:10.1101/2023.11.03.565471, p.13]
- **method：** 训练目标沿用 AlphaFold2 的 FAPE、AUX、Distance、MSA 和 Confidence 组合，并在 step 24500 后加入 ligand bond-length 的额外 L2 约束以改善几何合理性。
  - 证据：[doi:10.1101/2023.11.03.565471, p.13]
- **method：** 作者先用 RDKit 生成 100 个 ligand conformers，再选择最接近预测位置者；随后用 OpenMM 做快速 relaxation，以减少 clash 并微调 protein side chains。
  - 证据：[doi:10.1101/2023.11.03.565471, p.14]；[doi:10.1101/2023.11.03.565471, p.15]
- **results：** 在 PoseBusters 上，Umol 的 ligand RMSD≤2 Å 成功率为 45.3%，高于 RFAA 的 42% 和其他 AI 方法，但低于需要 native protein structure 的 AutoDock Vina 的 52.3%。
  - 证据：[doi:10.1101/2023.11.03.565471, p.5]；[doi:10.1101/2023.11.03.565471, p.7]；[doi:10.1101/2023.11.03.565471, p.16]；[doi:10.1101/2023.11.03.565471, p.17]
- **results：** 当阈值放宽到 2.35 Å 和 3 Å 时，Umol 进一步超过所有方法；在 3 Å 时其 SR 达到 69%，而 Vina 为 58%。
  - 证据：[doi:10.1101/2023.11.03.565471, p.5]；[doi:10.1101/2023.11.03.565471, p.6]
- **results：** 在 <30% sequence identity 子集上，Umol 的 SR 为 35.2%，是所有 AI 方法中最高；对应比较中 DiffDock 为 14.8%，Uni-Mol 为 21.1%，DeepDock 为 11.7%，TANKBind 为 1.6%，EquiBind 为 0%。
  - 证据：[doi:10.1101/2023.11.03.565471, p.6]；[doi:10.1101/2023.11.03.565471, p.7]
- **results：** ligand plDDT 与准确性和亲和力都呈正相关：80–100 分箱的 SR 为 72.3%，0–50 为 0%；当 ligand plDDT 高于 70 时，中位亲和力约 30 nM，而低于 60 时超过 500 nM。
  - 证据：[doi:10.1101/2023.11.03.565471, p.6]；[doi:10.1101/2023.11.03.565471, p.7]
- **results：** protein pocket 的 plDDT 与 pocket lDDT 的 Pearson 相关系数为 0.78，整体预测蛋白的平均 TM-score 为 0.96。
  - 证据：[doi:10.1101/2023.11.03.565471, p.6]；[doi:10.1101/2023.11.03.565471, p.22]

## 页码证据

- [doi:10.1101/2023.11.03.565471, p.14]
- [doi:10.1101/2023.11.03.565471, p.2]
- [doi:10.1101/2023.11.03.565471, p.3]
- [doi:10.1101/2023.11.03.565471, p.6]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
