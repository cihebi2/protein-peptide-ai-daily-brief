# A Diffusion-Based Framework for Designing Molecules in Flexible Protein Pockets

- **论文 ID：** `EVIW-87C7E30CF2A5F5BF`
- **期刊 / 来源：** bioRxiv preprint（DOI 前缀识别）
- **发表时间：** 未记录
- **DOI：** [10.1101/2025.05.27.656443](https://doi.org/10.1101/2025.05.27.656443)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白-配体` / `扩散/生成`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

提出 YuelDesign：一个联合生成 protein pocket 与 ligand 的 diffusion framework，使用 E3former 作为主干，并结合 EDM 与 D3PM，在 flexible pocket 场景中生成更可药、可合成且对接更优的分子。

## 创新边界

`本文的边界在于把 pocket flexibility 纳入联合生成与评测；我不把它当作已被独立 prior-art 证明的全局首创。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在柔性 protein pockets 中进行条件分子设计，同时显式建模 pocket 构象变化，以提升生成分子的 binding 相关性质与化学可行性。

## 方法

- 多构象pocket条件等变diffusion。

## 数据与基准

- protein-ligand complexes/MD conformers。

## 比较基线

- rigid-pocket TargetDiff/Pocket2Mol。

## 结果证据

- 论文报告更好pose/property；为计算。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 预印本、pocket ensemble成本、无实验。

## 仍未知

- 补充材料未展开，无法仅凭主文确认全部超参数、训练细节与采样配置。
- GitHub/Zenodo 仅在文中声明存在，未核验仓库内容或可运行性。
- 主文未提供湿实验验证，所有结果均为计算与对接评估。

## Pi 结构化证据摘录

- **baseline：** 主要 generative baselines 是 DiffSBDD 和 PMDM，文中多次将它们作为 rigid-pocket 对照方法。
  - 证据：[doi:10.1101/2025.05.27.656443, p.2]；[doi:10.1101/2025.05.27.656443, p.5]；[doi:10.1101/2025.05.27.656443, p.7]
- **baseline：** 对接与 pose 评估还使用 AutoDock Vina、MedusaDock 和 MedusaDock redocking；native ligands、DX4 与 CDK2 相关 PDB 结构作为具体参照。
  - 证据：[doi:10.1101/2025.05.27.656443, p.4]；[doi:10.1101/2025.05.27.656443, p.5]；[doi:10.1101/2025.05.27.656443, p.9]
- **data：** 主要数据来源是 Binding MOAD；文中写明该库约有 41,409 个 structural entries，其中 15,223 个带有 quantitative affinity measurements，并以 PDB 结构为基础整理。
  - 证据：[doi:10.1101/2025.05.27.656443, p.8]
- **data：** 每个复合物都保留 protein 与 ligand 的 3D spatial coordinates，并把 pocket 残基、蛋白原子和 ligand 原子统一编码为 atom tokens，以支持 joint generation。
  - 证据：[doi:10.1101/2025.05.27.656443, p.8]；[doi:10.1101/2025.05.27.656443, p.9]
- **data：** 作者对化学分析使用 MolVS、RDKit 和 SMARTS pattern；结构分析则追踪 bond length、atom-type transition、RMSD 和 bond count 变化。
  - 证据：[doi:10.1101/2025.05.27.656443, p.3]；[doi:10.1101/2025.05.27.656443, p.6]；[doi:10.1101/2025.05.27.656443, p.9]
- **data：** 蛋白-配体相互作用分析以 MedusaDock scores 和 AutoDock Vina scores 为主要打分指标，并在重对接中报告 pose RMSD。
  - 证据：[doi:10.1101/2025.05.27.656443, p.4]；[doi:10.1101/2025.05.27.656443, p.9]
- **declared_resources：** 作者声明计算资源来自 University of Virginia Research computing，并获得 NIH 1R35 GM134864 与 NSF 2210963 资助。
  - 证据：[doi:10.1101/2025.05.27.656443, p.10]
- **declared_resources：** 作者在文末声明数据和代码已放入 Zenodo，并给出两个 GitHub repositories：dokhlab/yuel_design 与 hust220/yuel_design。
  - 证据：[doi:10.1101/2025.05.27.656443, p.11]
- **declared_resources：** 文中未声明 new materials；可复用的核心输入主要是 Binding MOAD/PDB 结构数据与补充材料中的 tables 和 Movie S1。
  - 证据：[doi:10.1101/2025.05.27.656443, p.8]；[doi:10.1101/2025.05.27.656443, p.11]
- **limitations：** 作者明确指出，generated molecules 与 native ligands 的 similarity 仍然有限，说明 chemical space 仍未被充分覆盖。
  - 证据：[doi:10.1101/2025.05.27.656443, p.8]
- **limitations：** small rings 和其他 strained motifs 有过度表示的问题，因为初始采样阶段没有显式 chemical enforcement。
  - 证据：[doi:10.1101/2025.05.27.656443, p.4]；[doi:10.1101/2025.05.27.656443, p.8]
- **limitations：** 模型在 larger molecules 上性能下降，作者将原因归于高维表示和迭代去噪误差累积，并建议未来尝试 latent diffusion。
  - 证据：[doi:10.1101/2025.05.27.656443, p.8]
- **method：** YuelDesign 以 full-atom 表示同时建模 protein pocket 与 ligand，并用 E3former 作为主干网络，把 atom-level sequence features、pair features 和 3D coordinate information 结合起来处理 complex 结构。
  - 证据：[doi:10.1101/2025.05.27.656443, p.1]；[doi:10.1101/2025.05.27.656443, p.9]
- **method：** 模型使用 dual diffusion：EDM 负责连续坐标的去噪生成，D3PM 负责离散 atom types 的反向预测，二者共享 E3former features 和 diffusion time steps。
  - 证据：[doi:10.1101/2025.05.27.656443, p.1]；[doi:10.1101/2025.05.27.656443, p.9]
- **method：** E3former 借鉴 Evoformer stack，并通过 equivariant coordinate head 输出旋转/平移等变的 coordinate displacement，以保持生成结构的物理一致性。
  - 证据：[doi:10.1101/2025.05.27.656443, p.1]；[doi:10.1101/2025.05.27.656443, p.8]；[doi:10.1101/2025.05.27.656443, p.9]
- **method：** 训练与评估使用 Binding MOAD 结构复合物；作者将数据按 8:2 划分，并用 BLASTp、TM-align、pocket RMSD 以及 ligand Tanimoto 相似性过滤高度相似样本，以减少泄漏。
  - 证据：[doi:10.1101/2025.05.27.656443, p.8]
- **method：** 作者把 binding site 定义为与 ligand 任一原子距离 6 Å 内的 protein residues，并将 protein 与 molecular coordinates 拼接为单一 coordinate matrix，同时用 binary masks 区分来源。
  - 证据：[doi:10.1101/2025.05.27.656443, p.8]
- **method：** 评估流程覆盖 QED、Lipinski RO5、SAS、validity、functional group distribution、bond dynamics、pocket RMSD、AutoDock Vina、MedusaDock、redocking RMSD 以及 RDKit/Tanimoto similarity。
  - 证据：[doi:10.1101/2025.05.27.656443, p.2]；[doi:10.1101/2025.05.27.656443, p.3]；[doi:10.1101/2025.05.27.656443, p.4]；[doi:10.1101/2025.05.27.656443, p.5]；[doi:10.1101/2025.05.27.656443, p.9]
- **results：** 在生成分子质量上，YuelDesign 相比 DiffSBDD 和 PMDM 保持更高的 connectivity，并在不同分子大小下给出最低的 large-ring ratio。
  - 证据：[doi:10.1101/2025.05.27.656443, p.2]；[doi:10.1101/2025.05.27.656443, p.3]
- **results：** 在药物相似性指标上，YuelDesign 的 QED 整体高于两种基线，小分子场景下的 RO5 表现更好；SAS 差异不大，而 validity 基本接近 1.0。
  - 证据：[doi:10.1101/2025.05.27.656443, p.3]
- **results：** 功能基团分布与 native ligands 总体相近，alcohol 和 amine 最常见，但生成结果中 small rings 略有富集。
  - 证据：[doi:10.1101/2025.05.27.656443, p.3]；[doi:10.1101/2025.05.27.656443, p.4]
- **results：** 在 receptor 质量与结合姿态上，生成 pocket 的 median RMSD 为 1.8 Å；针对 3JQA，模型还能诱导新的 side-chain orientations、形成新的 polar contacts，并得到更好的 docking score 和更低的 redocking RMSD。
  - 证据：[doi:10.1101/2025.05.27.656443, p.4]
- **results：** CDK2 case study 显示，YuelDesign 能重现 K33-D145 salt bridge 的断裂与 D145 的构象适应，使 ligand 更接近 native bound state；rigid-pocket baselines 则难以实现这种变化。
  - 证据：[doi:10.1101/2025.05.27.656443, p.5]
- **results：** 对 denoising trajectory 的分析表明，atom types 多在最后 20 步稳定，bond changes 在后 50 步基本停止，coordinate RMSD 也在整个过程中持续下降。
  - 证据：[doi:10.1101/2025.05.27.656443, p.6]

## 页码证据

- [doi:10.1101/2025.05.27.656443, p.1]
- [doi:10.1101/2025.05.27.656443, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
