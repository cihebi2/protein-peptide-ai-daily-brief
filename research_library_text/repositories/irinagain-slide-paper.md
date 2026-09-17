# irinagain/slide-paper

- **仓库：** [https://github.com/irinagain/slide-paper](https://github.com/irinagain/slide-paper)
- **审计批次：** mass-review 论文声明仓库（repos2，浅克隆静态审计）
- **关联论文：** 10.1186/s43556-025-00340-0
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** R（含 1 个 MATLAB 文件 Sim_AJIVE.m）
- **复用度：** medium —— 论文全部仿真与真实数据分析脚本齐备、README 对每个文件用途说明清楚，可直接复现；但无 LICENSE、依赖第三方 R 包（r.jive、CCAGFA）与 MATLAB AJIVE 实现、真实数据需自行从 GDC 下载。
- **能力：** benchmark、protocol

## 仓库摘要

论文《Structural Learning and Integrative Decomposition of Multi-View Data》（SLIDE 方法，Gaynanova & Li）官方代码：提供 SLIDE 方法核心函数、全部仿真实验脚本（两数据集/三数据集、噪声/扰动/信噪比扫描），以及 JIVE/GFA/AJIVE 对比方法封装和 TCGA-BRCA 真实数据分析代码。

## 入口脚本

- Models_paper.R
- Sim_d2.R
- Sim_d2_AC.R
- Sim_d3.R
- Sim_d3_noise.R
- Sim_d3_perturb.R
- Sim_d3_snr.R
- BRCA/BRCA_analysis_d4_SLIDE.R
- BRCA/BRCA_analysis_d4_JIVE.R
- BRCA/BRCA_analysis_d4_GFA.R

## 数据加载

- 无内置数据加载器；TCGA-BRCA 需从 NCI GDC 自行获取（Lock & Dunson 2013 预处理版本）

## 模型权重

- 无（统计方法，无模型权重）

## 评测基准

- Sim_d2*.R / Sim_d3*.R（多视图仿真基准）
- SLIDEfunctions.R
- JIVEfunctions.R（r.jive 封装）
- GFAfunctions.R（CCAGFA 封装）
- Sim_AJIVE.m（MATLAB AJIVE 对比）

## 文档

- README.md（文件级用途说明详尽）

## 课题关联

- C008基准校准（多组学/多视图方法基准比较的核心实现之一）
- C011评估协议（仿真+真实数据的系统比较协议可迁移）
- C005表型（多视图表型结构分解）

## 与论文/课题的组合方式

- 与 DOI 10.1186/s43556-025-00340-0（多组学集成方法比较论文）组合：SLIDE 作为被比较方法，与 mofa（MOFA）、yangzi4/inmf 同批仓库构成完整方法族复现套件；其 Sim_* 脚本的数据生成协议可复用为 C008/C008 相关课题的仿真评测床。
