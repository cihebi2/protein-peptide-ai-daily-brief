# priorlabs/tabpfn

- **仓库：** [https://github.com/priorlabs/tabpfn](https://github.com/priorlabs/tabpfn)
- **审计批次：** mass-review 论文声明仓库（repos2，浅克隆静态审计）
- **关联论文：** 10.1038/s41586-024-08328-6
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **语言：** Python (PyTorch)
- **复用度：** high —— pip安装即用、sklearn API零学习成本、小样本(<=10k行)表格任务免训练，含微调/提示调优接口与不确定度输出；Apache-2.0宽松许可。是肽活性/毒性等小样本回归课题开箱即用的强基线。
- **能力：** inference、training_pipeline、benchmark、data_loader、protocol、visualization

## 仓库摘要

TabPFN：先验拟合网络(Prior-Fitted Network)表格学习模型，在海量合成数据上预训练后对全新表格分类/回归任务单次前向推理即完成'训练'，sklearn风格API（TabPFNClassifier/TabPFNRegressor），权重首次调用自动下载。Nature 2024论文官方包。

## 入口脚本

- src/tabpfn/classifier.py（TabPFNClassifier）
- src/tabpfn/regressor.py（TabPFNRegressor）
- src/tabpfn/inference.py、src/tabpfn/base.py
- examples/tabpfn_for_regression.py、examples/tabpfn_for_binary_classification.py、examples/tabpfn_for_multiclass_classification.py

## 数据加载

- src/tabpfn/preprocessing/（表格预处理：异常值、类别编码等）
- examples/batched_classification_cv.py、examples/batched_regression_m4.py（批量CV/回归示例）

## 模型权重

- checkpoint随PyPI/HuggingFace分发：TabPFN-3.5/3.5-Fast/3多版本，fit()时自动下载（src/tabpfn/model_loading.py、checkpoint.py）

## 评测基准

- examples/benchmarking_tabpfn.py
- tests/（含reference_predictions参考预测快照，保证数值可复现）
- src/tabpfn/regression_metrics.py、src/tabpfn/validation.py

## 文档

- README.md
- docs/
- CHANGELOG.md
- examples/notebooks/TabPFN_Demo_Local.ipynb
- THIRD-PARTY-NOTICES.md

## 课题关联

- L3肽性质（序列特征->性质的小样本回归，开箱即用强基线）
- C002肽毒性（毒性二分类/多分类小样本任务）
- C003多端点（多任务回归概率输出）
- C013基线新颖性（免训练基线+参考预测快照保证可比性）
- C010校准弃权（概率预测+不确定度可用于弃权机制研究）
- C008基准校准（benchmarking脚本与CV协议模板）
- X06优化（examples/input_gradients.py梯度引导特征优化思路）

## 与论文/课题的组合方式

- 配论文10.1038/s41586-024-08328-6：直接把AMP/毒性/活性数据集喂给TabPFNRegressor/Classifier获得免训练强基线，为C001/C002/C003课题划定'不训练就达到'的性能线；其概率输出与不确定度接口可做C010校准弃权的对照方法；benchmarking_tabpfn.py+batched CV脚本可作为C008/C011评估协议脚手架。
