# azamanos/hydraprot

- **仓库：** [https://github.com/azamanos/hydraprot](https://github.com/azamanos/hydraprot)
- **固定 commit：** `20fa6c05799c8008d34d5decb0bbd5f29538ca0a`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 31

## 仓库摘要

HydraProt 仓库以 MLP 与 3D U-Net 两条流水线实现蛋白水分子位置预测，冻结清单中可见训练、推理、评估、数据构建、数据切分与 checkpoint 资产；代码许可为 MIT，但数据与权重的独立许可边界在冻结证据中未建立。

## 可复用模块与资源

### checkpoints

- `checkpoints/mlp/HydrationNN_epoch_344_92.pth.tar`
  - 能力：model_weight
  - 用途：MLP/HydrationNN 预训练权重 checkpoint
  - 复用状态：partial；类型：unknown
- `checkpoints/unet/Unet3D_36_epoch_374.pth.tar`
  - 能力：model_weight
  - 用途：3D U-Net 预训练权重 checkpoint
  - 复用状态：partial；类型：unknown

### datasets

- `datasets/data_lists/mlp_train_data.npy`
  - 能力：bundled_split_data
  - 用途：MLP 训练分割的打包数据/索引列表
  - 复用状态：partial；类型：unknown
- `datasets/data_lists/mlp_validation_data.npy`
  - 能力：bundled_split_data
  - 用途：MLP 验证分割的打包数据/索引列表
  - 复用状态：partial；类型：unknown
- `datasets/data_lists/unet_train_data.npy`
  - 能力：bundled_split_data
  - 用途：U-Net 训练分割的打包数据/索引列表
  - 复用状态：partial；类型：unknown
- `datasets/data_lists/unet_validation_data.npy`
  - 能力：bundled_split_data
  - 用途：U-Net 验证分割的打包数据/索引列表
  - 复用状态：partial；类型：unknown
- `datasets/data_lists/test_data.npy`
  - 能力：bundled_split_data
  - 用途：留出测试集的数据/索引列表
  - 复用状态：partial；类型：unknown

### evaluation

- `evaluate_mlp.py`
  - 能力：evaluation_entrypoint
  - 用途：MLP 评估入口脚本
  - 复用状态：ready_for_review；类型：code_entry
- `evaluate_unet.py`
  - 能力：evaluation_entrypoint
  - 用途：U-Net 评估入口脚本
  - 复用状态：ready_for_review；类型：code_entry
- `utils/evaluation_utils.py`
  - 能力：evaluation_utils
  - 用途：评估指标与结果汇总辅助
  - 复用状态：ready_for_review；类型：code_entry
- `test_sets_evaluation.ipynb`
  - 能力：evaluation_notebook
  - 用途：留出测试集评估 notebook
  - 复用状态：ready_for_review；类型：unknown

### inference

- `predict.py`
  - 能力：inference_entrypoint
  - 用途：顶层推理入口脚本
  - 复用状态：ready_for_review；类型：code_entry
- `prediction/mlp_prediction.py`
  - 能力：inference_module
  - 用途：MLP 预测流程
  - 复用状态：ready_for_review；类型：code_entry
- `prediction/unet_prediction.py`
  - 能力：inference_module
  - 用途：U-Net 预测流程
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `models/mlp_model.py`
  - 能力：model_architecture
  - 用途：定义 MLP/HydrationNN 的核心网络结构
  - 复用状态：ready_for_review；类型：code_entry
- `models/unet_model.py`
  - 能力：model_architecture
  - 用途：定义 3D U-Net 的核心网络结构
  - 复用状态：ready_for_review；类型：code_entry
- `models/modules.py`
  - 能力：model_architecture
  - 用途：共享的网络模块、层与基础组件
  - 复用状态：ready_for_review；类型：code_entry
- `datasets/mlp_dataset.py`
  - 能力：data_loader
  - 用途：MLP 数据集封装与读取逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `datasets/unet_dataset.py`
  - 能力：data_loader
  - 用途：U-Net 数据集封装与读取逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `params/mlp_params.py`
  - 能力：config
  - 用途：MLP 训练超参数与实验参数定义
  - 复用状态：ready_for_review；类型：code_entry
- `params/unet_params.py`
  - 能力：config
  - 用途：U-Net 训练超参数与实验参数定义
  - 复用状态：ready_for_review；类型：code_entry
- `params/prediction_params.py`
  - 能力：config
  - 用途：推理阶段参数与路径配置
  - 复用状态：ready_for_review；类型：code_entry
- `datasets/create_datasets/create_mlp_dataset.ipynb`
  - 能力：dataset_creation
  - 用途：构建 MLP 训练/验证数据切分的 notebook 方法
  - 复用状态：ready_for_review；类型：unknown
- `datasets/create_datasets/create_unet_dataset.ipynb`
  - 能力：dataset_creation
  - 用途：构建 U-Net 训练/验证数据切分的 notebook 方法
  - 复用状态：ready_for_review；类型：unknown
- `utils/utils.py`
  - 能力：shared_utils
  - 用途：通用工具函数与辅助逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `utils/mlp_utils.py`
  - 能力：shared_utils
  - 用途：MLP 相关辅助函数
  - 复用状态：ready_for_review；类型：code_entry
- `utils/unet_utils.py`
  - 能力：shared_utils
  - 用途：U-Net 相关辅助函数
  - 复用状态：ready_for_review；类型：code_entry

### training

- `train_mlp.py`
  - 能力：training_entrypoint
  - 用途：MLP 训练入口脚本
  - 复用状态：ready_for_review；类型：code_entry
- `train/mlp_train_modules.py`
  - 能力：training_module
  - 用途：MLP 训练循环、损失与优化辅助
  - 复用状态：ready_for_review；类型：code_entry
- `train_unet.py`
  - 能力：training_entrypoint
  - 用途：U-Net 训练入口脚本
  - 复用状态：ready_for_review；类型：code_entry
- `train/unet_train_modules.py`
  - 能力：training_module
  - 用途：U-Net 训练循环、损失与优化辅助
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态盘点，未执行仓库代码或测试。
- 依赖未安装，训练/推理/评估行为无法验证。
- 大于 5MiB 的 blob 可能仅为 promisor 对象，完整内容未核验。
- 路径存在不代表可复现或结果可重现。
- 数据与 checkpoint 的独立许可边界未从冻结证据中建立。

## 仍未知

- `datasets/data_lists/*.npy` 的具体内容结构、样本规模与预处理规则未从冻结元数据确认。
- 两个 checkpoint 是否对应论文最终报告结果、训练轮次与随机种子未确认。
- `params/*.py` 是否是唯一配置来源不确定；未见统一 `config_recipe`。
- `prediction_results/*` 更像输出目录，其内容是否可复用未建立。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
