# hicai-zju/plmeae

- **仓库：** [https://github.com/hicai-zju/plmeae](https://github.com/hicai-zju/plmeae)
- **审计批次：** mass-review 论文声明仓库（repos2，浅克隆静态审计）
- **关联论文：** 10.1038/s41467-025-56751-8
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** medium —— 代码短小直接（模块化 zero-shot + finetuning），且附带预计算适应度数据（Fitness.npy/FilteredComboToInd.pkl）可直接复用；但无 LICENSE、无 requirements 锁定、含 __pycache__ 提交、数据路径需手改。
- **能力：** inference、training_pipeline、data_loader

## 仓库摘要

论文《Integrating Protein Language Models and Automatic Biofoundry for Enhanced Protein Evolution》官方实现：用 ESM 语言模型做零样本突变似然排序（module_1/module_2 选 top-96 突变库）并对 ESM 做适应度微调，结合自动化生物铸造厂闭环做蛋白质定向进化（GB1、UBC9、RPL40A 等蛋白）。

## 入口脚本

- module_1.py
- module_2.py
- Zero-shot/UBC9.py
- Zero-shot/RPL40A.py
- Finetuning/scripts/run_fitness.sh

## 数据加载

- Finetuning/tasks/fitness.py（读取训练/测试 CSV，路径需手动配置）

## 模型权重

- 无内置权重；依赖预训练 ESM（facebook/esm 系列）；仓库附带预计算数据 FilteredComboToInd.pkl 与 Fitness.npy

## 评测基准

- （无）

## 文档

- README.md

## 课题关联

- L2蛋白语言模型（ESM 零样本似然与微调范式）
- L1蛋白设计（语言模型引导定向进化）
- X06优化（结合生物铸造厂的进化搜索闭环）
- C013基线新颖性（ESM zero-shot 是蛋白适应度预测的标准基线）

## 与论文/课题的组合方式

- 与 DOI 10.1038/s41467-025-56751-8 组合：按 README 用 module_1/module_2 复现突变库生成与 top-96 选择，用 Finetuning 复现适应度微调；课题组合中其 zero-shot 打分可直接作为 L2/L1 课题的基线方法，Fitness.npy 可作小规模评测数据。
