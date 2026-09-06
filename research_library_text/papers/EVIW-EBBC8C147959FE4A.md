# BoltzGen: Toward Universal Binder Design

- **论文 ID：** `EVIW-EBBC8C147959FE4A`
- **期刊 / 来源：** bioRxiv
- **发表时间：** 2025 Nov 24
- **DOI：** [10.1101/2025.11.20.689494](https://doi.org/10.1101/2025.11.20.689494)
- **范围标签：** `Pi 已解析` / `核心相关` / `有静态审计仓库` / `结构预测`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

提出 BoltzGen：一个把结构预测与 binder 生成统一到同一 all-atom diffusion 模型的通用设计系统，支持 covalent bond、binding site、structure template、secondary structure 等条件，并在多项湿实验中验证其对新靶点和多种配体模态的设计能力。

## 创新边界

`主要新意在统一式 all-atom 生成与设计流程、几何化残基编码和可控 specification language；但它显著继承 Boltz-2、ProteinMPNN、RFdiffusion 等既有框架，且论文未独立验证全局 prior-art novelty。`。这不是全球首创性检索或独立复现结论。

## 研究问题

如何构建一个可跨蛋白、肽、nanobody 与小分子等多模态目标的通用 binder 设计系统，并让模型同时具备结构预测、条件控制、候选排序和实验可验证的设计能力？

## 方法

- 全原子扩散模型以几何虚拟原子表示待设计残基；PDB、AFDB和自蒸馏结构联合训练折叠/设计任务；逆折叠、结构重预测及多指标rank-based选择。

## 数据与基准

- PDB实验结构、AlphaFold DB和Boltz-1自蒸馏结构；约11,000个历史实验设计用于筛选权重；8类湿实验活动、26个靶点。

## 比较基线

- RFdiffusion、RFdiffusionAA、AlphaFold3/Chai/Boltz折叠指标和5个已知benchmark靶点。

## 结果证据

- 对9个低相似新靶点，每种模态各测试15个设计，论文报告蛋白和纳米抗体均在66%靶点获得纳摩尔binder；不同活动还覆盖多类肽和靶标。

## 可用资源与代码关系

- [https://github.com/HannesStark/boltzgen](https://github.com/HannesStark/boltzgen)
  - 固定 commit：`a3149cf18eeb58648d1abbb27539bd73f746cdda`
  - 静态复用层级：B_static_partial_shape
  - 许可证边界：license_identified_MIT_terms_require_review

## 已知限制

- 治疗开发还需选择性和可开发性；73–76 aa在部分靶点发生ubiquitin记忆/多样性塌缩；作者明确不声称零失败或即插即用；预印本未同行评议。

## 仍未知

- 部分 wetlab 数据仍为临时保密，完整复核不可得。
- NPM1 案例的位点特异性主要是间接推断。
- 若干任务仅有弱结合信号，未能给出稳健 Kd。

## Pi 结构化证据摘录

- **baseline：** 主要对照方法包括 RFdiffusion 和 RFdiffusionAA；作者以 refolding 后 RMSD、Vendi score 和靶点依赖性来比较它们与 BoltzGen。
  - 证据：[doi:10.1101/2025.11.20.689494, p.33]；[doi:10.1101/2025.11.20.689494, p.34]；[doi:10.1101/2025.11.20.689494, p.48]；[doi:10.1101/2025.11.20.689494, p.49]
- **baseline：** 逆折叠对照包括 ProteinMPNN 和 SolubleMPNN，BoltzIF 的设计可折叠性大致相当，疏水性介于两者之间。
  - 证据：[doi:10.1101/2025.11.20.689494, p.19]；[doi:10.1101/2025.11.20.689494, p.49]
- **baseline：** rucaparib 部分还提到已有专家引导的专用方法可达到低 nM binder，作为 BoltzGen 的对比背景。
  - 证据：[doi:10.1101/2025.11.20.689494, p.8]；[doi:10.1101/2025.11.20.689494, p.29]
- **data：** 训练集由 2023-06-01 前的 PDB 生物学组装体及多种过滤后的链/界面组成，并结合约 500 万条 AFDB monomer distillation。
  - 证据：[doi:10.1101/2025.11.20.689494, p.38]；[doi:10.1101/2025.11.20.689494, p.39]
- **data：** protein-ligand、RNA、DNA-protein 蒸馏集分别来自 BindingDB/ChEMBL、Rfam、JASPAR/SELEX 等来源，并通过 Boltz-1 预测质量阈值筛选。
  - 证据：[doi:10.1101/2025.11.20.689494, p.38]
- **data：** 实验聚焦 9 个 novel targets，作者要求它们在 PDB 的 bound context 中无 >30% 序列相似的同类蛋白，且多为单体。
  - 证据：[doi:10.1101/2025.11.20.689494, p.5]；[doi:10.1101/2025.11.20.689494, p.21]；[doi:10.1101/2025.11.20.689494, p.52]；[doi:10.1101/2025.11.20.689494, p.53]
- **data：** Benchmark 还包括 PD-L1、TNFα、PDGFR、IL-7Rα 和 InsulinR 等已有已知 binder 的靶点，用于对照既有方法。
  - 证据：[doi:10.1101/2025.11.20.689494, p.9]；[doi:10.1101/2025.11.20.689494, p.10]
- **declared_resources：** 作者声明公开 training code、inference code、model weights 和 all designs，GitHub 为 https://github.com/HannesStark/boltzgen，且项目采用 MIT License。
  - 证据：[doi:10.1101/2025.11.20.689494, p.1]；[doi:10.1101/2025.11.20.689494, p.4]
- **declared_resources：** 作者还公开部分 wetlab 原始数据与 sensograms 于 HuggingFace 数据集链接，供结果复核。
  - 证据：[doi:10.1101/2025.11.20.689494, p.21]；[doi:10.1101/2025.11.20.689494, p.32]
- **limitations：** 作者明确指出高亲和力只是第一步，selectivity 和 developability 仍需进一步整合到生成流程中。
  - 证据：[doi:10.1101/2025.11.20.689494, p.34]
- **limitations：** 长度 73–76 aa 区间出现 ubiquitin memorization，导致多样性坍塌，作者计划在后续训练中下采样 ubiquitin。
  - 证据：[doi:10.1101/2025.11.20.689494, p.34]；[doi:10.1101/2025.11.20.689494, p.50]
- **limitations：** benchmark targets 的结果只能提供有限 generalization 证据，因为这些靶点本身已有训练数据中的已知 binder。
  - 证据：[doi:10.1101/2025.11.20.689494, p.10]；[doi:10.1101/2025.11.20.689494, p.34]
- **limitations：** NPM1 的活细胞定位实验不能严格证明结合位点就是无序区，论文也承认这一点主要依赖 BoltzGen 生成结构与后续预测。
  - 证据：[doi:10.1101/2025.11.20.689494, p.7]
- **method：** 模型采用单一 all-atom diffusion 架构，同时执行结构预测与设计；设计残基用固定 14-atom 表示，并通过几何方式编码残基类型。
  - 证据：[doi:10.1101/2025.11.20.689494, p.11]；[doi:10.1101/2025.11.20.689494, p.12]；[doi:10.1101/2025.11.20.689494, p.13]；[doi:10.1101/2025.11.20.689494, p.14]
- **method：** 可控性由 specification language 提供，支持 covalent bonds、structure conditioning、binding site 以及 secondary structure 约束，可用于 cyclic peptides、helicons 和 nanobody 模板化设计。
  - 证据：[doi:10.1101/2025.11.20.689494, p.14]；[doi:10.1101/2025.11.20.689494, p.15]
- **method：** 训练数据主要来自 PDB、AlphaFold DB 自蒸馏结构，以及 protein-ligand、RNA、protein-DNA 的 Boltz-1 蒸馏集；训练任务覆盖 folding、binder design、motif scaffolding 和 unconditional design。
  - 证据：[doi:10.1101/2025.11.20.689494, p.16]；[doi:10.1101/2025.11.20.689494, p.17]；[doi:10.1101/2025.11.20.689494, p.37]；[doi:10.1101/2025.11.20.689494, p.38]；[doi:10.1101/2025.11.20.689494, p.39]；[doi:10.1101/2025.11.20.689494, p.40]；[doi:10.1101/2025.11.20.689494, p.41]；[doi:10.1101/2025.11.20.689494, p.42]；[doi:10.1101/2025.11.20.689494, p.43]；[doi:10.1101/2025.11.20.689494, p.44]；[doi:10.1101/2025.11.20.689494, p.45]
- **method：** 生成后 pipeline 会进行 inverse folding、refolding、small-molecule affinity prediction、物理/可开发性打分，并用 quality-diversity selection 选出最终候选。
  - 证据：[doi:10.1101/2025.11.20.689494, p.19]；[doi:10.1101/2025.11.20.689494, p.20]
- **results：** 对 9 个 novel targets，nanobody 和 general protein 两条路线都分别达到 6/9 的 nM binder 命中率。
  - 证据：[doi:10.1101/2025.11.20.689494, p.6]；[doi:10.1101/2025.11.20.689494, p.21]
- **results：** 对 melittin、indolicidin 和 protegrin，设计蛋白/肽均获得了可测 binding，并在多种情况下抑制抗菌或溶血活性；melittin 与 indolicidin 可达 nM 或 sub-µM 量级。
  - 证据：[doi:10.1101/2025.11.20.689494, p.7]；[doi:10.1101/2025.11.20.689494, p.23]；[doi:10.1101/2025.11.20.689494, p.24]；[doi:10.1101/2025.11.20.689494, p.25]；[doi:10.1101/2025.11.20.689494, p.26]
- **results：** 针对 NPM1 的无序区，5 个候选里有 1 个在活细胞中稳定定位到 nucleoli，提供了体内结合证据。
  - 证据：[doi:10.1101/2025.11.20.689494, p.7]；[doi:10.1101/2025.11.20.689494, p.26]；[doi:10.1101/2025.11.20.689494, p.27]
- **results：** RagC 线性肽设计在 29 个测试中命中 7 个，最高 Kd 为 3.5 µM；RagA:RagC 的二硫键环肽在 24 个测试中有 14 个 binders，Kd 约 80–1100 µM。
  - 证据：[doi:10.1101/2025.11.20.689494, p.7]；[doi:10.1101/2025.11.20.689494, p.8]；[doi:10.1101/2025.11.20.689494, p.27]；[doi:10.1101/2025.11.20.689494, p.28]
- **results：** 对 Penguinpox cGAMP PDE 与 FhaB 的 nanobody 只在最高抗原浓度下出现弱信号，作者将其解释为至多 2 µM 级别的弱 binder。
  - 证据：[doi:10.1101/2025.11.20.689494, p.8]；[doi:10.1101/2025.11.20.689494, p.28]；[doi:10.1101/2025.11.20.689494, p.29]
- **results：** 小分子方面，rucaparib 设计中 5/6 可表达且 Kd 为 43–151.5 µM；未公开的 rhodamine 衍生物中 4 个设计的 Kd 为 30.9–252.2 µM。
  - 证据：[doi:10.1101/2025.11.20.689494, p.8]；[doi:10.1101/2025.11.20.689494, p.29]；[doi:10.1101/2025.11.20.689494, p.30]
- **results：** GyrA 设计中 1808 个候选里 352 个抑制 E. coli 生长超过 4×，其中 54 个在界面 alanine 突变后失活，支持目标位点特异性。
  - 证据：[doi:10.1101/2025.11.20.689494, p.9]；[doi:10.1101/2025.11.20.689494, p.31]；[doi:10.1101/2025.11.20.689494, p.32]
- **results：** 在 5 个 benchmark targets 上，nanobody 和 protein 两种模态都达到 4/5 的 nM 级命中率，并在 PDGFR 上出现 pM hits；唯一明显的非特异问题来自 IL-7Rα 对 HSA 的额外结合。
  - 证据：[doi:10.1101/2025.11.20.689494, p.10]；[doi:10.1101/2025.11.20.689494, p.32]
- **results：** 计算上，BoltzGen 的 folding 性能与 Boltz-2 相当，而在 target-conditioning diversity 评估中比 RFdiffusion / RFdiffusionAA 更能区分不同靶点。
  - 证据：[doi:10.1101/2025.11.20.689494, p.33]；[doi:10.1101/2025.11.20.689494, p.34]

## 页码证据

- [doi:10.1101/2025.11.20.689494, p.10]
- [doi:10.1101/2025.11.20.689494, p.16]
- [doi:10.1101/2025.11.20.689494, p.1]
- [doi:10.1101/2025.11.20.689494, p.21]
- [doi:10.1101/2025.11.20.689494, p.34]
- [doi:10.1101/2025.11.20.689494, p.4]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
