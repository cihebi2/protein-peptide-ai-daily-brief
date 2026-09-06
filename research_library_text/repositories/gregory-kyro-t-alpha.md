# gregory-kyro/t-alpha

- **仓库：** [https://github.com/gregory-kyro/t-alpha](https://github.com/gregory-kyro/t-alpha)
- **固定 commit：** `f9973d1966b61986178ab4370c73e46b4401d140`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 27

## 仓库摘要

该仓库提供 T-ALPHA 的蛋白-配体亲和力预测流水线，覆盖模型结构、数据加载、训练、推理、MC dropout 不确定性与 checkpoint 辅助；未见独立评估脚本、bundled 数据或实际模型权重。

## 可复用模块与资源

### checkpoints

- `src/utils/checkpoint_utils.py`
  - 能力：checkpoint_io
  - 用途：checkpoint 保存/加载与路径处理辅助；未见 tracked 权重文件
  - 复用状态：partial；类型：code_entry

### inference

- `scripts/inference.py`
  - 能力：inference_entrypoint
  - 用途：推理 CLI 入口
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/mc_dropout.py`
  - 能力：inference_entrypoint
  - 用途：MC dropout 推理 CLI 入口
  - 复用状态：ready_for_review；类型：code_entry
- `src/inference/perform_inference.py`
  - 能力：inference_pipeline
  - 用途：批量推理与结果输出
  - 复用状态：ready_for_review；类型：code_entry
- `src/inference/mc_dropout.py`
  - 能力：uncertainty_inference
  - 用途：MC dropout 不确定性估计
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `src/models/full_model.py`
  - 能力：model_architecture
  - 用途：主模型组装与前向定义，承载层次化预测主干
  - 复用状态：ready_for_review；类型：code_entry
- `src/models/egnn.py`
  - 能力：model_architecture
  - 用途：EGNN 子模块，用于图表示学习/消息传递
  - 复用状态：ready_for_review；类型：code_entry
- `src/models/dmasif.py`
  - 能力：model_architecture
  - 用途：dMaSIF 子模块，提供表面相关特征/几何建模
  - 复用状态：ready_for_review；类型：code_entry
- `src/models/atomnet.py`
  - 能力：model_architecture
  - 用途：Atom-level 分支或编码模块
  - 复用状态：ready_for_review；类型：code_entry
- `src/models/surface_convnet.py`
  - 能力：model_architecture
  - 用途：surface 特征卷积模块
  - 复用状态：ready_for_review；类型：code_entry
- `src/models/egnn_encoder.py`
  - 能力：model_architecture
  - 用途：EGNN 编码器封装或中间表示抽取
  - 复用状态：ready_for_review；类型：code_entry
- `src/models/dmasif_conv.py`
  - 能力：model_architecture
  - 用途：dMaSIF 相关卷积层或算子
  - 复用状态：ready_for_review；类型：code_entry
- `src/models/utils.py`
  - 能力：model_architecture
  - 用途：模型侧通用工具函数
  - 复用状态：ready_for_review；类型：code_entry
- `src/data/full_model_dataset.py`
  - 能力：data_loader
  - 用途：数据集包装/加载逻辑，支撑训练与推理输入构造
  - 复用状态：ready_for_review；类型：code_entry
- `src/utils/uncertainty_weighting.py`
  - 能力：utility
  - 用途：不确定性加权或自学习辅助逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `src/utils/geometry.py`
  - 能力：utility
  - 用途：几何计算辅助
  - 复用状态：ready_for_review；类型：code_entry
- `src/utils/graph_utils.py`
  - 能力：utility
  - 用途：图构造/图特征辅助
  - 复用状态：ready_for_review；类型：code_entry
- `src/utils/knn.py`
  - 能力：utility
  - 用途：kNN 邻域构建辅助
  - 复用状态：ready_for_review；类型：code_entry
- `data_scalers/protein_sequence_scaler.pkl`
  - 能力：preprocessing_scaler
  - 用途：蛋白序列特征归一化/缩放器；属于预处理资产而非 model checkpoint
  - 复用状态：partial；类型：unknown
- `data_scalers/ligand_sequence_scaler.pkl`
  - 能力：preprocessing_scaler
  - 用途：配体序列特征归一化/缩放器；属于预处理资产而非 model checkpoint
  - 复用状态：partial；类型：unknown
- `data_scalers/ligand_properties_scaler.pkl`
  - 能力：preprocessing_scaler
  - 用途：配体性质特征缩放器
  - 复用状态：partial；类型：unknown
- `data_scalers/connected_graph_scaler.pkl`
  - 能力：preprocessing_scaler
  - 用途：连通图特征缩放器
  - 复用状态：partial；类型：unknown
- `data_scalers/unconnected_graph_scaler.pkl`
  - 能力：preprocessing_scaler
  - 用途：非连通图特征缩放器
  - 复用状态：partial；类型：unknown

### training

- `scripts/train.py`
  - 能力：training_entrypoint
  - 用途：训练 CLI 入口
  - 复用状态：ready_for_review；类型：code_entry
- `src/training/train_model.py`
  - 能力：training_orchestration
  - 用途：训练流程编排与模型实例化
  - 复用状态：ready_for_review；类型：code_entry
- `src/training/lightning_module.py`
  - 能力：training_module
  - 用途：Lightning training module
  - 复用状态：ready_for_review；类型：code_entry
- `src/training/losses.py`
  - 能力：loss_functions
  - 用途：loss 与 objective 定义
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态审查，未执行代码、未安装依赖、未运行测试。
- 未见 tracked bundled data 与独立 evaluation harness。
- 未见实际模型权重；`checkpoint_utils.py` 仅是 checkpoint 辅助。
- 5 个 `data_scalers/*.pkl` 仅能从文件名判断为预处理资产，序列化内容与来源未核验。

## 仍未知

- `T-ALPHA.ipynb` 的具体内容未读，可能包含实验或结果，但不能据路径确认。
- `requirements.txt` 仅表明依赖清单存在，未验证可安装性与版本兼容性。
- 是否存在外部下载数据、隐藏权重或未纳入清单的评估资源，静态库存无法确认。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
