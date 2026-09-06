# MDF-DTA: A Multi-Dimensional Fusion Approach for Drug-Target Binding Affinity Prediction

- **论文 ID：** `EVIW-E18C301976BF7DBA`
- **期刊 / 来源：** J Chem Inf Model
- **发表时间：** 2024 Jun 18
- **DOI：** [10.1021/acs.jcim.4c00310](https://doi.org/10.1021/acs.jcim.4c00310)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白-配体`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

提出 MDF-DTA，把药物与蛋白的 1D、2D、3D 预训练表征分别编码后再做融合，并用该融合表示完成 DTA 回归与分类预测。

## 创新边界

`创新点主要在多维表征融合，不是候选分子的生成、优化或湿实验验证。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在 DAVIS 与 KIBA 等基准上，如何融合药物与蛋白的多维表征，提高 drug-target binding affinity 预测的精度、稳定性与可解释性。

## 方法

- 多维drug/protein encoders与fusion regressor。

## 数据与基准

- Davis、KIBA。

## 比较基线

- DeepDTA/GraphDTA等与模态消融。

## 结果证据

- 论文报告超过多种SOTA；为计算affinity。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 随机benchmark、计算affinity、无实验。

## 仍未知

- 未见独立外部测试集或前瞻性实验。
- 3D drug encoder 的命名在正文与图注中不一致（EGNN/E3NN）。
- 代码与数据虽声明开源，但本次未实际抓取并验证仓库内容。

## Pi 结构化证据摘录

- **baseline：** 文中对比的基线包括 KronRLS、SimBoost、SimCNN-DTA、DeepDTA、WideDTA、AttentionDTA、MATT-DTI、GraphDTA、TransVAEDTA 和 FusionDTA。
  - 证据：[doi:10.1021/acs.jcim.4c00310, p.7]
- **baseline：** 统计检验部分把 AttentionDTA 作为主要对照模型，借此说明 MDF-DTA 在多个指标上有显著提升。
  - 证据：[doi:10.1021/acs.jcim.4c00310, p.8]
- **data：** DAVIS 数据集包含 30,056 个 interactions，涉及 442 个 proteins 和 68 个 ligands；KIBA 数据集包含 118,218 个 interactions，涉及 467 个 proteins 和 52,498 个 ligands。
  - 证据：[doi:10.1021/acs.jcim.4c00310, p.4]
- **data：** 作者强调两个数据集的蛋白对相似性较低：DAVIS 中 92% 的 protein-protein Smith-Waterman 相似性不超过 60%，KIBA 中除约 1% 外均不超过 60%。
  - 证据：[doi:10.1021/acs.jcim.4c00310, p.4]
- **declared_resources：** 作者声明 source code 和 data 已在 GitHub 以 MIT License 发布，且大体量 embeddings 可按需提供。
  - 证据：[doi:10.1021/acs.jcim.4c00310, p.10]
- **limitations：** 作者明确表示工作仍有改进空间，未来需要更显式地建模原子级相互作用，并加入更多特征以增强可解释性。
  - 证据：[doi:10.1021/acs.jcim.4c00310, p.10]
- **limitations：** 当前实验只在 DAVIS 与 KIBA 两个基准上完成，未见外部独立测试集或湿实验验证的证据。
  - 证据：[doi:10.1021/acs.jcim.4c00310, p.4]；[doi:10.1021/acs.jcim.4c00310, p.7]；[doi:10.1021/acs.jcim.4c00310, p.10]
- **method：** 药物侧分别使用 Mol2Vec、GIN 和 EGNN 提取 1D、2D、3D 表征，蛋白侧分别使用 ProtVec、ProtBERT 和 ESM-Fold 提取对应维度表征，然后进入各自的 fusion block。
  - 证据：[doi:10.1021/acs.jcim.4c00310, p.3]；[doi:10.1021/acs.jcim.4c00310, p.5]；[doi:10.1021/acs.jcim.4c00310, p.6]
- **method：** 各维度嵌入先做 L2 normalization，再经过全连接层；药物侧与蛋白侧分别拼接成 fused embeddings，最后合并后通过三层全连接网络输出亲和力分值。
  - 证据：[doi:10.1021/acs.jcim.4c00310, p.3]；[doi:10.1021/acs.jcim.4c00310, p.5]；[doi:10.1021/acs.jcim.4c00310, p.6]
- **method：** 训练使用 Keras 和 Adam，学习率为 0.0001，损失函数是 MSE，最多训练 500 epochs，并配合 early stopping、batch size 64 和 5-fold cross-validation 调参。
  - 证据：[doi:10.1021/acs.jcim.4c00310, p.7]
- **method：** 评估同时覆盖回归与二分类任务，采用 CI、MSE、rm2 和 AUPR；AUPR 的阈值设定为 DAVIS 的 7 和 KIBA 的 12.1。
  - 证据：[doi:10.1021/acs.jcim.4c00310, p.7]
- **results：** 在 KIBA 上，MDF-DTA 报告 MSE 0.146、CI 0.892、rm2 0.787、AUPR 0.848，整体优于文中列出的基线方法。
  - 证据：[doi:10.1021/acs.jcim.4c00310, p.7]；[doi:10.1021/acs.jcim.4c00310, p.8]
- **results：** 在 DAVIS 上，MDF-DTA 报告 MSE 0.172、CI 0.912、rm2 0.763、AUPR 0.792，同样优于文中列出的基线方法。
  - 证据：[doi:10.1021/acs.jcim.4c00310, p.7]；[doi:10.1021/acs.jcim.4c00310, p.8]
- **results：** 作者还报告 McNemar test 在 DAVIS 与 KIBA 上均得到 p<0.05，表示相对 AttentionDTA 的改进具有统计显著性。
  - 证据：[doi:10.1021/acs.jcim.4c00310, p.8]
- **results：** 消融实验显示，去掉 EGNN 或 ESM-Fold 会明显恶化 MSE，说明 3D drug 表征和 3D target 表征都是关键增益来源。
  - 证据：[doi:10.1021/acs.jcim.4c00310, p.9]

## 页码证据

- [doi:10.1021/acs.jcim.4c00310, p.10]
- [doi:10.1021/acs.jcim.4c00310, p.1]
- [doi:10.1021/acs.jcim.4c00310, p.4]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
