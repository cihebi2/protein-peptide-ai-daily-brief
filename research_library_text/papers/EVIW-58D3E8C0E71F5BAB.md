# OrgNet+: towards robust protein stability prediction with convolutional neural networks

- **论文 ID：** `EVIW-58D3E8C0E71F5BAB`
- **期刊 / 来源：** Bioinformatics
- **发表时间：** 2026 Jul 7
- **DOI：** [10.1093/bioinformatics/btag258](https://doi.org/10.1093/bioinformatics/btag258)
- **范围标签：** `待 Pi 解析` / `核心相关` / `论文声明资源`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析待处理

## 作者主张的创新点

论文声称OrgNet+在训练中显式加入NMA、MD、Monte Carlo和生成模型构象集合，学习取向无关且构象稳健的稳定性预测器。

## 创新边界

`not_global_prior_art_verified`。这不是全球首创性检索或独立复现结论。

## 研究问题

减少三维CNN对同一蛋白不同合理构象的ΔΔG预测波动，并提高直接/反向突变的一致性。

## 方法

- 把突变局部环境体素化，使用取向标准化3D CNN；通过多来源约3 Å构象扰动扩充训练，五折同源拆分集成。

## 数据与基准

- S2648训练集（131个蛋白的实验单点突变）；S669、S461直接/反向测试，并为各突变生成多方法构象集合。

## 比较基线

- OrgNet、RaSP、PremPS等稳定性预测器及单一构象生成器/后验平均消融。

## 结果证据

- S669直接RMSE由OrgNet 1.66降至1.54、Pearson由0.31升至0.41；S461 RMSE 1.15、Pearson 0.54；在集合上预测方差相对OrgNet降低25%至30%。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 单一生成器增强会学习其特定扰动模式并跨生成器退化；Boltz-2部分蛋白因显存失败；仍依赖有限突变数据与近似构象集合。

## 仍未知

- 各构象生成器参数、数据许可与仓库运行性未验证。

## 页码证据

- [doi:10.1093/bioinformatics/btag258, p.1]
- [doi:10.1093/bioinformatics/btag258, p.2]
- [doi:10.1093/bioinformatics/btag258, p.4]
- [doi:10.1093/bioinformatics/btag258, p.6]
- [doi:10.1093/bioinformatics/btag258, p.7]
- [doi:10.1093/bioinformatics/btag258, p.8]
- [doi:10.1093/bioinformatics/btag258, p.9]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
