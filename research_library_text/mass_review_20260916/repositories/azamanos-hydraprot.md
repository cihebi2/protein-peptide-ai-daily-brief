# azamanos/hydraprot

- **仓库：** [https://github.com/azamanos/hydraprot](https://github.com/azamanos/hydraprot)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** high —— 训练/推理/评测完整管线齐全，conda 环境 yml 提供，权重与数据集在 Zenodo 有明确 DOI 下载，参数化配置清晰
- **能力：** data_loader、training_pipeline、inference、benchmark

## 仓库摘要

HydraProt：用 3D U-Net + MLP 两阶段深度学习管线预测蛋白质结构中显式水分子位置的快速工具，支持 PDB/CIF 输入，服务结构生物学与药物发现。

## 入口脚本

- train_unet.py
- train_mlp.py
- predict.py
- evaluate_unet.py
- evaluate_mlp.py

## 数据加载

- datasets/mlp_dataset.py
- datasets/unet_dataset.py
- datasets/__init__.py
- datasets/create_datasets/create_unet_dataset.ipynb

## 模型权重

- checkpoints/mlp/
- checkpoints/unet/（目录占位，模型权重与数据集经 Zenodo 下载: https://doi.org/10.5281/zenodo.10517963）

## 评测基准

- evaluate_unet.py
- evaluate_mlp.py
- test_sets_evaluation.ipynb

## 文档

- readme.md
- overall_pipeline_simple.png

## 课题关联

- C016
- C004

## 与论文/课题的组合方式

- 作为 docking 课题（C016）的结构预处理工具，为蛋白-配体对接补显式水分子以改进结合位点建模
- 水分子位置预测可作为 binder 设计（C004）中活性位点特征增强
