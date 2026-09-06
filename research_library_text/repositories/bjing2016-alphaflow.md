# bjing2016/alphaflow

- **仓库：** [https://github.com/bjing2016/alphaflow](https://github.com/bjing2016/alphaflow)
- **固定 commit：** `0408d7c89dac444a43a9089d7427ce470b0a5e67`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 20

## 仓库摘要

静态审查显示 AlphaFlow 以蛋白 ensemble 生成的模型、训练、推理和 Atlas 预处理管线为主；未见 tracked 权重或原始数据。

## 可复用模块与资源

### datasets

- `splits/atlas_train.csv`
  - 能力：atlas_train_split_manifest
  - 用途：Atlas 训练集划分清单
  - 复用状态：partial；类型：unknown
- `splits/atlas_val.csv`
  - 能力：atlas_val_split_manifest
  - 用途：Atlas 验证集划分清单
  - 复用状态：partial；类型：unknown
- `splits/atlas_test.csv`
  - 能力：atlas_test_split_manifest
  - 用途：Atlas 测试集划分清单
  - 复用状态：partial；类型：unknown
- `splits/cameo2022.csv`
  - 能力：cameo2022_split_manifest
  - 用途：CAMEO 2022 测试划分清单
  - 复用状态：partial；类型：unknown
- `splits/pdb_test.csv`
  - 能力：pdb_test_split_manifest
  - 用途：PDB 测试划分清单
  - 复用状态：partial；类型：unknown
- `splits/pdb_test.json`
  - 能力：pdb_test_metadata
  - 用途：PDB 测试集元数据/标注清单
  - 复用状态：partial；类型：config

### inference

- `predict.py`
  - 能力：prediction_entrypoint
  - 用途：推理/预测启动脚本
  - 复用状态：ready_for_review；类型：code_entry
- `alphaflow/data/inference.py`
  - 能力：inference_pipeline
  - 用途：推理侧输入处理与结果准备
  - 复用状态：ready_for_review；类型：code_entry
- `alphaflow/model/wrapper.py`
  - 能力：model_wrapper_for_inference
  - 用途：模型调用封装，便于推理流程接入
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `alphaflow/model/alphafold.py`
  - 能力：model_architecture
  - 用途：核心生成式模型/包装实现
  - 复用状态：ready_for_review；类型：code_entry
- `alphaflow/model/trunk.py`
  - 能力：model_architecture
  - 用途：模型 trunk 主体模块
  - 复用状态：ready_for_review；类型：code_entry
- `alphaflow/utils/diffusion.py`
  - 能力：model_architecture
  - 用途：diffusion / flow matching 相关采样工具
  - 复用状态：ready_for_review；类型：code_entry
- `alphaflow/data/data_pipeline.py`
  - 能力：data_pipeline
  - 用途：输入特征与批处理流水线
  - 复用状态：ready_for_review；类型：code_entry
- `Dockerfile`
  - 能力：environment_recipe
  - 用途：容器化依赖与运行环境定义
  - 复用状态：ready_for_review；类型：unknown
- `scripts/download_atlas.sh`
  - 能力：dataset_preparation
  - 用途：Atlas 外部数据下载入口
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/mmseqs_search.py`
  - 能力：msa_or_search_helper
  - 用途：MMseqs2 搜索辅助脚本
  - 复用状态：ready_for_review；类型：code_entry

### training

- `train.py`
  - 能力：training_entrypoint
  - 用途：训练启动脚本
  - 复用状态：ready_for_review；类型：code_entry
- `alphaflow/data/data_modules.py`
  - 能力：data_module_for_training
  - 用途：训练数据模块封装
  - 复用状态：ready_for_review；类型：code_entry
- `alphaflow/data/feature_pipeline.py`
  - 能力：feature_pipeline_for_training
  - 用途：训练特征生成
  - 复用状态：ready_for_review；类型：code_entry
- `alphaflow/data/input_pipeline.py`
  - 能力：input_pipeline_for_training
  - 用途：训练输入组装
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态审查；未运行代码、未安装依赖、未执行测试。
- 未见 tracked checkpoint 文件，无法确认可复现权重来源。
- 未见 bundled raw data；`splits/*.csv` 只是分割清单，不能证明数据已可直接复现。
- 外部下载脚本和 MMseqs2 相关流程依赖仓库外资源，许可与可用性未核实。

## 仍未知

- Atlas/CAMEO/PDB 数据的实际来源、下载地址与许可未在静态材料中完全确认。
- 是否存在未跟踪的大型 checkpoint 或 promisor-only blob 仍无法排除。
- 训练/评估指标与真实运行参数无法由静态清单证明。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
