# shibhansh/loss-of-plasticity

- **仓库：** [https://github.com/shibhansh/loss-of-plasticity](https://github.com/shibhansh/loss-of-plasticity)
- **审计批次：** mass-review 论文声明仓库（repos2，浅克隆静态审计）
- **关联论文：** 10.1038/s41586-024-07711-7
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** medium —— 代码组织清晰（algos/nets/envs分层）、MIT许可、多场景实验入口齐全；但领域为持续学习/优化动力学，与肽-蛋白课题族直接错配，且无预训练权重、复现需大规模训练算力。
- **能力：** training_pipeline、benchmark、data_loader

## 仓库摘要

Nature 2024《Loss of Plasticity in Deep Continual Learning》官方代码：在ImageNet任务增量、CIFAR类增量、缓慢变化回归、PPO强化学习等持续学习场景中演示标准反向传播的可塑性丧失，并提出continual backprop（持续重置低效用单元）加以缓解。

## 入口脚本

- lop/imagenet/single_expr.py、lop/imagenet/multi_param_expr.py（ImageNet任务增量实验）
- lop/algos/bp.py、lop/algos/cbp.py、lop/algos/gnt.py（反向传播/continual backprop/生成与测试算法实现）
- lop/slowly_changing_regression/（快速演示小实验）
- lop/rl/（PPO持续强化学习）

## 数据加载

- lop/envs/（环境封装）
- lop/imagenet/class_order/（类别顺序划分文件）
- 数据集（ImageNet/CIFAR等）运行时联网下载

## 模型权重

- 无预训练权重，全部实验从零训练

## 评测基准

- lop/permuted_mnist/、lop/incremental_cifar/（各持续学习基准）
- lop/imagenet/all_plot.py、bp_plot.py（结果绘图）

## 文档

- README.md
- citations.bib
- install.sh
- 各子目录README

## 课题关联

- 与课题族弱相关（持续学习/优化动力学领域）；间接参考：X06优化（continual backprop作为注入随机性的优化器变体思路）、L2蛋白语言模型（长周期持续预训练中的可塑性维持问题类比）

## 与论文/课题的组合方式

- 配论文10.1038/s41586-024-07711-7复现可塑性丧失曲线；若课题组未来做长周期数据流上的蛋白语言模型持续预训练（如不断加入新序列数据），其'低效用单元重置维持可塑性'思路可作为X06优化方向的技术备选。其余课题族不建议投入。
