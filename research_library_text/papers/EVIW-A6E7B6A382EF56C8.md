# SPOT: A machine learning model that predicts specific substrates for transport proteins

- **论文 ID：** `EVIW-A6E7B6A382EF56C8`
- **期刊 / 来源：** PLoS Biol
- **发表时间：** 2024 Sep 26
- **DOI：** [10.1371/journal.pbio.3002807](https://doi.org/10.1371/journal.pbio.3002807)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `论文声明资源`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者声称提出了 SPOT，这是首个可通用于多类 transporters、直接预测“特定 substrate–transporter 配对”的机器学习模型，并配套 web server 与 Python function 便于检索候选底物。[doi:10.1371/journal.pbio.3002807, p.1][doi:10.1371/journal.pbio.3002807, p.14][doi:10.1371/journal.pbio.3002807, p.16]

## 创新边界

`其新意主要在于把序列嵌入与分子嵌入结合，用于 transporter-substrate 二分类与 substrate class 预测；它是预测/排序工具，不是底物生成、蛋白设计或实验筛选流程本身。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在缺乏高质量负样本和充分实验注释的情况下，建立一个能跨 transporter family、低序列同一性和未见 substrate 进行泛化的模型，用于判断给定 small molecule 是否为特定 transport protein 的 substrate，并进一步预测 substrate class。

## 方法

- protein/substrate encoders与interaction classifier/ranker。

## 数据与基准

- transporter-substrate数据库和实验注释。

## 比较基线

- homology/传统ML。

## 结果证据

- 论文报告新候选/验证；仅明确实验写实验。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 负样本、transporter class偏差与实验coverage。

## 仍未知

- 残余 false negatives 的真实比例无法从文中直接量化。
- GO 与 UniProt 性能差异是否完全由注释质量造成，文中只是推测。
- Web server 当前可用性及仓库后续状态未在本次冻结证据外核验。

## Pi 结构化证据摘录

- **baseline：** 最主要的简单基线是 similarity-based homolog approach；当 k=1 时，accuracy 仅 64.2%、precision 78.9%、recall 76.5%，且 k 增大后 precision 继续下降。[doi:10.1371/journal.pbio.3002807, p.13]
  - 证据：[doi:10.1371/journal.pbio.3002807, p.13]
- **baseline：** 作者还用 one-hot encoded substrate 的方案做对照，在已见 substrate 子集上其 accuracy 为 88.2%、MCC 为 0.72、ROC-AUC 为 0.950，仍低于 SPOT。[doi:10.1371/journal.pbio.3002807, p.14]
  - 证据：[doi:10.1371/journal.pbio.3002807, p.14]
- **baseline：** 在 substrate class 任务上，作者将结果与 TranCEP 的 74.2% overall accuracy 对照，指出 SPOT 的架构和新数据集带来明显更高的分类性能。[doi:10.1371/journal.pbio.3002807, p.12]
  - 证据：[doi:10.1371/journal.pbio.3002807, p.12]
- **data：** 二分类主数据集最初由 4,775 个 GO pairs 与 15,864 个 UniProt pairs 组成，去重后为 18,006 个 unique transporter-substrate pairs；进一步过滤后得到 8,587 个二分类样本、5,882 个 transport proteins 和 364 个 substrates。[doi:10.1371/journal.pbio.3002807, p.3][doi:10.1371/journal.pbio.3002807, p.17][doi:10.1371/journal.pbio.3002807, p.18]
  - 证据：[doi:10.1371/journal.pbio.3002807, p.3]；[doi:10.1371/journal.pbio.3002807, p.17]；[doi:10.1371/journal.pbio.3002807, p.18]
- **data：** 二分类训练在正样本基础上扩展了随机采样负样本，最终形成 33,162 个 transporter-molecule datapoints，平均每个正样本对应约 3 个负样本。[doi:10.1371/journal.pbio.3002807, p.5][doi:10.1371/journal.pbio.3002807, p.17][doi:10.1371/journal.pbio.3002807, p.18]
  - 证据：[doi:10.1371/journal.pbio.3002807, p.5]；[doi:10.1371/journal.pbio.3002807, p.17]；[doi:10.1371/journal.pbio.3002807, p.18]
- **data：** 底物类别预测任务把底物映射到 7 个类别，最终使用 11,664 个 transport proteins，并保持训练/测试蛋白不重叠。[doi:10.1371/journal.pbio.3002807, p.4][doi:10.1371/journal.pbio.3002807, p.18]
  - 证据：[doi:10.1371/journal.pbio.3002807, p.4]；[doi:10.1371/journal.pbio.3002807, p.18]
- **data：** 外部验证使用了 Majd 等对 GalP 和 AAC 的 high-throughput screening 数据，每个 transporter 都对应 30 个候选化合物，且部分化合物无法映射到 InChI。[doi:10.1371/journal.pbio.3002807, p.14][doi:10.1371/journal.pbio.3002807, p.21]
  - 证据：[doi:10.1371/journal.pbio.3002807, p.14]；[doi:10.1371/journal.pbio.3002807, p.21]
- **declared_resources：** 论文声明代码、Jupyter notebooks 和数据集已公开：代码与 notebooks 在 GitHub 和 Zenodo，数据集在 Zenodo。[doi:10.1371/journal.pbio.3002807, p.1][doi:10.1371/journal.pbio.3002807, p.16]
  - 证据：[doi:10.1371/journal.pbio.3002807, p.1]；[doi:10.1371/journal.pbio.3002807, p.16]
- **declared_resources：** 作者提供了 web server `https://spot.cs.hhu.de`，并给出 Python function 与仓库链接 `https://github.com/AlexanderKroll/SPOT` 供使用者调用。[doi:10.1371/journal.pbio.3002807, p.14][doi:10.1371/journal.pbio.3002807, p.16]
  - 证据：[doi:10.1371/journal.pbio.3002807, p.14]；[doi:10.1371/journal.pbio.3002807, p.16]
- **limitations：** task-specific transporter representation 没有带来预期提升，作者认为一个重要原因是可用于微调的 positive transporter-substrate pairs 只有约 8,633 个，远少于此前 enzyme-substrate 任务的数据规模。[doi:10.1371/journal.pbio.3002807, p.15][doi:10.1371/journal.pbio.3002807, p.19][doi:10.1371/journal.pbio.3002807, p.20]
  - 证据：[doi:10.1371/journal.pbio.3002807, p.15]；[doi:10.1371/journal.pbio.3002807, p.19]；[doi:10.1371/journal.pbio.3002807, p.20]
- **limitations：** 负样本由采样构造，因此仍可能混入 false negatives；作者只是通过同源过滤与后验性能推断其比例较低，无法直接完全消除。[doi:10.1371/journal.pbio.3002807, p.4][doi:10.1371/journal.pbio.3002807, p.5][doi:10.1371/journal.pbio.3002807, p.15][doi:10.1371/journal.pbio.3002807, p.18]
  - 证据：[doi:10.1371/journal.pbio.3002807, p.4]；[doi:10.1371/journal.pbio.3002807, p.5]；[doi:10.1371/journal.pbio.3002807, p.15]；[doi:10.1371/journal.pbio.3002807, p.18]
- **limitations：** 作者明确指出，该模型最适合单个 transporter 搭配预选候选分子的场景；若对大量 transporters 和大量 molecules 批量筛选，约 11% false positive rate 会产生过多误报。[doi:10.1371/journal.pbio.3002807, p.16]
  - 证据：[doi:10.1371/journal.pbio.3002807, p.16]
- **limitations：** GO 来源测试点的表现弱于 UniProt 来源测试点，作者推测这可能反映 GO 注释质量较低，因此真实泛化性能仍存在一定不确定性。[doi:10.1371/journal.pbio.3002807, p.15][doi:10.1371/journal.pbio.3002807, p.22]
  - 证据：[doi:10.1371/journal.pbio.3002807, p.15]；[doi:10.1371/journal.pbio.3002807, p.22]
- **limitations：** 作者也承认，尽管 AlphaFold 类结构预测已很强，但当前结构表示并未超过序列表示，说明结构信息尚未被有效转化为更好的 function prediction。[doi:10.1371/journal.pbio.3002807, p.2][doi:10.1371/journal.pbio.3002807, p.15]
  - 证据：[doi:10.1371/journal.pbio.3002807, p.2]；[doi:10.1371/journal.pbio.3002807, p.15]
- **method：** 作者从 GO 和 UniProt 提取带实验或人工审校证据的 transporter-substrate pairs，合并去重后构建主数据集，并按蛋白不重叠的 80/20 方式划分训练/测试集。[doi:10.1371/journal.pbio.3002807, p.3][doi:10.1371/journal.pbio.3002807, p.16][doi:10.1371/journal.pbio.3002807, p.17][doi:10.1371/journal.pbio.3002807, p.18]
  - 证据：[doi:10.1371/journal.pbio.3002807, p.3]；[doi:10.1371/journal.pbio.3002807, p.16]；[doi:10.1371/journal.pbio.3002807, p.17]；[doi:10.1371/journal.pbio.3002807, p.18]
- **method：** 负样本不是数据库直接提供的，而是通过随机采样构造；作者优先采样与真底物结构相近的分子，并排除与高度相似蛋白已知底物冲突的样本，以降低 false negatives。[doi:10.1371/journal.pbio.3002807, p.4][doi:10.1371/journal.pbio.3002807, p.5][doi:10.1371/journal.pbio.3002807, p.17][doi:10.1371/journal.pbio.3002807, p.18]
  - 证据：[doi:10.1371/journal.pbio.3002807, p.4]；[doi:10.1371/journal.pbio.3002807, p.5]；[doi:10.1371/journal.pbio.3002807, p.17]；[doi:10.1371/journal.pbio.3002807, p.18]
- **method：** 蛋白表示使用 ESM-1b，分子表示使用 ChemBERTa 或 ECFP；最终把 transporter 与 molecule embedding 串接后输入 gradient boosted decision tree / XGBoost 分类器。[doi:10.1371/journal.pbio.3002807, p.5][doi:10.1371/journal.pbio.3002807, p.6][doi:10.1371/journal.pbio.3002807, p.19][doi:10.1371/journal.pbio.3002807, p.20]
  - 证据：[doi:10.1371/journal.pbio.3002807, p.5]；[doi:10.1371/journal.pbio.3002807, p.6]；[doi:10.1371/journal.pbio.3002807, p.19]；[doi:10.1371/journal.pbio.3002807, p.20]
- **method：** 超参数通过 5-fold CV 选择，并以 MCC 作为主要优化目标；底物类别任务还加入类别权重，并把不同 fold 的 protein sequence identity 控制在 60% 以下。[doi:10.1371/journal.pbio.3002807, p.6][doi:10.1371/journal.pbio.3002807, p.20]
  - 证据：[doi:10.1371/journal.pbio.3002807, p.6]；[doi:10.1371/journal.pbio.3002807, p.20]
- **method：** 作者还尝试微调 ESM-1b 形成 task-specific transporter representation，但在该任务上没有带来优于通用表示的提升。[doi:10.1371/journal.pbio.3002807, p.6][doi:10.1371/journal.pbio.3002807, p.15][doi:10.1371/journal.pbio.3002807, p.19][doi:10.1371/journal.pbio.3002807, p.20]
  - 证据：[doi:10.1371/journal.pbio.3002807, p.6]；[doi:10.1371/journal.pbio.3002807, p.15]；[doi:10.1371/journal.pbio.3002807, p.19]；[doi:10.1371/journal.pbio.3002807, p.20]
- **results：** 二分类最优模型为 ESM-1b + ChemBERTa，在独立测试集上达到 92.4% accuracy、0.961 ROC-AUC、0.80 MCC 和 0.88 precision。[doi:10.1371/journal.pbio.3002807, p.7][doi:10.1371/journal.pbio.3002807, p.8]
  - 证据：[doi:10.1371/journal.pbio.3002807, p.7]；[doi:10.1371/journal.pbio.3002807, p.8]
- **results：** 当测试蛋白与训练集最近序列相似度低于 40% 时，模型仍有 84.0% accuracy 和 0.56 MCC；对训练中未出现过的 substrate，accuracy 仍有 86.7%，MCC 为 0.61。[doi:10.1371/journal.pbio.3002807, p.8][doi:10.1371/journal.pbio.3002807, p.9]
  - 证据：[doi:10.1371/journal.pbio.3002807, p.8]；[doi:10.1371/journal.pbio.3002807, p.9]
- **results：** 按生命域划分时，Bacteria、Eukarya、Archaea 的 accuracy 分别为 95.3%、89.6% 和 97.5%；对应 MCC 分别为 0.875、0.727 和 0.934。[doi:10.1371/journal.pbio.3002807, p.10]
  - 证据：[doi:10.1371/journal.pbio.3002807, p.10]
- **results：** 底物类别模型达到 95.1% accuracy，并显著优于 TranCEP 报告的 74.2%；在 sequence identity <40% 的子集上仍有 60.2% accuracy，明显高于随机 14.3%。[doi:10.1371/journal.pbio.3002807, p.12]
  - 证据：[doi:10.1371/journal.pbio.3002807, p.12]
- **results：** 与简单 similarity-based baseline 相比，SPOT 的 accuracy、precision 和 recall 都更高；在 GalP 与 AAC 的 screening 数据上也分别取得 86.2% 和 81.5% accuracy。[doi:10.1371/journal.pbio.3002807, p.13][doi:10.1371/journal.pbio.3002807, p.14]
  - 证据：[doi:10.1371/journal.pbio.3002807, p.13]；[doi:10.1371/journal.pbio.3002807, p.14]
- **results：** 作者还报告，预测分数接近 0 或 1 的样本占 94.5%，这部分样本的 accuracy 达到 94.2%，说明输出分数与置信度有较强相关性。[doi:10.1371/journal.pbio.3002807, p.8]
  - 证据：[doi:10.1371/journal.pbio.3002807, p.8]

## 页码证据

- [doi:10.1371/journal.pbio.3002807, p.1]
- [doi:10.1371/journal.pbio.3002807, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
