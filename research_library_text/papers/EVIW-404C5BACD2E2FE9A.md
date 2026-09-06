# TargetCLP: clathrin proteins prediction combining transformed and evolutionary scale modeling-based multi-view features via weighted feature integration approach

- **论文 ID：** `EVIW-404C5BACD2E2FE9A`
- **期刊 / 来源：** Brief Bioinform
- **发表时间：** 2025 Jan 23
- **DOI：** [10.1093/bib/bbaf026](https://doi.org/10.1093/bib/bbaf026)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `论文声明资源` / `语言模型`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者提出 TargetCLP：先从序列构建 PSSM-CLBP、RECM-CLBP、QLC 与 ESM-1b 四类特征，再用 differential evolution 学习加权融合，随后用 BTG 做特征选择，最后以 SnBiLSTM 完成 clathrin 预测。[doi:10.1093/bib/bbaf026, p.2][doi:10.1093/bib/bbaf026, p.4][doi:10.1093/bib/bbaf026, p.5][doi:10.1093/bib/bbaf026, p.8][doi:10.1093/bib/bbaf026, p.10]

## 创新边界

`其新意主要在特征变换、加权融合、BTG 选择和 SnBiLSTM 组合；冻结证据只支持与 Le et al. 的对比，不能据此验证全局新颖性。[doi:10.1093/bib/bbaf026, p.8][doi:10.1093/bib/bbaf026, p.9][doi:10.1093/bib/bbaf026, p.10]`。这不是全球首创性检索或独立复现结论。

## 研究问题

从蛋白序列中准确区分 clathrin 与 non-clathrin 蛋白，并尽量提升对未见数据的泛化能力；作者把这一任务定位为对疾病相关 clathrin 功能识别的计算预测问题。[doi:10.1093/bib/bbaf026, p.1][doi:10.1093/bib/bbaf026, p.2][doi:10.1093/bib/bbaf026, p.9]

## 方法

- 序列PLM与evolutionary/handcrafted features融合分类。

## 数据与基准

- clathrin/non-clathrin proteins。

## 比较基线

- 传统ML/PLM。

## 结果证据

- 论文报告超过baselines；为计算。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 类别/物种小、全蛋白功能分类。

## 仍未知

- 未独立核验 GitHub 仓库内容、可复现性与许可证边界
- 未见冻结证据支持全局 prior-art 结论，因此新颖性只能作论文内相对判断
- 正文在独立测试段落把训练集误写成 CL2481，疑似笔误；我按 CL2421 理解

## Pi 结构化证据摘录

- **baseline：** 主要外部基线是 Le et al. predictor；论文报告其在 CL2421 上的 Acc 为 91.70%、Sen 为 91.70%、Spe 为 91.60%、MCC 为 0.83。[doi:10.1093/bib/bbaf026, p.9]
  - 证据：[doi:10.1093/bib/bbaf026, p.9]
- **baseline：** 内部基线包括单视图特征、串联融合 S-Features 和加权融合 W-Features，用于证明 DE 权重学习与 BTG 的增益。[doi:10.1093/bib/bbaf026, p.6][doi:10.1093/bib/bbaf026, p.7][doi:10.1093/bib/bbaf026, p.8]
  - 证据：[doi:10.1093/bib/bbaf026, p.6]；[doi:10.1093/bib/bbaf026, p.7]；[doi:10.1093/bib/bbaf026, p.8]
- **data：** 训练/独立数据集来自 NCBI/UniProt，先去除 100% 相似冗余后形成 CL2421 与 CL485；CL2421 含 2421 条序列（1288 正、1133 负），CL485 含 485 条序列（258 正、227 负）。[doi:10.1093/bib/bbaf026, p.2][doi:10.1093/bib/bbaf026, p.9]
  - 证据：[doi:10.1093/bib/bbaf026, p.2]；[doi:10.1093/bib/bbaf026, p.9]
- **data：** 负类由与 clathrin 在结构/功能上相近的 vesicular transport proteins 组成，作者还用 DeepLoc 2.0 对数据做了亚细胞定位分析。[doi:10.1093/bib/bbaf026, p.2]
  - 证据：[doi:10.1093/bib/bbaf026, p.2]
- **declared_resources：** 作者声明 data 和 source code 公开在 GitHub，论文给出的仓库是 TargetCLP 项目主页。[doi:10.1093/bib/bbaf026, p.2][doi:10.1093/bib/bbaf026, p.10]
  - 证据：[doi:10.1093/bib/bbaf026, p.2]；[doi:10.1093/bib/bbaf026, p.10]
- **declared_resources：** 方法依赖 ESM-1b（esm1b_t33_650M_UR50S，约 650M 参数，UniRef50 预训练），以及 PSI-BLAST、BLAST、DeepLoc 2.0 等外部工具/资源。[doi:10.1093/bib/bbaf026, p.2][doi:10.1093/bib/bbaf026, p.4]
  - 证据：[doi:10.1093/bib/bbaf026, p.2]；[doi:10.1093/bib/bbaf026, p.4]
- **limitations：** 作者明确承认 ESM embeddings 对超长蛋白存在长度上限问题，而且没有显式讨论计算复杂度。[doi:10.1093/bib/bbaf026, p.10]
  - 证据：[doi:10.1093/bib/bbaf026, p.10]
- **limitations：** 论文只在有限范围数据集上评估，并且作者提到未来需要更大规模数据集和 user-friendly web server，说明当前外推与部署仍有限。[doi:10.1093/bib/bbaf026, p.10]
  - 证据：[doi:10.1093/bib/bbaf026, p.10]
- **method：** 作者把每条序列编码为 PSSM-CLBP、RECM-CLBP、QLC 与 ESM-1b 四种单视图特征，其中 PSSM/RECM 经 CLBP 变换后各为 236 维，QLC 为 147 维，ESM 通过 global average pooling 得到 1280 维表示。[doi:10.1093/bib/bbaf026, p.2][doi:10.1093/bib/bbaf026, p.3][doi:10.1093/bib/bbaf026, p.4]
  - 证据：[doi:10.1093/bib/bbaf026, p.2]；[doi:10.1093/bib/bbaf026, p.3]；[doi:10.1093/bib/bbaf026, p.4]
- **method：** 作者用 differential evolution 在 [-2,2]^4 范围内搜索四个视角的融合权重，报告的最优权重为 (-1.1776, 1, 1.1734, 0.1735)。[doi:10.1093/bib/bbaf026, p.4]
  - 证据：[doi:10.1093/bib/bbaf026, p.4]
- **method：** 在 1899 维加权融合特征上，作者再用 BTG 做特征选择，把表示压缩到 969 维，然后输入 SnBiLSTM 训练最终分类器。[doi:10.1093/bib/bbaf026, p.5][doi:10.1093/bib/bbaf026, p.8]
  - 证据：[doi:10.1093/bib/bbaf026, p.5]；[doi:10.1093/bib/bbaf026, p.8]
- **method：** 评估采用 stratified 5-fold CV 和独立测试集，并用 Acc、Sen、Spe、MCC、AUC 与 AUPR 衡量二分类表现。[doi:10.1093/bib/bbaf026, p.5][doi:10.1093/bib/bbaf026, p.6]
  - 证据：[doi:10.1093/bib/bbaf026, p.5]；[doi:10.1093/bib/bbaf026, p.6]
- **results：** 单视图里，RECM-CLBP + SnBiLSTM 在训练集上表现最好，Acc 92.57%、MCC 0.85、AUC 0.95；ESM 与 QLC 也接近，但略低。[doi:10.1093/bib/bbaf026, p.6]
  - 证据：[doi:10.1093/bib/bbaf026, p.6]
- **results：** 加权融合优于简单串联融合：在 SnBiLSTM 上，Acc 从 92.52% 提升到 93.65%，MCC 从 0.85 提升到 0.89，AUC 从 0.95 提升到 0.96。[doi:10.1093/bib/bbaf026, p.7]
  - 证据：[doi:10.1093/bib/bbaf026, p.7]
- **results：** BTG 进一步提升结果，SnBiLSTM 在 CL2421 上达到 Acc 95.37%、MCC 0.90、AUC 0.98；在 CL485 上达到 Acc 92.78%、MCC 0.85、AUC 0.96。[doi:10.1093/bib/bbaf026, p.8][doi:10.1093/bib/bbaf026, p.9]
  - 证据：[doi:10.1093/bib/bbaf026, p.8]；[doi:10.1093/bib/bbaf026, p.9]
- **results：** 作者声称相对 Le et al. predictor，TargetCLP 在训练集上的 Acc 提升 3.92%，MCC 提升 8.09%，但该对比未给出对方 AUC。[doi:10.1093/bib/bbaf026, p.9]
  - 证据：[doi:10.1093/bib/bbaf026, p.9]

## 页码证据

- [doi:10.1093/bib/bbaf026, p.1]
- [doi:10.1093/bib/bbaf026, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
