# GPSFun: geometry-aware protein sequence function predictions with language models

- **论文 ID：** `EVIW-19ED48AF3238BE4A`
- **期刊 / 来源：** Nucleic Acids Res
- **发表时间：** 2024 May 13
- **DOI：** [10.1093/nar/gkae381](https://doi.org/10.1093/nar/gkae381)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `论文声明资源` / `语言模型`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者提出 GPSFun，一个面向蛋白序列的网页服务，将 ESMFold、ProtTrans 和几何 GNN 组合到同一管线中，用于预测配体结合位点、GO、亚细胞定位和溶解度，并声称在多项基准上优于现有方法。

## 创新边界

`创新主要在多任务预测管线与几何编码的系统整合，而不是新的蛋白设计或生成框架；其核心仍建立在 ESMFold、ProtTrans、DSSP 和既有任务数据/方法之上。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在蛋白序列数量快速增长而功能注释仍然稀缺的背景下，构建一个无需 MSA、也不依赖实验解析结构、但仍能覆盖多类蛋白功能与性质任务的统一预测平台。

## 方法

- 用语言模型生成序列嵌入并预测结构，再以几何模型完成DNA、RNA、肽、ATP、HEM等位点及蛋白级功能预测。[doi:10.1093/nar/gkae381, p.1][doi:10.1093/nar/gkae381, p.2]

## 数据与基准

- 结合位点基准来自BioLiP，按2021-01-01前训练、2021-01-01至2023-03-29独立测试进行时间切分。[doi:10.1093/nar/gkae381, p.2]

## 比较基线

- 正文比较BLAST-KNN和无结构信息基线，并与既有单任务工具比较。[doi:10.1093/nar/gkae381, p.4][doi:10.1093/nar/gkae381, p.7]

## 结果证据

- 论文报告在多项任务优于其比较方法；这是基准预测结果，不是功能实验验证。[doi:10.1093/nar/gkae381, p.2][doi:10.1093/nar/gkae381, p.7]

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 结构由模型预测，且论文指出AlphaFold2流程对数据库外序列计算昂贵；时间切分不等同严格低同源外推。[doi:10.1093/nar/gkae381, p.2]

## 仍未知

- figshare 链接中的源码是否为完整可复现实验包，当前证据未核验。
- 是否存在更大规模、外部独立测试集上的稳健性结果，冻结页面未展示。
- 模型对低置信度 ESMFold 结构的敏感性没有系统量化。
- 与作者既有 GraphSite/LMetalSite/SPROF-GO 之外的独立 prior art 对照是否充分，当前证据不足以判断。

## Pi 结构化证据摘录

- **baseline：** 结合位点对比基线同时覆盖 sequence-based 与 structure-based 方法，包括 GraphSite、PepBind、PepBCL、TargetS、LMetalSite、GraphBind、GeoBind、aaRNA、PepNN、MaSIF-site、GraphPPIS、ScanNet、DELIA 和 IonCom。
  - 证据：[doi:10.1093/nar/gkae381, p.4]；[doi:10.1093/nar/gkae381, p.6]
- **baseline：** GO 对比基线包括 BLAST-KNN、DeepGOPlus、GOLabeler、Foldseek-KNN、DeepGraphGO 和 NetGO；亚细胞定位基线包括 DeepLoc 与 DeepLoc 2.0；溶解度基线包括 GraphSol、SoluProt、SWI 和 NetSolP。
  - 证据：[doi:10.1093/nar/gkae381, p.6]；[doi:10.1093/nar/gkae381, p.7]
- **baseline：** 作者还加入了 BLAST-KNN、Foldseek-KNN 和 no-structure baseline，对照说明结构信息与几何编码确实带来可测增益。
  - 证据：[doi:10.1093/nar/gkae381, p.7]；[doi:10.1093/nar/gkae381, p.6]
- **data：** 蛋白-配体结合位点基准来自 BioLiP2；作者按 2021-01-01 前后划分训练/独立测试集，并用 CD-HIT 去除 identity>25% 且覆盖度>30% 的冗余序列。
  - 证据：[doi:10.1093/nar/gkae381, p.2]
- **data：** 蛋白-蛋白与蛋白-金属离子结合位点数据直接沿用前作，而 GO、亚细胞定位和溶解度数据也分别沿用已有公开数据集。
  - 证据：[doi:10.1093/nar/gkae381, p.2]
- **declared_resources：** 作者声明源码和数据托管在 figshare DOI 10.6084/m9.figshare.25324903。
  - 证据：[doi:10.1093/nar/gkae381, p.7]
- **declared_resources：** GPSFun 网站免费开放、无需登录，也不收集 cookies 或个人信息。
  - 证据：[doi:10.1093/nar/gkae381, p.4]
- **declared_resources：** 部署使用 nginx、Go、Vue 3、MySQL、MongoDB、Mol* 与 Graphviz，任务运行在 NVIDIA Tesla V100 GPU 集群上。
  - 证据：[doi:10.1093/nar/gkae381, p.4]
- **limitations：** 网页服务存在明确操作约束：每批最多 20 条蛋白，结果可保留 2 个月，且首次初始化与模型加载需要少于 5 分钟、单条 500 aa 约 2 分钟。
  - 证据：[doi:10.1093/nar/gkae381, p.4]
- **limitations：** 本冻结证据中没有新的湿实验验证，效果主要来自公开基准集上的计算评估，因此外部真实场景泛化仍未被独立证明。
  - 证据：[doi:10.1093/nar/gkae381, p.2]；[doi:10.1093/nar/gkae381, p.4]；[doi:10.1093/nar/gkae381, p.7]
- **limitations：** 模型依赖 ESMFold 预测结构，并展示 pLDDT/pTM 作为置信度指标，所以性能上限仍受结构预测质量约束。
  - 证据：[doi:10.1093/nar/gkae381, p.4]；[doi:10.1093/nar/gkae381, p.2]
- **method：** 对输入 FASTA，GPSFun 先用 ESMFold 预测蛋白三维构象，再用 ProtTrans（ProtT5-XL-U50）提取序列嵌入作为输入特征。
  - 证据：[doi:10.1093/nar/gkae381, p.2]
- **method：** 模型把蛋白表示为半径图，残基作为节点，若 Cα 距离小于 15 Å 则连边，并显式编码主链与侧链的几何关系。
  - 证据：[doi:10.1093/nar/gkae381, p.2]
- **method：** 几何特征包含 SE(3)-invariant 的节点/边信息，侧链重原子质心也参与编码，以捕捉残基内与残基间的距离、方向、键角和扭转角。
  - 证据：[doi:10.1093/nar/gkae381, p.2]
- **method：** 图网络使用 attention-based message passing 更新节点，再用连接节点回写边特征，并加入全局节点更新模块。
  - 证据：[doi:10.1093/nar/gkae381, p.3]
- **method：** 训练阶段，结合 five-fold cross-validation 或多随机种子集成，配合 multi-task learning、label diffusion、Adam 优化器和 binary cross entropy loss。
  - 证据：[doi:10.1093/nar/gkae381, p.3]；[doi:10.1093/nar/gkae381, p.4]
- **results：** 在 10 个配体/离子结合位点测试集上，GPSFun 的 AUPR 都是最佳，分别达到 DNA 0.535、RNA 0.578、peptide 0.344、protein 0.485、ATP 0.723、HEM 0.811、Zn2+ 0.858、Ca2+ 0.578、Mg2+ 0.369 和 Mn2+ 0.719。
  - 证据：[doi:10.1093/nar/gkae381, p.6]
- **results：** 消融实验显示：用 ProtTrans 嵌入替代 MSA 特征可使十种 ligand 的平均 AUPR 提升 4.2%；去掉结构信息会使平均 AUPR 下降 19.3%；去掉几何 featurizer 再下降 11.5%。
  - 证据：[doi:10.1093/nar/gkae381, p.6]
- **results：** 在 GO、亚细胞定位和溶解度任务上，作者报告 GPSFun 优于 DeepGOPlus、DeepLoc、NetSolP 等方法，并在 GO 的 MF/BP/CC 上分别取得超过 11.6%、25.3% 和 5.8% 的 AUPR 提升。
  - 证据：[doi:10.1093/nar/gkae381, p.7]
- **results：** 表 2 和表 3 进一步显示，GPSFun 在亚细胞定位的 micro/macro AUPR 以及溶解度的 Acc、MCC、AUC、AUPR 上都达到最佳或接近最佳。
  - 证据：[doi:10.1093/nar/gkae381, p.6]

## 页码证据

- [doi:10.1093/nar/gkae381, p.4]
- [doi:10.1093/nar/gkae381, p.7]
- [doi:10.1093/nar/gkae381, p.1]
- [doi:10.1093/nar/gkae381, p.2]
- [doi:10.1093/nar/gkae381, p.4]
- [doi:10.1093/nar/gkae381, p.7]
- [doi:10.1093/nar/gkae381, p.2]
- [doi:10.1093/nar/gkae381, p.1]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
