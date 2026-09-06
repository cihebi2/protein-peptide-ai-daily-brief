# Enhancing missense variant pathogenicity prediction with protein language models using VariPred

- **论文 ID：** `EVIW-D719F0DEC8B7742D`
- **期刊 / 来源：** Sci Rep
- **发表时间：** 2024 Apr 7
- **DOI：** [10.1038/s41598-024-51489-7](https://doi.org/10.1038/s41598-024-51489-7)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `论文声明资源` / `语言模型`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者提出 VariPred：一个基于 ESM-1b 的 twin-network 序列分类框架，结合 wildtype/mutant residue embeddings 与 LLR，在多个公开 benchmark 上优于 PolyPhen-2、FATHMM、REVEL、MetaLR、ESM variant 和 3Cnet。

## 创新边界

`创新主要在冻结 pLM 上的输入拼接与浅层分类头，不在 pLM 预训练本身或新的湿实验。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在缺乏高质量结构、MSA 和手工特征时，如何仅用蛋白序列更准确地预测 missense variant 的致病性，并降低 type 2 data circularity 对评估的干扰。

## 方法

- 从野生型与突变序列PLM表示构建变异特征，监督训练致病/中性分类。

## 数据与基准

- 六个variant impact基准，包含疾病和中性变体并讨论data circularity。

## 比较基线

- Missense3D及结构、进化和其他PLM变异预测器。

## 结果证据

- 论文报告多数基准达到或超过SOTA，且无需结构和预处理；为临床意义计算分类。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 长序列ESM-2成本高，数据循环/基因重叠可高估性能；模型输出不等同于临床判定。

## 仍未知

- 补充材料中的更细消融和超参数搜索细节未在冻结页中完整展开。
- GitHub 仓库内容与脚本的可复现性未独立核验。
- 公开基准的标签冲突与历史版本差异对最终分数的具体影响仍不可完全量化。

## Pi 结构化证据摘录

- **baseline：** 对照方法覆盖 ESM variant、3Cnet、PolyPhen-2、FATHMM、REVEL 和 MetaLR，既包括无监督 pLM 基线，也包括传统机器学习与集成模型。
  - 证据：[doi:10.1038/s41598-024-51489-7, p.1]；[doi:10.1038/s41598-024-51489-7, p.2]；[doi:10.1038/s41598-024-51489-7, p.4]
- **baseline：** 作者强调 3Cnet 依赖 MSA、物化性质、motif/active site 以及 SNVBox 的 85 项特征，而 PolyPhen-2 和 FATHMM 也依赖更重的预处理与外部特征。
  - 证据：[doi:10.1038/s41598-024-51489-7, p.2]；[doi:10.1038/s41598-024-51489-7, p.6]；[doi:10.1038/s41598-024-51489-7, p.9]
- **baseline：** ESM variant 只是零样本基线，只用 ESM-1b 的 LLR 做病理性判别；VariPred 和 3Cnet 则是需要监督训练的深度学习对照。
  - 证据：[doi:10.1038/s41598-024-51489-7, p.2]；[doi:10.1038/s41598-024-51489-7, p.3]
- **data：** 训练集沿用 3Cnet 划分，原始来源是 ClinVar 72,470 条 curated missense variants 与 GnomAD 60,614 条 exome variants；去掉 simulated pathogenic data 和重复项后，作者实际用于训练的规模变为 ClinVar 72,466 条、GnomAD 59,018 条。
  - 证据：[doi:10.1038/s41598-024-51489-7, p.8]
- **data：** ClinVar 测试集包含 21,125 条记录，跨模型可比的 common test set 为 12,853 条；作者还构造了序列相似度 ≤30% 的 no-homology split，用于检验未见基因上的泛化。
  - 证据：[doi:10.1038/s41598-024-51489-7, p.8]；[doi:10.1038/s41598-024-51489-7, p.4]；[doi:10.1038/s41598-024-51489-7, p.5]
- **data：** SwissvarFilteredMix 与 VaribenchSelectedPure 经过 ANNOVAR 和 RefSeq/Entrez 重注释后，原始规模分别为 1153 benign 加 1023 pathogenic，以及 3629 benign 加 2122 pathogenic；跨工具可比的共同子集最后分别剩余 1603 和 1837 个变体。
  - 证据：[doi:10.1038/s41598-024-51489-7, p.9]
- **declared_resources：** 作者声明用于复现的 data 与 code 都公开在 GitHub 仓库 https://github.com/wlin16/VariPred.git。
  - 证据：[doi:10.1038/s41598-024-51489-7, p.12]
- **declared_resources：** 实现与评估还明确使用了 Biopython 1.80、Python 3.9、ANNOVAR、ESM tokenizer，以及一块 12GB GPU（Nvidia GTX 1080Ti）进行推断。
  - 证据：[doi:10.1038/s41598-024-51489-7, p.6]；[doi:10.1038/s41598-024-51489-7, p.9]；[doi:10.1038/s41598-024-51489-7, p.12]
- **limitations：** 作者明确指出，SwissvarFilteredMix 与 VaribenchSelectedPure 这两个老基准与 ClinVar 之间存在标签冲突和历史版本差异，因此性能下降未必完全反映模型缺陷。
  - 证据：[doi:10.1038/s41598-024-51489-7, p.7]
- **limitations：** VariPred 目前只使用序列信息，作者也承认未来若加入结构信息、功能数据或更生物学合理的数据增强，性能可能继续提升。
  - 证据：[doi:10.1038/s41598-024-51489-7, p.7]
- **limitations：** 即便在去同源 split 下仍保持较好结果，但相较标准 split 指标下降明显，说明对真正未见蛋白的泛化仍然弱于同一分布内测试。
  - 证据：[doi:10.1038/s41598-024-51489-7, p.4]；[doi:10.1038/s41598-024-51489-7, p.5]；[doi:10.1038/s41598-024-51489-7, p.7]
- **limitations：** 阈值 0.2 是在验证集上按 MCC 选择的，因训练数据明显偏向 neutral variants，因此该操作点对数据分布较敏感。
  - 证据：[doi:10.1038/s41598-024-51489-7, p.12]
- **method：** 先比较 ESM-1b、ESM-1v、ESM-2 三种 pLM，并分别测试仅 LLR、仅 embeddings、以及 LLR+embeddings 的三种输入方式，最终选择 ESM-1b 作为 VariPred 的特征提取器。
  - 证据：[doi:10.1038/s41598-024-51489-7, p.2]；[doi:10.1038/s41598-024-51489-7, p.3]；[doi:10.1038/s41598-024-51489-7, p.10]
- **method：** VariPred 采用 twin-network/Siamese 式流程，把 wildtype 与 mutant 序列分别送入同一个 pLM，只取突变位点的 residue embedding，再将两侧表示拼接后送入 FNN 分类器。
  - 证据：[doi:10.1038/s41598-024-51489-7, p.2]；[doi:10.1038/s41598-024-51489-7, p.10]；[doi:10.1038/s41598-024-51489-7, p.12]
- **method：** 作者对长序列做 1022 长度截断，提取 1280 维 embedding，并把 LLR 追加到 2560 维表示后形成 2561 维输入；FNN 使用一层隐藏层、LeakyReLU、dropout 0.5、学习率 0.0001，输出阈值设为 0.2。
  - 证据：[doi:10.1038/s41598-024-51489-7, p.9]；[doi:10.1038/s41598-024-51489-7, p.10]；[doi:10.1038/s41598-024-51489-7, p.12]
- **method：** 评估设计同时包含 ClinVar 常规测试、去同源 split、balanced-label 子集，以及 SwissvarFilteredMix/VaribenchSelectedPure 的 Type 2 circularity 检测，以检验模型是否只是记住基因标签。
  - 证据：[doi:10.1038/s41598-024-51489-7, p.4]；[doi:10.1038/s41598-024-51489-7, p.5]；[doi:10.1038/s41598-024-51489-7, p.8]；[doi:10.1038/s41598-024-51489-7, p.9]
- **results：** 在 ClinVar 上，LLR-only 的 MCC 以 ESM-1b 最佳（0.600），embedding-only 将 MCC 提升到 0.746，LLR+embeddings 再升至 0.751，说明表示学习比单独阈值更强。
  - 证据：[doi:10.1038/s41598-024-51489-7, p.3]
- **results：** 在 ClinVar common test set 上，VariPred 的 MCC 为 0.714，优于 3Cnet（0.673）、ESM variant（0.649）、REVEL（0.537）、MetaLR（0.513）、PolyPhen-2（0.521）和 FATHMM（0.379）。
  - 证据：[doi:10.1038/s41598-024-51489-7, p.4]
- **results：** 在 balanced-label 子集上，VariPred 的 MCC 为 0.623，而 3Cnet 为 0.567；两者 AUC-ROC 都约为 0.88，表明 VariPred 更不依赖多数类投机。
  - 证据：[doi:10.1038/s41598-024-51489-7, p.4]
- **results：** 在 no-homology split 中，VariPred 的 MCC 从 0.75 降到 0.65、AUC-ROC 从 0.93 降到 0.91，说明标准随机划分会高估其在未见基因上的泛化。
  - 证据：[doi:10.1038/s41598-024-51489-7, p.4]；[doi:10.1038/s41598-024-51489-7, p.5]
- **results：** 在 Type 2 circularity 检测里，VariPred 在 SwissvarFilteredMix 上取得最高 MCC 0.466；FATHMM 和 MetaLR 在 VaribenchSelectedPure 上分别为 0.327 和 0.221，均高于它们在 SwissvarFilteredMix 上的分数，符合基因级偏置会抬高单类基准的模式。
  - 证据：[doi:10.1038/s41598-024-51489-7, p.5]；[doi:10.1038/s41598-024-51489-7, p.6]

## 页码证据

- [doi:10.1038/s41598-024-51489-7, p.1]
- [doi:10.1038/s41598-024-51489-7, p.2]
- [doi:10.1038/s41598-024-51489-7, p.9]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
