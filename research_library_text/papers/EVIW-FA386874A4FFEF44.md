# Graph neural pre-training based drug-target affinity prediction

- **论文 ID：** `EVIW-FA386874A4FFEF44`
- **期刊 / 来源：** Front Genet
- **发表时间：** 2024 Sep 16
- **DOI：** [10.3389/fgene.2024.1452339](https://doi.org/10.3389/fgene.2024.1452339)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `图与几何学习` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者提出 GNPDTA：先用 INFOGRAPH 预训练的 drug/target GIN 从无标注数据中抽取低层特征，再用浅层 2D CNN 与 predictor 融合并回归 DTA，声称可缩小 pre-training 目标与下游 DTA 目标/样本形式不一致的问题，并在五个基准集上取得更优结果。

## 创新边界

`创新边界仅限于 DTA 预测的表示学习与特征融合；不包含新分子/蛋白候选生成、对接或湿实验验证，且冻结材料内未独立核验全球新颖性。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在标注稀缺的 drug-target affinity prediction 中，如何先利用大量无标注 drug/target 数据学到更稳健的图表示，再把这些低层表示转化为适合 drug-target pair 预测的高层特征。

## 方法

- 分子图与蛋白图/序列pretext tasks、融合回归。

## 数据与基准

- Davis/KIBA/PDBBind类benchmark。

## 比较基线

- DeepDTA/GraphDTA及pretraining baselines。

## 结果证据

- 论文报告超过无预训练和SOTA；为计算。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- drug-target joint unlabeled数据不足，scaffold/target OOD未知。

## 仍未知

- 未运行作者代码，无法确认复现性与实际训练细节。
- GitHub 链接仅为论文声明，未在本次冻结材料中核验仓库内容是否与文中一致。
- 未见独立 prior-art 证据，因此 global_novelty_verified 保持 false。
- DTC/Metz/Tox-Cast 的基线覆盖较少，泛化结论仍有限。

## Pi 结构化证据摘录

- **baseline：** Davis/Kiba 的对比基线覆盖 DeepDTA、WideDTA、MATT、AttentionDTA、SAG-DTA、GraphDTA、DeepCDA、ELECTRA-DTA、MRBDTA、DeepGLSTM、GCN-BERT、MGraphDTA、DeepGS、MFR-DTA、MAM、GSAML-DTA 等。
  - 证据：[doi:10.3389/fgene.2024.1452339, p.7]；[doi:10.3389/fgene.2024.1452339, p.9]；[doi:10.3389/fgene.2024.1452339, p.10]
- **baseline：** 在 DTC、Metz、Tox-Cast 上，作者只与 GraphDTA 和 DeepGLSTM 比较，并说明这些数据集上已验证的方法较少。
  - 证据：[doi:10.3389/fgene.2024.1452339, p.10]
- **baseline：** 消融比较还包含 NO Pre-trained GIN+2D CNN、2D CNN、Pre-trained GIN+1D CNN，用来分离验证 pre-training 与 2D CNN 的作用。
  - 证据：[doi:10.3389/fgene.2024.1452339, p.6]；[doi:10.3389/fgene.2024.1452339, p.8]
- **data：** 无标注预训练数据来自 Swiss-Prot 的 565,928 个 targets 和 CHEMBL 的 2,105,464 个 drugs。
  - 证据：[doi:10.3389/fgene.2024.1452339, p.2]
- **data：** 监督评测使用 Kiba、Davis、DTC、Metz 和 Tox-Cast 五个基准数据集，并给出了各自的 drug、target 与 pair 数量。
  - 证据：[doi:10.3389/fgene.2024.1452339, p.2]
- **data：** 作者采用 80/20 train/test split，并用 CI 和 MSE 作为主要评价指标。
  - 证据：[doi:10.3389/fgene.2024.1452339, p.6]
- **declared_resources：** 论文第 5 页给出代码地址 https://github.com/yeqing0713/GNPDTA，并声明代码可用。
  - 证据：[doi:10.3389/fgene.2024.1452339, p.5]
- **declared_resources：** 作者声明训练批次大小受 16 GB GPU 限制，最终 batch size 设为 1,280。
  - 证据：[doi:10.3389/fgene.2024.1452339, p.6]
- **declared_resources：** 资助来源列为 National Natural Science Foundation of China、Zhejiang “Lingyan” R&D Program 和 Wenzhou Natural Science Foundation。
  - 证据：[doi:10.3389/fgene.2024.1452339, p.11]
- **limitations：** 作者明确承认标注 DTA 数据仍然较小，因此模型结构被限制为 shallow CNN 与较浅 predictor。
  - 证据：[doi:10.3389/fgene.2024.1452339, p.6]
- **limitations：** 对 DTC、Metz、Tox-Cast 的外部对比基线较少，因而该部分结论的横向比较空间有限。
  - 证据：[doi:10.3389/fgene.2024.1452339, p.10]
- **limitations：** 讨论部分把更强的 GNN 结构、特征融合方式和可视化/可解释性列为 future work，说明现有版本仍有改进空间。
  - 证据：[doi:10.3389/fgene.2024.1452339, p.11]
- **method：** GNPDTA 采用两阶段流程：先在无标注 drug 与 target 图上分别预训练两个 GIN，再把得到的低层特征送入下游监督模块。
  - 证据：[doi:10.3389/fgene.2024.1452339, p.3]；[doi:10.3389/fgene.2024.1452339, p.4]
- **method：** 预训练部分使用 INFOGRAPH 的 mutual information maximization 思路，并明确说明训练目标不依赖标签。
  - 证据：[doi:10.3389/fgene.2024.1452339, p.4]
- **method：** 下游阶段对 target 片段和 drug 节点分别用浅层 2D CNN 提取高层特征，再拼接后由浅层 predictor 输出 affinity 分数。
  - 证据：[doi:10.3389/fgene.2024.1452339, p.5]
- **method：** 作者将 target 预训练设为非重叠 sliding window，推理时改用重叠窗口；drug 侧则在预训练后做 zero-padding 和 truncation，把节点数固定到 64。
  - 证据：[doi:10.3389/fgene.2024.1452339, p.4]；[doi:10.3389/fgene.2024.1452339, p.5]
- **method：** 实验设置里，模型用 shallow CNN 和 predictor 是因为作者认为现有标注 DTA 数据规模较小，难以支撑参数更多的网络。
  - 证据：[doi:10.3389/fgene.2024.1452339, p.6]
- **results：** 在 Davis 上，GNPDTA 报告 CI=0.907、MSE=0.199，表中列为该组最优。
  - 证据：[doi:10.3389/fgene.2024.1452339, p.7]
- **results：** 在 Kiba 上，GNPDTA 报告 CI=0.906、MSE=0.126，同样优于表中比较方法。
  - 证据：[doi:10.3389/fgene.2024.1452339, p.7]
- **results：** 在 DTC、Metz 和 Tox-Cast 上，GNPDTA 分别报告 CI/MSE 为 0.899/0.144、0.812/0.283、0.921/0.301。
  - 证据：[doi:10.3389/fgene.2024.1452339, p.8]
- **results：** 作者进一步声称，该方法在 DTC、Metz、Tox-Cast 上也优于仅比较的 GraphDTA 和 DeepGLSTM。
  - 证据：[doi:10.3389/fgene.2024.1452339, p.10]

## 页码证据

- [doi:10.3389/fgene.2024.1452339, p.11]
- [doi:10.3389/fgene.2024.1452339, p.1]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
