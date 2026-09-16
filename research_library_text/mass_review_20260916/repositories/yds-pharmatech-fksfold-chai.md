# yds-pharmatech/fksfold-chai

- **仓库：** [https://github.com/yds-pharmatech/fksfold-chai](https://github.com/yds-pharmatech/fksfold-chai)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **语言：** Python
- **复用度：** high —— pip 可装、CLI 与 Pythonic 推理兼容 Chai-1（权重自动下载）、FK 引导模块（chai_lab_extension/steering）与可视化/轨迹导出示例齐全；属早期研究版本
- **能力：** inference、protocol、visualization

## 仓库摘要

FKSFold：在 Chai-1（AlphaFold3 类折叠模型）的扩散过程中施加 Feynman-Kac（FK）粒子滤波引导，用于分子胶诱导三元复合物结构预测（YDS-GlueFold 的早期前身，bioRxiv 2025）。

## 入口脚本

- chai_lab/main.py（fksfold fold CLI）
- examples/run.py
- examples/run_save_traj.py
- examples/run_internal_fks_vis.py

## 数据加载

- chai_lab/data/（继承 Chai-1 的输入/MSA/特征管线）

## 模型权重

- 复用 Chai-1 官方权重（兼容 chai-lab 推理，自动下载）；仓库不附带权重

## 评测基准

- tests/
- tests_dev/

## 文档

- README.md
- examples/covalent_bonds/README.md
- examples/msas/README.md
- examples/restraints/

## 课题关联

- C004
- C007

## 与论文/课题的组合方式

- 推理期 FK 引导是不重训模型的条件化生成手段（C007），可与 boltz_restr 的约束引导形成方法学对照组
- 分子胶三元复合物预测直接服务 binder/PPI 课题（C004），其 steering/scoring.py 与 particle_filter.py 可迁移到其他扩散式结构模型
