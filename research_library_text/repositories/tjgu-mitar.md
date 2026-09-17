# tjgu/mitar

- **仓库：** [https://github.com/tjgu/mitar](https://github.com/tjgu/mitar)
- **审计批次：** mass-review 论文声明仓库（repos2，浅克隆静态审计）
- **关联论文：** 10.1038/s42256-024-00836-4
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** high —— 数据划分、采样种子、训练/评估/预测脚本、3个预训练Keras模型、多平台安装包全部入库，复现材料极完整；风险是技术栈老旧(TF1.14/Keras2.2.4/py3.7)需容器化运行。
- **能力：** training_pipeline、inference、benchmark、data_loader

## 仓库摘要

miTAR：CNN+BiRNN 混合深度学习的 miRNA 靶基因预测工具，在 DeepMirTar 与 miRAW 两个数据集上训练了 miTAR1/miTAR2/miTAR 三个模型，提供参数选择、30 次随机划分评估和批量预测的完整脚本。

## 入口脚本

- scripts_data_models/predict_onemiRmultimRNA.py
- scripts_data_models/predict_multimiRmultimRNA.py
- scripts_data_models/evals_CNN_BiRNN_DeepMirTar_miTAR1_sampling.py
- scripts_data_models/evals_CNN_BiRNN_MirTarRAW_miTAR_sampling.py
- scripts_data_models/parameter_sel_CNN_BiRNN_MirTarRAW_miTAR.py

## 数据加载

- scripts_data_models/data/ (DeepMirTar/miRAW 划分文件)
- scripts_data_models/data/sampling/ (20个种子的3折采样)
- scripts_data_models/data/tests/ (预测示例输入)

## 模型权重

- scripts_data_models/results/miTAR1_CNN_BiRNN_b30_lr0.005_dout0.2.h5
- scripts_data_models/results/miTAR2_CNN_BiRNN_b200_lr0.1_dout0.4.h5
- scripts_data_models/results/miTAR_CNN_BiRNN_b100_lr0.005_dout0.2.h5
- conda/ 11平台离线conda包
- mitar/mitar-0.0.1.tar.gz (pip源码包)

## 评测基准

- scripts_data_models/evals_* (30次训练/验证/测试重采样评估)
- scripts_data_models/parameter_sel_* (6学习率x5dropoutx5batchsize网格)

## 文档

- readme.md

## 课题关联

- C011 评估协议(30次随机重采样+均值与95%CI报告范式)
- C008 基准校准 / C010 校准弃权(预测概率阈值-p作为置信度使用的案例)
- C003 多端点(多数据集交叉训练评估方法论参考)；注：领域为miRNA靶预测而非肽/蛋白，内容相关性为方法论层面

## 与论文/课题的组合方式

- 与 10.1038/s42256-024-00836-4 完全对应：results/*.h5 直接复现论文预测，evals_* 复现统计表
- 其'30次随机划分+95%置信区间+多种子采样'评估协议可整体移植到 C008/C010/C011 的肽活性基准校准课题，作为严格评估模板
- predict_*.py 的概率阈值 -p 0.8 置信度筛选机制可作为 C010 校准/弃权设计的对照案例
