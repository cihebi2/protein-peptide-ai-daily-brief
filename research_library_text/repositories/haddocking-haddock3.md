# haddocking/haddock3

- **仓库：** [https://github.com/haddocking/haddock3](https://github.com/haddocking/haddock3)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **语言：** Python
- **复用度：** high —— 成熟维护的 pip 可安装软件（Apache-2.0），配置文件驱动全流程，examples 内含蛋白-肽/蛋白-蛋白等 15+ 场景的完整示例数据与配置，端到端测试齐全，开箱可跑
- **能力：** protocol、benchmark、inference、visualization

## 仓库摘要

HADDOCK3 是 BonvinLab 开发的信息整合型生物分子对接（protein-protein/protein-peptide/蛋白-配体等）模块化工作流引擎，基于 CNS 力场，可用实验/生化信息作为模糊约束引导 docking，并含打分、精修、分析模块。

## 入口脚本

- src/haddock/ (haddock3 CLI, 配置文件驱动: haddock3 <config.toml>)
- setup.py
- pyproject.toml
- Dockerfile

## 数据加载

- examples/data/
- src/haddock/modules/ (topology/sampling/refinement/scoring/analysis 各模块自带输入处理)

## 模型权重

- 无模型权重（基于 CNS 力场的物理对接引擎，非深度学习；CNS 可执行随包分发）

## 评测基准

- end-to-end_tests/
- integration_tests/
- tests/
- examples/run_tests.py
- examples/compare_runs.py

## 文档

- README.md
- docs/
- examples/README.md
- notebooks/
- CHANGELOG.md
- CITING.md

## 课题关联

- C016
- C004
- C011

## 与论文/课题的组合方式

- docking 课题族的核心验证工具：examples/docking-protein-peptide 与 peptide-cyclisation 配置可直接改作 AMP/binder 生成后的结构验证与打分协议；scoring 模块可对 C004 binder/PPI 课题的生成复合物做能量打分排名，替代或对照深度学习打分器。
