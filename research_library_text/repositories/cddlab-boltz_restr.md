# cddlab/boltz_restr

- **仓库：** [https://github.com/cddlab/boltz_restr](https://github.com/cddlab/boltz_restr)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** high —— 开箱可跑：无需重训、复用官方 Boltz 权重、提供 Colab notebook 与丰富 YAML 示例，安装（uv）与文档完整
- **能力：** inference、data_loader、training_pipeline、benchmark、visualization、protocol

## 仓库摘要

Boltz-1/2 的约束引导推理（restraint-guided inference）扩展：支持配体构象约束与距离约束，无需重训权重即可实现改进 docking 姿态、采样配体解离路径与蛋白域运动。

## 入口脚本

- src/boltz/（CLI 主包）
- visualize_dissociation.py
- visualize_intermediate.py
- scripts/eval/
- scripts/train/
- scripts/process/

## 数据加载

- src/boltz/data/（feature/msa/parse/tokenize/sample/crop 等子模块）

## 模型权重

- 复用 Boltz-1/2 官方权重（--checkpoint 可选，默认自动下载模型）；仓库本身不附带权重

## 评测基准

- tests/test_regression.py
- tests/test_kernels.py
- docs/evaluation.md

## 文档

- README.md
- docs/prediction.md
- docs/training.md
- docs/evaluation.md
- examples/*.yaml（pocket/ligand/affinity/multimer 等 9 个示例配置）

## 课题关联

- C016
- C004
- C007

## 与论文/课题的组合方式

- 约束引导采样即推理期条件控制（C007），可借鉴到条件生成课题的'无需重训的条件化'范式
- 直接用作 C016 docking 姿态改进与配体解离路径采样的工具链
- binder/PPI 课题（C004）中可用距离约束引导复合物构象采样
