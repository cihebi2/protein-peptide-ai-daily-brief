# Co-design protein sequence and structure in discrete space via generative flow

- **论文 ID：** `EVIW-E1EB5AD1AEBADA84`
- **期刊 / 来源：** Bioinformatics
- **发表时间：** 2025 Apr 30
- **DOI：** [10.1093/bioinformatics/btaf248](https://doi.org/10.1093/bioinformatics/btaf248)
- **范围标签：** `Pi 已解析` / `核心相关` / `有静态审计仓库` / `扩散/生成`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

提出 CoFlow，一个把 joint discrete flow、结构 VQ-VAE 与带时间特征的 transformer 结合起来的蛋白共设计模型，可从全掩码或部分约束输入迭代生成 sequence 和 backbone，并在多个生成任务上优于 ESM3 与其他基线。

## 创新边界

`创新主要在于把现有离散流与 ESM3 风格的结构离散化整合到蛋白共设计框架中，尚未覆盖 side chains、protein complexes 或湿实验验证。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在离散表示空间中同时生成蛋白质序列与骨架结构，并在无条件与条件设定下保持两者一致性、可控性与可用性。

## 方法

- 将序列和结构token组成联合状态，以离散流从mask/noise迭代生成；约束任务固定motif token，仅生成其余部分。

## 数据与基准

- 评估无条件生成、序列/结构一致性、PDB新颖度及24个motif scaffold问题。

## 比较基线

- ESM3不同采样策略及序列或结构单独设计方法。

## 结果证据

- 论文报告无条件一致性约为ESM3的8倍，并解决24个motif任务中的20个；均为计算结构/序列评价。

## 可用资源与代码关系

- [https://github.com/LtECoD/CoFlow](https://github.com/LtECoD/CoFlow)
  - 固定 commit：`b3c9d609e5ff215bc731d946a410e6f51199bc3c`
  - 静态复用层级：C_license_or_component_gaps
  - 许可证边界：license_not_found_reuse_blocked

## 已知限制

- 没有证明生成蛋白可表达、折叠或保留motif功能；结果依赖结构预测指标。

## 仍未知

- Supplementary material 中的训练超参、预处理细节和部分采样策略未在本次页文本中完整展开。
- 论文未给出 side-chain 或 protein complex 设计的实证结果，因此这些场景的泛化能力不明确。
- 虽然提供了代码仓库地址，但本次冻结页未核验仓库内容、许可证和可执行性。

## Pi 结构化证据摘录

- **baseline：** 无条件生成中对比了 4 个 ESM3 sampling variants，并进一步与 FrameDiff、RFDiffusion、Proteus、Chroma、MultiFlow、Protpardelle 和 ProteinGenerator 这些方法做横向比较。
  - 证据：[doi:10.1093/bioinformatics/btaf248, p.4]；[doi:10.1093/bioinformatics/btaf248, p.5]
- **baseline：** 在条件任务里，motif-scaffolding 对照了 4 条 ESM3-based pipelines；folding 使用 ESM3 作为对照；inverse folding 还涉及 ProteinMPNN 这一序列设计基线。
  - 证据：[doi:10.1093/bioinformatics/btaf248, p.5]
- **baseline：** 作者也在消融中比较了 ESM3、ESM3 加 discrete flow，以及完整 CoFlow，用来说明时间特征和训练设定对生成质量的影响。
  - 证据：[doi:10.1093/bioinformatics/btaf248, p.6]
- **data：** 训练数据来自 MGnify30 中长度 40 到 512 的蛋白实例，因此作者将模型定位为适用于最长 512 residues 的生成。
  - 证据：[doi:10.1093/bioinformatics/btaf248, p.3]
- **data：** 无条件生成评估时，每个模型随机采样 500 个不同长度蛋白，并用 scRMSD、pTM、diversity 和 novelty 进行评价。
  - 证据：[doi:10.1093/bioinformatics/btaf248, p.4]
- **data：** 作者还使用 10K hold-out 数据集评估 token 预测准确率，motif-scaffolding 采用 24 个问题的数据集，folding 与 inverse folding 则使用 438 个 monomers 的测试集。
  - 证据：[doi:10.1093/bioinformatics/btaf248, p.5]
- **declared_resources：** 论文声明源代码与数据预处理脚本公开在 GitHub 和 Zenodo，便于复现其流程。
  - 证据：[doi:10.1093/bioinformatics/btaf248, p.1]；[doi:10.1093/bioinformatics/btaf248, p.7]
- **declared_resources：** 模型依赖 ESM3 的 structure VQ-VAE 来把连续坐标离散化并恢复三维结构，这是其关键外部组件。
  - 证据：[doi:10.1093/bioinformatics/btaf248, p.2]；[doi:10.1093/bioinformatics/btaf248, p.3]
- **declared_resources：** 训练语料明确使用 MGnify30，说明该工作依赖大规模公共蛋白序列/结构资源。
  - 证据：[doi:10.1093/bioinformatics/btaf248, p.3]
- **limitations：** 作者明确指出当前模型不生成 side-chain structures，这限制了分子建模的精细度与真实感。
  - 证据：[doi:10.1093/bioinformatics/btaf248, p.7]
- **limitations：** 论文只覆盖 monomer design，尚未扩展到 protein complexes，因此复合物层面的适用性仍未验证。
  - 证据：[doi:10.1093/bioinformatics/btaf248, p.7]
- **limitations：** 所有结果都来自 in silico experiments，仍需要 wet-lab validation 才能全面评估其实用性。
  - 证据：[doi:10.1093/bioinformatics/btaf248, p.7]
- **limitations：** 作者还承认模型参数规模受限，进一步 scaling data 或 model size 可能继续提升性能，但这一点尚未实证。
  - 证据：[doi:10.1093/bioinformatics/btaf248, p.7]
- **method：** 将蛋白表示为 sequence tokens 与 backbone structure tokens 的联合离散变量，用从 noise 到 data 的 joint discrete flow 建模，并把条件分布分解为序列与结构两部分做线性插值采样。
  - 证据：[doi:10.1093/bioinformatics/btaf248, p.2]；[doi:10.1093/bioinformatics/btaf248, p.3]
- **method：** 在反向采样中引入 balanced noise，使未掩码 token 在前期仍可回到 mask，同时保证最后一步不会再回掩码，从而支持更稳定的迭代 unmasking。
  - 证据：[doi:10.1093/bioinformatics/btaf248, p.3]
- **method：** 模型主体是 48 层 transformer，初始表示由 sequence 与 structure embeddings 求和构成，并加入 layer-wise Fourier time features，最终输出两个 categorical distributions。
  - 证据：[doi:10.1093/bioinformatics/btaf248, p.3]
- **method：** 训练时随机采样时间步，对插值后的蛋白状态预测原始样本，并以 cross-entropy loss 优化；采样时可从 fully masked 或 partially masked tokens 启动，以覆盖 unconditional 和 conditional generation。
  - 证据：[doi:10.1093/bioinformatics/btaf248, p.3]
- **results：** 在无条件生成中，CoFlow 的平均 scRMSD 为 3.1 Å，而 ESM3 各策略中的最低均值为 24.3 Å，作者据此称其 consistency 约高 8 倍，同时 pTM 更高且方差更低。
  - 证据：[doi:10.1093/bioinformatics/btaf248, p.4]
- **results：** 与 FrameDiff、RFDiffusion、Proteus、Chroma、MultiFlow、Protpardelle 和 ProteinGenerator 等基线相比，CoFlow 在 400 和 500 residues 的长蛋白上更占优势，novelty 大体可比，secondary-structure distribution 也更接近自然蛋白。
  - 证据：[doi:10.1093/bioinformatics/btaf248, p.5]
- **results：** 在 motif-scaffolding 中，CoFlow 解决了 24 个问题中的 20 个，超过 ESM3-based pipelines；在 folding 与 inverse folding 上也优于 ESM3，native sequence recovery 达到 0.56 对比 0.5。
  - 证据：[doi:10.1093/bioinformatics/btaf248, p.5]
- **results：** 消融实验显示，更多 sampling steps 会持续降低 entropy 并提高 pTM，但收益递减；作者因此选择 400 steps 作为效率与质量的折中。
  - 证据：[doi:10.1093/bioinformatics/btaf248, p.5]；[doi:10.1093/bioinformatics/btaf248, p.6]
- **results：** 把 ESM3 直接接入 discrete flow 并未达到 CoFlow 的效果，作者将改进归因于更宽的 masking ratio 以及显式 time feature。
  - 证据：[doi:10.1093/bioinformatics/btaf248, p.6]

## 页码证据

- [doi:10.1093/bioinformatics/btaf248, p.1]
- [doi:10.1093/bioinformatics/btaf248, p.5]
- [doi:10.1093/bioinformatics/btaf248, p.7]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
