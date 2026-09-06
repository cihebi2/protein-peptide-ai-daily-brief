# Geometric Deep Learning for Structure-Based Ligand Design

- **论文 ID：** `EVIW-CE352CFECBC51F9B`
- **期刊 / 来源：** ACS Cent Sci
- **发表时间：** 2023 Nov 17
- **DOI：** [10.1021/acscentsci.3c00572](https://doi.org/10.1021/acscentsci.3c00572)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白-配体` / `图与几何学习` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

提出 FRAME，一个基于 3D protein-ligand 结构与 geometric deep learning 的 fragment-based molecular expansion 框架，能够迭代选择添加位置、选择 fragment 并预测几何，从而生成更 drug-like 的配体候选。

## 创新边界

`主要新意在于把结构导向的配体扩展建模为顺序动作，并用 SE(3)-equivariant 打分网络学习；它不是全新靶点发现，也没有实验层面的最终药效验证。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在已知蛋白口袋与起始配体结构时，如何自动决定在何处添加哪些 fragment 以及其几何构型，以高效生成更优的配体扩展候选。

## 方法

- 把PDBbind配体逐步移除片段构造参考轨迹；位置网络预测可扩展原子，片段评分网络枚举用户片段库及几何并贪婪选优；网络输入蛋白口袋、当前配体和候选片段的原子类型与3D几何。

## 数据与基准

- 筛选后4,200个高分辨率蛋白-配体复合物，按蛋白相似性分成70/15/15；自建900片段库，基准使用最常见60片段；多项测试用100个复合物，位置识别另用700个测试样本。

## 比较基线

- 基线包括随机位置/片段、去除蛋白口袋输入的消融、Glide迭代对接、LiGAN以及Enamine REAL Space超大库虚拟筛选。

## 结果证据

- 位置模型选择点中95%是参考配体真实连接点，召回92%；片段评分把参考片段排第一45%、前十65%；100蛋白基准中FRAME改善预测亲和力和脱靶选择性，并比迭代Glide生成更药物样的分子，27/100蛋白上超大商业库虚拟筛选找不到所需子结构而FRAME仍可生成。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 当前使用贪婪搜索，作者把更复杂多样化搜索留作未来工作。 亲和力、logP、可合成性等主要是计算代理；作者明确指出最终需要合成和实验测量。 模型从已知活性复合物重构轨迹学习，可能偏向PDBbind可见化学空间。 正文只说模型和数据将放GitHub，未给出可核验的直接仓库URL。

## 仍未知

- GitHub 代码与数据的具体可核验链接未出现在冻结页中。
- 缺少独立 wet-lab 验证，真实实验表现未知。
- 未在冻结证据中看到对全球新颖性或专利独占性的外部核验。

## Pi 结构化证据摘录

- **baseline：** attachment 任务中，作者对比了 random baseline 和不使用 pocket 的 ablation（FRAME no pocket）。
  - 证据：[doi:10.1021/acscentsci.3c00572, p.5]
- **baseline：** fragment ranking 与扩展阶段都对比了 docking / Glide；扩展阶段还使用了 iterative docking 作为主要物理基线。
  - 证据：[doi:10.1021/acscentsci.3c00572, p.6]；[doi:10.1021/acscentsci.3c00572, p.7]
- **baseline：** 作者还比较了 random expansion 和基于 Enamine REAL Space 的 virtual screening。
  - 证据：[doi:10.1021/acscentsci.3c00572, p.7]；[doi:10.1021/acscentsci.3c00572, p.8]
- **baseline：** 最终质量比较中还纳入了 LiGAN 这一生成完整 ligand 的方法作为横向对照。
  - 证据：[doi:10.1021/acscentsci.3c00572, p.8]
- **data：** 最终训练与测试数据集由 4200 个 ligand 组成，作者过滤掉了 lipids、peptides、carbohydrates、nucleotides、重复项和超出 property range 的化合物，median K_D 约为 300 nM。
  - 证据：[doi:10.1021/acscentsci.3c00572, p.3]
- **data：** 数据按 protein-ligand pair 以 70%/15%/15% 划分训练、验证和测试集，并限制不同集合之间蛋白序列同一性不超过 30%。
  - 证据：[doi:10.1021/acscentsci.3c00572, p.3]
- **data：** 作者还构建了包含 900 个 unique fragments 的 library；benchmark 主要使用其中 60 个高频 fragment 以平衡效率与表达能力。
  - 证据：[doi:10.1021/acscentsci.3c00572, p.3]
- **declared_resources：** 作者声明计算模型和数据集将通过 GitHub 提供，Supporting Information 也可免费获取。
  - 证据：[doi:10.1021/acscentsci.3c00572, p.9]
- **declared_resources：** 文章还声明由 NSF Graduate Research Fellowships 和 NIH R01GM127359 资助，并注明 Stanford University 已提交相关专利申请。
  - 证据：[doi:10.1021/acscentsci.3c00572, p.10]
- **limitations：** 作者明确承认模型在部分案例中仍会失败，导致 docking score 和 synthetic complexity 比 reference ligand 更差，且 autoregressive 错误可能阻断增长轨迹或错过关键相互作用。
  - 证据：[doi:10.1021/acscentsci.3c00572, p.9]
- **limitations：** 文中用于评估的多项指标本身仍是计算 proxy，包括 log P、synthetic accessibility 和 docking score，因此真实效果仍需通过合成与实验测量验证。
  - 证据：[doi:10.1021/acscentsci.3c00572, p.9]
- **limitations：** 作者未给出 wet-lab 验证，也未证明其在真实药物发现项目中一定优于其它方法。
  - 证据：[doi:10.1021/acscentsci.3c00572, p.9]
- **method：** FRAME 将配体扩展拆成 attachment location selection 与 fragment scoring 两个步骤，并分别用独立的 SE(3)-equivariant neural networks 进行预测。
  - 证据：[doi:10.1021/acscentsci.3c00572, p.2]；[doi:10.1021/acscentsci.3c00572, p.4]
- **method：** 训练样本来自 PDBBind 中筛选后的 protein-ligand 结构；作者把 reference ligand 逐步拆解成 intermediate states / reference trajectories，再把任务转成监督学习。
  - 证据：[doi:10.1021/acscentsci.3c00572, p.2]；[doi:10.1021/acscentsci.3c00572, p.3]
- **method：** 推理时会枚举 fragment、attachment point 和 dihedral angles，并以 greedy 方式迭代扩展，直到达到目标分子量或模型判断应停止。
  - 证据：[doi:10.1021/acscentsci.3c00572, p.3]；[doi:10.1021/acscentsci.3c00572, p.7]
- **method：** 网络输入只包含原子坐标、元素类型以及 ligand/protein/candidate-fragment 标记，没有使用 hand-crafted features。
  - 证据：[doi:10.1021/acscentsci.3c00572, p.4]
- **results：** attachment location model 在测试集上达到 95% precision 和 92% recall；去掉 pocket 信息后性能下降到 80% precision 和 70% recall。
  - 证据：[doi:10.1021/acscentsci.3c00572, p.5]
- **results：** fragment-scoring model 将 reference fragment 排在第 1 位的比例为 45%，排进 top 10 的比例为 65%，大约是 random 或 docking 的 3 倍。
  - 证据：[doi:10.1021/acscentsci.3c00572, p.6]
- **results：** fine-tuned 版本可在 78% 的案例中恢复 reference fragment 的关键相互作用；相比之下，docking 往往选出更多相互作用，但作者认为这可能夸大了结合优势。
  - 证据：[doi:10.1021/acscentsci.3c00572, p.6]
- **results：** 在 100 个测试蛋白口袋上，FRAME 将起始分子的 median docking score 从 -4.36 改善到 -7.54 kcal/mol，并在整体质量上优于 random expansion、iterative docking 和 virtual screening。
  - 证据：[doi:10.1021/acscentsci.3c00572, p.7]；[doi:10.1021/acscentsci.3c00572, p.8]
- **results：** 模型还学到了具体相互作用规律：methyl 的 staggered 构象更优，氢键最优距离约 2.9 Å，π-π 相互作用最优中心距离约 4 Å，Ca2+-carboxylate 最优距离约 2.6 Å。
  - 证据：[doi:10.1021/acscentsci.3c00572, p.8]；[doi:10.1021/acscentsci.3c00572, p.9]
- **results：** 在结构扰动方面，模型对小幅平移（<0.5 Å）和旋转（<10°）较稳健，但更大扰动可能需要先做 force-field minimization。
  - 证据：[doi:10.1021/acscentsci.3c00572, p.7]

## 页码证据

- [doi:10.1021/acscentsci.3c00572, p.1]
- [doi:10.1021/acscentsci.3c00572, p.2]
- [doi:10.1021/acscentsci.3c00572, p.3]
- [doi:10.1021/acscentsci.3c00572, p.4]
- [doi:10.1021/acscentsci.3c00572, p.5]
- [doi:10.1021/acscentsci.3c00572, p.6]
- [doi:10.1021/acscentsci.3c00572, p.7]
- [doi:10.1021/acscentsci.3c00572, p.9]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
