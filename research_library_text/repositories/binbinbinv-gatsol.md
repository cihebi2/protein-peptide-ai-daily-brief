# binbinbinv/gatsol

- **仓库：** [https://github.com/binbinbinv/gatsol](https://github.com/binbinbinv/gatsol)
- **固定 commit：** `fe6fb60749c302b2898cf2859418a7b3abbfd7c5`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 23

## 仓库摘要

冻结仓库主要提供蛋白溶解度预测推理链路：PDB/FASTA 预处理、contact map 构建、特征提取、K-fold 超参选择与重训练脚本都可见，但未见冻结权重文件或独立模型定义；代码许可可确认是 MIT，数据与示例输入的边界仍需单独核查。

## 可复用模块与资源

### checkpoints

- `check_point/best_model/readme.md`
  - 能力：checkpoint_placeholder
  - 用途：仅说明最佳模型位置；冻结树内未见任何序列化权重文件
  - 复用状态：blocked；类型：unknown

### datasets

- `dataset/eSol_train.csv`
  - 能力：training_dataset
  - 用途：训练集 CSV
  - 复用状态：partial；类型：unknown
- `dataset/eSol_test.csv`
  - 能力：test_dataset
  - 用途：测试集 CSV
  - 复用状态：partial；类型：unknown
- `dataset/S.cerevisiae_test.csv`
  - 能力：test_dataset
  - 用途：S.cerevisiae 外部测试集 CSV
  - 复用状态：partial；类型：unknown

### evaluation

- `parameters_selection/distance_map/K_fold_distance_map_Selection.py`
  - 能力：hyperparameter_selection
  - 用途：distance map 的 K-fold 超参选择；旁边配有 .log 记录
  - 复用状态：partial；类型：code_entry
- `parameters_selection/learning_rate/K_fold_learning_rate_Selection.py`
  - 能力：hyperparameter_selection
  - 用途：learning rate 的 K-fold 超参选择；旁边配有 .log 记录
  - 复用状态：partial；类型：code_entry
- `parameters_selection/node_feature_selection/K_fold_node_feature_selection.py`
  - 能力：hyperparameter_selection
  - 用途：node feature 的 K-fold 选择；旁边配有 .log 记录
  - 复用状态：partial；类型：code_entry
- `parameters_selection/num_batch_size/K_fold_num_batch_size.py`
  - 能力：hyperparameter_selection
  - 用途：batch size 的 K-fold 选择；旁边配有 .log 记录
  - 复用状态：partial；类型：code_entry
- `parameters_selection/num_heads/K_fold_num_heads_Selection.py`
  - 能力：hyperparameter_selection
  - 用途：attention heads 的 K-fold 选择；旁边配有 .log 记录
  - 复用状态：partial；类型：code_entry
- `parameters_selection/num_hidden_channels/K_fold_num_hidden_channels.py`
  - 能力：hyperparameter_selection
  - 用途：hidden channels 的 K-fold 选择；旁边配有 .log 记录
  - 复用状态：partial；类型：code_entry
- `parameters_selection/num_hidden_layers/K_fold_num_hidden_layers_Selection.py`
  - 能力：hyperparameter_selection
  - 用途：hidden layers 的 K-fold 选择；旁边配有 .log 记录
  - 复用状态：partial；类型：code_entry

### inference

- `Predict/tools/Predict.py`
  - 能力：inference_entrypoint
  - 用途：主推理入口，串联预处理与预测输出
  - 复用状态：partial；类型：code_entry
- `Predict/tools/Predict.sh`
  - 能力：inference_entrypoint
  - 用途：推理命令行包装器
  - 复用状态：partial；类型：code_entry
- `Predict/tools/feature_extract/feature_extra.py`
  - 能力：preprocessing
  - 用途：推理前特征提取的打包副本
  - 复用状态：partial；类型：code_entry
- `Predict/tools/pdb_to_cm/pdb_to_cm.py`
  - 能力：preprocessing
  - 用途：推理前 PDB 到 contact map 转换的打包副本
  - 复用状态：partial；类型：code_entry
- `Predict/NEED_to_PREPARE/list.csv`
  - 能力：inference_input
  - 用途：示例输入清单；同目录还包含 FASTA/PDB 示例用于准备推理
  - 复用状态：partial；类型：unknown

### reusable_assets

- `environment.yaml`
  - 能力：dependencies
  - 用途：Python/conda 环境规格，定义运行推理、训练和超参搜索所需依赖
  - 复用状态：partial；类型：config
- `tools/feature_extract/Protein_parameters_setting.json`
  - 能力：config
  - 用途：特征提取参数配置，供序列/结构特征构造复用
  - 复用状态：partial；类型：config
- `tools/feature_extract/feature_extra.py`
  - 能力：code_entry
  - 用途：特征提取辅助脚本，构造模型输入特征
  - 复用状态：partial；类型：code_entry
- `tools/pdb_to_cm/pdb_to_cm.py`
  - 能力：code_entry
  - 用途：把 PDB 转为 contact map 的预处理脚本
  - 复用状态：partial；类型：code_entry
- `parameters_selection/protein_map_visualization/protein_map_visualization.ipynb`
  - 能力：visualization_notebook
  - 用途：蛋白图/接触图可视化 notebook，用于人工检查特征表示
  - 复用状态：unknown；类型：unknown

### training

- `re_train.py`
  - 能力：training_script
  - 用途：重训练脚本；仓库中还有 `train.log` 但未见执行验证
  - 复用状态：partial；类型：code_entry
- `trian.py`
  - 能力：training_script
  - 用途：训练脚本候选；文件名与入口语义不完全清晰，静态冻结树内无执行证据
  - 复用状态：partial；类型：code_entry

## 使用限制

- 仅做静态审查，未执行代码、未安装依赖、未运行测试。
- 仓库中存在 `tools/` 与 `Predict/tools/` 的镜像式脚本副本，具体哪一份是主维护源仍有不确定性。
- 未见冻结权重文件，checkpoint 只能确认到占位说明。
- 数据与示例输入未见独立许可证，不能直接假定可与 MIT 代码同边界复用。
- 路径存在不等于可复现。

## 仍未知

- `trian.py` 是否为实际训练入口还是辅助脚本，静态命名不足以完全确认。
- `parameters_selection/*.log` 只证明曾有历史输出痕迹，不能证明当前配置可直接复现。
- `dataset/readme.md` 与示例输入文件的授权边界未在静态清单中明确。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
