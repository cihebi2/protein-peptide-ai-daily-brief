# DataDTA: a multi-feature and dual-interaction aggregation framework for drug–target binding affinity prediction

- **论文 ID：** `EVIW-903FC9F7CF235FD5`
- **期刊 / 来源：** Bioinformatics
- **发表时间：** 2023 Sep 9
- **DOI：** [10.1093/bioinformatics/btad560](https://doi.org/10.1093/bioinformatics/btad560)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白-配体` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者提出 DataDTA：先从蛋白 3D 结构预测 binding pockets 并提取 pocket descriptors，再为配体构建 SMILES 编码与 AG-FPs，最后用 CNN、highway block 和 multihead attention 的双交互融合框架完成 DTA 预测。

## 创新边界

`新意主要在多源特征组合与双层级融合，不是候选分子生成、优化或 wet-lab 发现；它属于可用于设计决策的亲和力预测方法。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在缺少真实蛋白-配体复合物结构时，如何把蛋白序列、预测口袋描述子、配体 SMILES 和分子低维图特征联合起来，提高 drug–target binding affinity (DTA) 回归预测的准确性。

## 方法

- 从预测蛋白三维结构取top-3 DoGSiteScorer口袋并形成126维描述符；分子侧使用AG-FPs和SMILES，蛋白侧使用口袋与序列；CNN、highway和multi-head attention执行多尺度/双交互融合，以MSE训练。

## 数据与基准

- 使用PDBbind 2016 general/refined/core及PDB test105/test71；最终11906训练、1000验证、290 core测试，另有105和71个测试复合物。SMILES固定120字符、蛋白序列固定1000，过长截断；训练并比较五次，按验证集选最优模型。

## 比较基线

- 比较Pafnucy、TopologyNet、DeepDTAF、DeepDTA、FusionDTA和MFR-DTA；对DeepDTAF同时报告原生口袋与预测口袋设置，并做无dual-interaction、无AG-FPs、无口袋、仅top-1口袋消融。

## 结果证据

- core 2016上DataDTA报告RMSE 1.274、R 0.814、CI 0.806，优于表中对照的R；test105上R 0.676，低于使用原生复合物的Pafnucy/DeepDTAF，但优于多个无结构或预测结构对照；test71上结果有竞争力但R和CI略低于MFR-DTA。消融显示去掉口袋或仅用top-1口袋均变差。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- test105明确显示预测复合物结构会引入偏差；top-3口袋、固定长度截断和验证集择优限制外推；只按既有PDBbind处理并不能证明新骨架/新靶点时间外泛化，且部分基线使用原生复合物，输入信息并不完全对等。

## 仍未知

- 未独立验证不同 pocket 预测器下的稳健性。
- 未从正文获得完整训练耗时、硬件消耗与复现环境信息。
- 未对更广泛的外部数据集做系统性泛化验证。

## Pi 结构化证据摘录

- **baseline：** 主要对比基线包括 DeepDTA、Pafnucy、TopologyNet、DeepDTAF、FusionDTA 和 MFR-DTA。
  - 证据：[doi:10.1093/bioinformatics/btad560, p.7]
- **baseline：** 为公平比较，作者还把 DeepDTAF 在 predicted pockets 设置下重新训练，并重训了 FusionDTA 与 MFR-DTA。
  - 证据：[doi:10.1093/bioinformatics/btad560, p.7]
- **data：** 主要基准来自 PDBbind 2016：general set 9221 对、refined set 3685 对、core set 290 对；另使用 PDB 的 test105 和 test71 作为外部测试集。
  - 证据：[doi:10.1093/bioinformatics/btad560, p.3]
- **data：** 输入长度固定为 SMILES 120、protein sequence 1000；更长序列截断，更短序列补零。
  - 证据：[doi:10.1093/bioinformatics/btad560, p.3]
- **data：** 口袋特征使用预测的 top-3 pockets，不足 3 个时用零填充，以降低单一 pocket 漏检带来的信息缺失。
  - 证据：[doi:10.1093/bioinformatics/btad560, p.4]；[doi:10.1093/bioinformatics/btad560, p.8]
- **declared_resources：** 论文声明 DataDTA 的代码和数据公开在 GitHub 仓库 `https://github.com/YanZhu06/DataDTA`。
  - 证据：[doi:10.1093/bioinformatics/btad560, p.1]；[doi:10.1093/bioinformatics/btad560, p.10]
- **declared_resources：** 口袋特征来自 Proteins Plus / DoGSiteScorer，基准数据来自 PDBbind 2016 与 PDB 的 test105、test71。
  - 证据：[doi:10.1093/bioinformatics/btad560, p.3]；[doi:10.1093/bioinformatics/btad560, p.4]
- **limitations：** DataDTA 依赖 binding pocket prediction 的质量，作者明确承认如果 pocket 预测更准确，DTA 性能还可能继续提升。
  - 证据：[doi:10.1093/bioinformatics/btad560, p.9]
- **limitations：** 作者也指出 highway 与 multihead attention 的组合会影响可解释性，attention weights 只能提供有限解释。
  - 证据：[doi:10.1093/bioinformatics/btad560, p.9]
- **limitations：** 在 test105 上，带 native complex structures 的方法仍优于 DataDTA，说明该框架在缺少真实复合物结构时存在性能上限。
  - 证据：[doi:10.1093/bioinformatics/btad560, p.7]
- **method：** 对 drug SMILES 和 protein sequence 采用 integer/label encoding，并用 CNN residual blocks 与 dilated convolution 提取序列表征。
  - 证据：[doi:10.1093/bioinformatics/btad560, p.3]；[doi:10.1093/bioinformatics/btad560, p.5]
- **method：** 对药物额外构建 900 维 AG-FPs，对蛋白额外使用 DoGSiteScorer 预测的 top-3 pockets 提取 126 维 pocket descriptors，再分别线性映射到 256 维。
  - 证据：[doi:10.1093/bioinformatics/btad560, p.4]；[doi:10.1093/bioinformatics/btad560, p.5]
- **method：** 将四路特征分别拼接和堆叠后输入 highway block 与 multihead attention，在 bit-wise 和 vector-wise 两个层面融合，最后经全连接层回归 affinity。
  - 证据：[doi:10.1093/bioinformatics/btad560, p.5]；[doi:10.1093/bioinformatics/btad560, p.6]
- **results：** 在 core 2016 test dataset 上，DataDTA 达到 RMSE 1.274、MSE 1.012、R 0.814、SD 1.265、CI 0.806，表中优于 DeepDTA、Pafnucy、TopologyNet、DeepDTAF、FusionDTA 和 MFR-DTA。
  - 证据：[doi:10.1093/bioinformatics/btad560, p.7]
- **results：** 在 test105 上，DataDTA 的结果为 RMSE 1.405、MSE 1.127、R 0.676、SD 1.316、CI 0.746；作者也指出带 native complex structures 的 Pafnucy 和 DeepDTAF 在该集上更强。
  - 证据：[doi:10.1093/bioinformatics/btad560, p.7]
- **results：** 在 test71 上，DataDTA 达到 RMSE 1.220、MSE 0.949、R 0.538、SD 1.146、CI 0.688，整体有竞争力，但在 R/CI 上略低于 MFR-DTA。
  - 证据：[doi:10.1093/bioinformatics/btad560, p.7]
- **results：** 消融结果显示，去掉 dual-interaction module 后 CI 降到 0.790；去掉 AG-FPs、去掉 pockets，或只保留 top-1 pocket，都会让性能低于完整 DataDTA。
  - 证据：[doi:10.1093/bioinformatics/btad560, p.8]；[doi:10.1093/bioinformatics/btad560, p.9]

## 页码证据

- [doi:10.1093/bioinformatics/btad560, p.10]
- [doi:10.1093/bioinformatics/btad560, p.1]
- [doi:10.1093/bioinformatics/btad560, p.3]
- [doi:10.1093/bioinformatics/btad560, p.4]
- [doi:10.1093/bioinformatics/btad560, p.7]
- [doi:10.1093/bioinformatics/btad560, p.8]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
