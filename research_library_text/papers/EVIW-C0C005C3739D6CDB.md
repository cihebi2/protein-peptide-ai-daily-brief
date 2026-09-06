# Probabilistic generative transformer language models for generative design of molecules

- **论文 ID：** `EVIW-C0C005C3739D6CDB`
- **期刊 / 来源：** J Cheminform
- **发表时间：** 2023 Sep 25
- **DOI：** [10.1186/s13321-023-00759-z](https://doi.org/10.1186/s13321-023-00759-z)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `扩散/生成` / `语言模型`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者提出 GMTransformer，一种基于 blank-filling transformer 的概率生成模型，声称可在 SMILES、SELFIES 和 DeepSMILES 上生成高新颖性分子，并通过掩码替换解释生成过程，还能进行性质条件生成。

## 创新边界

`创新边界主要在于把 blank-filling 生成机制具体迁移到分子字符串设计；冻结材料内没有独立先验对照，无法验证其全球首创性。`。这不是全球首创性检索或独立复现结论。

## 研究问题

如何用可解释、数据效率更高的生成式语言模型在分子字符串空间中生成新分子，并支持掩码补全式的 tinkering design 与性质定向生成。

## 方法

- 以token插入和两侧空白动作逐步生成；比较三种分子字符串表示和tokenizer；在MOSES上评估并以logP/tPSA/QED分位数据训练条件模型。

## 数据与基准

- MOSES约193.7万分子，训练约160万、测试和scaffold测试各约17.6万；可用性声明另提到QM9。

## 比较基线

- MOSES中的VAE/GAN/自回归等生成模型及不同字符串表示。

## 结果证据

- SMILES版本报告novelty 96.83%、internal diversity 87.01%，并能改变生成属性分布；这些是计算生成统计。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 只使用2D字符串，不含3D构象；属性优化通过筛选/重训，不能保证合成或活性；“解释”主要是token动作概率，不是化学因果。

## 仍未知

- 冻结材料未提供独立 prior-art 对照，因此全球首创性无法确认。
- 论文给出的 GitHub 仓库可访问性与代码版本对应关系未被验证。
- SELFIES 结果的低 FCD 原因在文中仍未解释清楚。

## Pi 结构化证据摘录

- **baseline：** MOSES 参考基线包含 GCT-SGDR、VAE、AAE 和 char RNN，并报告了 valid、unique、IntDiv、FCD、Frag、Scaf 等指标。
  - 证据：[doi:10.1186/s13321-023-00759-z, p.5]
- **baseline：** 作者又把结果与 Gnaneshwar 的 score-based diffusion model 和 Wang 的 cTransformer 进行文字比较，强调 GMT-PE-SMILES 在部分指标上占优。
  - 证据：[doi:10.1186/s13321-023-00759-z, p.7]
- **data：** 主要实验数据来自 MOSES benchmark，数据集共 1,936,962 个分子结构，论文使用训练集与测试集开展实验。
  - 证据：[doi:10.1186/s13321-023-00759-z, p.5]；[doi:10.1186/s13321-023-00759-z, p.6]
- **data：** 条件生成数据集把 MOSES 训练集按 logP、tPSA、QED 的 top 50% 切分，每个子集 792,331 条，总集 1,584,662 条。
  - 证据：[doi:10.1186/s13321-023-00759-z, p.10]；[doi:10.1186/s13321-023-00759-z, p.11]
- **data：** 另有一个 QM9 训练实验使用 atom-level SMILES；作者说明 QM9 原始分子数据可从 quantum-machine.org 下载。
  - 证据：[doi:10.1186/s13321-023-00759-z, p.10]；[doi:10.1186/s13321-023-00759-z, p.14]
- **declared_resources：** 作者在摘要和数据可用性部分声称 source code and datasets 可通过 GitHub 仓库获取，并给出了修改后的代码地址。
  - 证据：[doi:10.1186/s13321-023-00759-z, p.1]；[doi:10.1186/s13321-023-00759-z, p.14]
- **declared_resources：** MOSES 平台、QM9 与 RDKit 是论文实验的关键外部资源，分别用于主 benchmark、补充训练和性质计算。
  - 证据：[doi:10.1186/s13321-023-00759-z, p.5]；[doi:10.1186/s13321-023-00759-z, p.10]；[doi:10.1186/s13321-023-00759-z, p.14]
- **limitations：** 作者明确指出，单靠结构指标时，生成样本与 druggability 和 biological processes 的相关性并不清楚，因此引入了 FCD 作为补充代理。
  - 证据：[doi:10.1186/s13321-023-00759-z, p.12]
- **limitations：** 作者也承认 GMT-SELFIES 的 FCD 表现偏低，且原因不够清楚；其他使用 SELFIES 的相关模型也有类似低 FCD 现象。
  - 证据：[doi:10.1186/s13321-023-00759-z, p.13]
- **limitations：** 条件训练依赖属性标注样本；当目标属性标注不足时，作者只能建议先做预训练再迁移微调。
  - 证据：[doi:10.1186/s13321-023-00759-z, p.11]
- **method：** 模型用 transformer 编码 canvas，再经线性层、softmax 和 MLP 依次选择填充位置、token，以及是否在左右生成新的 blank。
  - 证据：[doi:10.1186/s13321-023-00759-z, p.4]；[doi:10.1186/s13321-023-00759-z, p.5]
- **method：** 训练时随机采样分子、生成顺序 permutation 和中间 canvas，并对后续填充动作的对数概率求和优化。
  - 证据：[doi:10.1186/s13321-023-00759-z, p.5]
- **method：** 作者分别在 SMILES、SELFIES 与 DeepSMILES 上训练模型，并结合 atom-level tokenizer 与 SmilesPE tokenizer 做比较。
  - 证据：[doi:10.1186/s13321-023-00759-z, p.4]；[doi:10.1186/s13321-023-00759-z, p.9]；[doi:10.1186/s13321-023-00759-z, p.10]
- **method：** 条件生成通过选取 MOSES 训练集中 logP、tPSA、QED 各自 top 50% 的样本重新训练生成器；当标注较少时作者建议先预训练再迁移微调。
  - 证据：[doi:10.1186/s13321-023-00759-z, p.10]；[doi:10.1186/s13321-023-00759-z, p.11]
- **results：** GMT-SMILES、GMT-PE-SMILES、GMT-SELFIES 的 validity 分别为 85.87%、82.88%、100%，novelty 分别为 95.31%、88.29%、96.83%，IntDiv 分别为 85.69%、85.58%、87.01%。
  - 证据：[doi:10.1186/s13321-023-00759-z, p.6]
- **results：** 在 FCD/Test 上，GMT-PE-SMILES 最优，为 19.86%；作者还与 diffusion model 和 cTransformer 做了对比，声称该模型在多项指标上更优或相近。
  - 证据：[doi:10.1186/s13321-023-00759-z, p.7]
- **results：** 将训练样本减半后，多数指标仅小幅变化，作者据此主张模型具备较好的 data efficiency。
  - 证据：[doi:10.1186/s13321-023-00759-z, p.7]
- **results：** 掩码示例中，模型把被遮蔽的首 token 预测为 C 的概率为 0.895；在 F 位点的 tinkering 示例中，Br、F、Cl 的概率分别为 0.427、0.297、0.25。
  - 证据：[doi:10.1186/s13321-023-00759-z, p.7]；[doi:10.1186/s13321-023-00759-z, p.8]
- **results：** 训练过程表明，SMILES 模型在 100 epochs 后 validity 超过 80%，而 SELFIES 从训练初期到结束都保持 100% validity，Scaf/TestSF 也随 epoch 上升。
  - 证据：[doi:10.1186/s13321-023-00759-z, p.8]；[doi:10.1186/s13321-023-00759-z, p.9]
- **results：** 条件生成后，logP、tPSA、QED 三个生成集的分布都比整个 MOSES 训练集更接近对应 top 50% 训练子集；过滤后分别得到 16,748、16,643 和 17,082 个样本。
  - 证据：[doi:10.1186/s13321-023-00759-z, p.11]

## 页码证据

- [doi:10.1186/s13321-023-00759-z, p.13]
- [doi:10.1186/s13321-023-00759-z, p.14]
- [doi:10.1186/s13321-023-00759-z, p.1]
- [doi:10.1186/s13321-023-00759-z, p.3]
- [doi:10.1186/s13321-023-00759-z, p.5]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
