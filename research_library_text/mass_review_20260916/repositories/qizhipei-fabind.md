# qizhipei/fabind

- **仓库：** [https://github.com/qizhipei/fabind](https://github.com/qizhipei/fabind)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** high —— 训练+推理+测试代码齐全，权重（HuggingFace）与预处理数据（Zenodo）均公开可下载，含推理示例与数据划分
- **能力：** training_pipeline、inference、benchmark、data_loader

## 仓库摘要

FABind 系列蛋白-配体对接方法官方仓库：FABind（NeurIPS 2023）端到端口袋预测+姿态生成，FABind+（KDD 2025）增强口袋预测并支持采样与回归（置信度）双模式。

## 入口脚本

- FABind/fabind/main_fabind.py
- FABind/fabind/fabind_inference.py
- FABind_plus/fabind/main_fabind.py
- FABind_plus/fabind/inference_sampling_fabind.py
- FABind_plus/fabind/inference_regression_fabind.py
- FABind_plus/fabind/train_confidence.py

## 数据加载

- FABind/fabind/data.py
- FABind_plus/fabind/data.py
- FABind/fabind/inference_preprocess_protein.py
- FABind/fabind/inference_preprocess_mol_confs.py

## 模型权重

- ckpt/（空目录）；权重在 HuggingFace: QizhiPei/FABind_model 与 KaiyuanGao/FABind_plus_model；预处理数据 Zenodo: https://zenodo.org/records/11352521

## 评测基准

- FABind/fabind/test_fabind.py
- FABind_plus/fabind/test_regression_fabind.py
- FABind_plus/fabind/test_sampling_fabind.py
- split_pdb_id/（PDBBind 划分）

## 文档

- README.md
- FABind/README.md
- FABind_plus/README.md
- FABind/inference_examples/
- FABind_plus/inference_examples/

## 课题关联

- C016
- C008
- C010

## 与论文/课题的组合方式

- 作为 C016 docking 课题的快速强基线引擎（端到端秒级对接）
- FABind+ 的 confidence 回归头与 train_confidence.py 可用于 C010 校准弃权课题（姿态置信度→选择性预测）
- 在 PDBBind 基准上的标准化评测流程可用于 C008 基准校准对比
