# De novo synthetic antimicrobial peptide design with a recurrent neural network

- **论文 ID：** `EVIW-647BFF7FAA5ECC23`
- **期刊 / 来源：** Protein Sci
- **发表时间：** 2024 Jul 11
- **DOI：** [10.1002/pro.5088](https://doi.org/10.1002/pro.5088)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `肽与抗菌肽`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

提出 AMPd-Up，一个基于标准 RNN language model 的 de novo 抗菌肽生成工具；作者声称它能优于若干现有生成方法，并通过体外验证在 58 条候选中得到 40 条具抗菌活性的序列。

## 创新边界

`创新边界主要是序列生成、候选筛选与体外验证，而不是新的蛋白结构预测或新的实验筛选平台。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在已知抗菌肽样本有限、人工设计效率低的情况下，如何自动生成新的短肽候选，并尽量保持抗菌活性、较低溶血性与足够新颖性。

## 方法

- 标准RNN语言模型逐残基生成不超过50 aa的序列，从多个随机初始化模型采样；以AMPlify、AMP Scanner v2和iAMPpred排序，再进行MIC和猪红细胞溶血实验。

## 数据与基准

- 训练集2253条AMP；计算评估对比LSTM、AMPGAN v2和HydrAMP；实验测试58条新生成候选，菌株包括E. coli与S. aureus。

## 比较基线

- 对比早期LSTM生成器、AMPGAN v2、HydrAMP，并用三种独立AMP预测器作为计算筛选基线。

## 结果证据

- AMPlify判断的生成AMP比例为95.50%，较最佳对照AMPGAN v2高4.60个百分点；58条测试肽中40条有抗菌活性，15条对革兰阴性/阳性菌均活跃，DeNo1007显示较强活性且无可观察溶血。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 训练集小；训练目标不使用MIC强度且不同实验室MIC不可直接比较；生成序列频繁出现LLKK/LKKL模式，显示模式偏置；体外验证范围有限。

## 仍未知

- 未评估对更广泛菌种、临床分离株或体内感染模型的效果。
- 未说明化学合成产率、稳定性、药代或系统毒理等更完整转化指标。
- 没有独立外部证据可在本次冻结证据中验证全局新颖性。

## Pi 结构化证据摘录

- **baseline：** 生成基线包括 LSTM language model、AMPGAN v2 和 HydrAMP；判别基线包括 AMPlify、AMP Scanner Vr.2 和 iAMPpred。
  - 证据：[doi:10.1002/pro.5088, p.3]；[doi:10.1002/pro.5088, p.4]；[doi:10.1002/pro.5088, p.12]
- **baseline：** 为公平比较，AMPGAN v2 只保留 antibacterial peptides；LSTM 用作者提供的生成集，HydrAMP 通过在线服务器获取。
  - 证据：[doi:10.1002/pro.5088, p.12]
- **data：** 训练数据来自 APD3 下载的 2571 条记录，去重并剔除非标准氨基酸后得到 2253 条序列。
  - 证据：[doi:10.1002/pro.5088, p.11]
- **data：** 横向比较时每种方法生成 2000 条序列并分 5 批评估；AMPd-Up 进一步生成 20,000 条序列，其中 14,188 条 complete、8,737 条 distinct。
  - 证据：[doi:10.1002/pro.5088, p.12]；[doi:10.1002/pro.5088, p.13]
- **data：** 用于实验验证的 58 条候选来自长度 ≤35 aa 的 7434 条序列池，按 AMPd-Up score 分层抽样并额外加入高频序列，形成 List A/B/C（38/4/16 条）。
  - 证据：[doi:10.1002/pro.5088, p.13]
- **declared_resources：** AMPd-Up 被声明为开源工具，GitHub 地址为 https://github.com/bcgsc/AMPd-Up，验证用模型文件可在 Zenodo 获取。
  - 证据：[doi:10.1002/pro.5088, p.10]；[doi:10.1002/pro.5088, p.13]
- **declared_resources：** 实现环境为 PyTorch 1.7.1 / Python 3.6.7，训练与相似性分析所用数据主要来自 APD3 和 DADP。
  - 证据：[doi:10.1002/pro.5088, p.11]；[doi:10.1002/pro.5088, p.13]
- **limitations：** 作者明确指出训练集只有 2253 条序列，规模仍偏小。
  - 证据：[doi:10.1002/pro.5088, p.10]
- **limitations：** 模型训练没有把 MIC 纳入目标，而 MIC 又会受实验协议差异影响，跨实验室比较有限。
  - 证据：[doi:10.1002/pro.5088, p.10]
- **limitations：** 完整序列与活性验证都依赖两个标准菌株和猪 RBC，尚不能推出对其他病原、体内效应或作用机制的普适结论。
  - 证据：[doi:10.1002/pro.5088, p.8]；[doi:10.1002/pro.5088, p.10]；[doi:10.1002/pro.5088, p.11]
- **method：** 以 APD3 中 2253 条非冗余、≤50 aa 的抗菌肽为训练集，训练只包含 20 种标准氨基酸和 EOS 的 21 维 one-hot RNN language model，使用 cross-entropy、SGD、dropout，并通过 5-fold CV 选参。
  - 证据：[doi:10.1002/pro.5088, p.11]；[doi:10.1002/pro.5088, p.12]
- **method：** 生成时从每个起始氨基酸自回归采样，单个模型实例最多给出 20 条候选；作者再用 1000 个随机初始化的模型实例扩增候选池。
  - 证据：[doi:10.1002/pro.5088, p.12]；[doi:10.1002/pro.5088, p.13]
- **method：** 评估阶段用 AMPlify、AMP Scanner Vr.2 和 iAMPpred 作为代理指标，并与 LSTM、AMPGAN v2、HydrAMP 等生成基线比较；体外则做 broth microdilution、MBC 和 RBC hemolysis assays。
  - 证据：[doi:10.1002/pro.5088, p.3]；[doi:10.1002/pro.5088, p.4]；[doi:10.1002/pro.5088, p.12]；[doi:10.1002/pro.5088, p.13]；[doi:10.1002/pro.5088, p.14]
- **results：** 按三种预测器评估，AMPd-Up 的估计生成准确率分别为 95.50%、100.00% 和 99.30%，均优于 LSTM、AMPGAN v2 与 HydrAMP。
  - 证据：[doi:10.1002/pro.5088, p.3]；[doi:10.1002/pro.5088, p.4]
- **results：** 生成序列整体富含 K/L，平均长度 28.90 aa；去除 incomplete 后平均长度 21.56 aa、平均净电荷 6.45，且与训练集平均相似度仅 49.97%，与已知 AMP 平均相似度 51.03%。
  - 证据：[doi:10.1002/pro.5088, p.4]；[doi:10.1002/pro.5088, p.5]
- **results：** 体外验证中 58 条候选有 40 条对至少一种菌株有效，15 条同时对 E. coli ATCC 25922 与 S. aureus ATCC 29213 有效；DeNo1007 对两菌株均达 MIC 4 μg/mL 且无可观溶血。
  - 证据：[doi:10.1002/pro.5088, p.8]；[doi:10.1002/pro.5088, p.9]；[doi:10.1002/pro.5088, p.10]

## 页码证据

- [doi:10.1002/pro.5088, p.10]
- [doi:10.1002/pro.5088, p.3]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
