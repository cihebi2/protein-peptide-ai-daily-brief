# Cytochrome P450 Enzyme Design by Constraining the Catalytic Pocket in a Diffusion Model

- **论文 ID：** `EVIW-1463F1CB9ABB78D8`
- **期刊 / 来源：** Research (Wash D C)
- **发表时间：** 2024 Jul 8
- **DOI：** [10.34133/research.0413](https://doi.org/10.34133/research.0413)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `扩散/生成`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

论文声称先通过祖先重建、回变和逐步前向累积识别出5个 founder residues，再提出“3-point fixation”口袋模型，最后把该原则嵌入P450Diffusion以生成并实验验证新的F6H型P450。

## 创新边界

`作者主张的是P450 catalytic pocket 设计原则与扩散式序列生成的组合创新；我无法仅凭冻结PDF独立验证其全球首创性。`。这不是全球首创性检索或独立复现结论。

## 研究问题

作者要解决的是：如何从天然P450的功能创新机制中提炼可迁移的口袋设计原则，并据此用生成式模型de novo设计具有目标F6H活性的P450酶。

## 方法

- 两阶段序列扩散：以226,509条天然P450序列预训练，再以19,234条CYP706X相关序列微调，并固定T114、F123、A220、M248、A317五个位点；从60,000条生成序列按序列质量、五残基三维口袋约束和apigenin结合模式筛选17条做酵母表达与HPLC功能实验。

## 数据与基准

- 预训练集226,509条P450序列；微调集19,234条CYP706X相关序列；功能机制部分包含祖先蛋白、反向突变和累积突变实验；最终从60,000条生成序列筛选17个设计。

## 比较基线

- 论文把目标定位为超越只做结构预测/设计的模型，并采用祖先序列重建、RMA、PFA和结构筛选作为机制与验证基线；未见与其他酶序列生成器在同一F6H湿实验面板上的直接头对头比较。

## 结果证据

- 17个设计中10个显示显著F6H活性，6个相对天然CYP706X1的scutellarein产量提高1.3至3.5倍；论文还用表达、纯化、结构建模与MD分析区分活性和非活性设计。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 功能验证集中于单一P450亚家族和F6H反应，不能直接外推到其他底物、反应类型或P450家族。 17个实验设计来自60,000条候选的强筛选，成功率反映的是完整筛选流程而非无筛选生成分布。 作者指出仍有五个创始残基之外的突变影响功能，并提到膜蛋白表达与纯化仍具挑战。

## 仍未知

- 19,202 与 19,234 的 fine-tuning 数据规模为何不一致。
- 5 个 founder residues 是否是唯一最小解，文中未做穷举证明。
- GitHub 仓库是否可直接复现全部实验与模型输出，冻结证据未核验。
- P450Diffusion 在其他 P450 功能或底物上的可迁移性仍未知。

## Pi 结构化证据摘录

- **baseline：** 实验对照主要使用天然 CYP706X1，并辅以 Cnan706X 和 Lsal706X 作为活性基准。
  - 证据：[doi:10.34133/research.0413, p.5]
- **baseline：** 作者把 pre-trained 模型与 fine-tuning 模型对比，指出后者生成序列更靠近 CYP706X 亚家族。
  - 证据：[doi:10.34133/research.0413, p.5]
- **baseline：** ancXY 和 ancY 作为非功能基线，而 CYP706X 亚家族祖先作为功能演化基线，用来定位 F6H 的出现位置。
  - 证据：[doi:10.34133/research.0413, p.3]
- **data：** 训练数据包含 226,509 条天然 P450 序列；微调数据集规模在文中分别写为 19,202 条和 19,234 条，存在内部计数不一致。
  - 证据：[doi:10.34133/research.0413, p.5]；[doi:10.34133/research.0413, p.9]
- **data：** 作者从 60,000 条生成序列中先筛到 77 条，再到 33 条、19 条，最终得到 17 条用于实验验证的设计。
  - 证据：[doi:10.34133/research.0413, p.10]
- **data：** 实验验证覆盖 17 个合成设计，以及 ancXY、ancX、ancX1、ancX2、ancX3 和 ancX-16 等重组蛋白。
  - 证据：[doi:10.34133/research.0413, p.10]
- **data：** ancX3 晶体在 1.34 M NaCl、13.4% PEG3350、0.1 M MgCl2 和 0.1 M imidazole 条件下获得，结构条目为 PDB 8JC2。
  - 证据：[doi:10.34133/research.0413, p.8]
- **declared_resources：** 作者在 Data Availability 中给出模型仓库 https://github.com/JiangLab2020/P450Diffusion，并声明有补充数据在线提供。
  - 证据：[doi:10.34133/research.0413, p.11]
- **declared_resources：** 实验与解析资源包括上海同步辐射光源 BL17U1，以及 ORISE Supercomputer 上完成的数值计算。
  - 证据：[doi:10.34133/research.0413, p.10]
- **declared_resources：** 论文还声明了资金来源、引物与质粒表、以及 PDB 结构资源 8JC2，说明研究具有完整的实验与计算支撑。
  - 证据：[doi:10.34133/research.0413, p.8]；[doi:10.34133/research.0413, p.10]；[doi:10.34133/research.0413, p.11]
- **limitations：** 作者明确承认，这 5 个 founder residues 可能不是唯一可行组合，仍可能存在其他等效残基方案。
  - 证据：[doi:10.34133/research.0413, p.7]
- **limitations：** P450 作为膜蛋白，酵母中表达量低且纯化困难，作者也指出需要更好的可溶性和折叠策略。
  - 证据：[doi:10.34133/research.0413, p.7]；[doi:10.34133/research.0413, p.8]
- **limitations：** 作者建议未来纳入 substrate-tunneling、整体稳定性等更多特征来改进生成模型。
  - 证据：[doi:10.34133/research.0413, p.8]
- **limitations：** 17 个候选里只有 10 个活性，说明筛选和模型仍有明显失败率，尚未达到高命中率设计。
  - 证据：[doi:10.34133/research.0413, p.5]
- **method：** 作者用TMHMM、Expresso、RAxML 和 FastML 重建 CYP706X/Y 家族祖先序列，并对 ancX3 进行晶体学解析。
  - 证据：[doi:10.34133/research.0413, p.8]
- **method：** 结构建模部分以 ancX3 晶体结构为模板，结合 ColabFold、RosettaRelax 和 RosettaLigand 完成 apigenin/CpdI 对接。
  - 证据：[doi:10.34133/research.0413, p.8]；[doi:10.34133/research.0413, p.9]
- **method：** MD 与自由能评估在 Amber20 中完成，祖先蛋白做 100 ns，设计体做 300 ns，并用 MM-PB/GBSA 分解结合能。
  - 证据：[doi:10.34133/research.0413, p.9]
- **method：** P450Diffusion 采用 VHSE8 编码和带 self-attention 的 U-Net 扩散模型，先用 226,509 条天然 P450 序列预训练，再用 CYP706X 相近序列微调。
  - 证据：[doi:10.34133/research.0413, p.5]；[doi:10.34133/research.0413, p.9]；[doi:10.34133/research.0413, p.10]
- **method：** 虚拟筛选把 60,000 条生成序列依次经 motif、esm-1v、AlphaFold2、ProteinMPNN、RosettaLigand 和 MD 过滤，最后保留 17 个候选。
  - 证据：[doi:10.34133/research.0413, p.10]
- **results：** ancXY 的 16 个口袋差异位点中，L220A/I114T/T317A/W123F/L248M 这 5 个替换构成 founder residues，任一回变都会削弱或失活。
  - 证据：[doi:10.34133/research.0413, p.3]；[doi:10.34133/research.0413, p.4]
- **results：** ancXY-5 获得 F6H 活性，作者据此提出“3-point fixation”模型，并把底物固定到近似 NAC 的反应构象。
  - 证据：[doi:10.34133/research.0413, p.4]
- **results：** 17 个候选设计中有 10 个显示显著 F6H 活性，其中 6 个的 scutellarein 产量达到 CYP706X1 的 1.3 到 3.5 倍。
  - 证据：[doi:10.34133/research.0413, p.5]
- **results：** 活性设计体的底物 RMSD 和整体蛋白 RMSD 都更低，说明稳定的结合与更好的全局结构稳定性相关。
  - 证据：[doi:10.34133/research.0413, p.6]
- **results：** 无活性设计体中的表面突变可破坏盐桥、螺旋或氢键，提示失活可能来自全局折叠和结合稳定性下降。
  - 证据：[doi:10.34133/research.0413, p.6]

## 页码证据

- [doi:10.34133/research.0413, p.11]
- [doi:10.34133/research.0413, p.1]
- [doi:10.34133/research.0413, p.5]
- [doi:10.34133/research.0413, p.7]
- [doi:10.34133/research.0413, p.9]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
