# abelavit/PepCNN

- **仓库：** [https://github.com/abelavit/PepCNN](https://github.com/abelavit/PepCNN)
- **固定 commit：** `c6fc1d8f07ee708de6a095f748b60d39e9815824`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 5

## 仓库摘要

这是 PepCNN 仓库的静态审查：可确认的核心方法是两份 `*_num2_train_network.py` 网络定义；存在一个 `Fasta.txt` 可能作为输入序列/样本文件，但冻结清单未证明其为正式数据集。未发现许可证、checkpoint、独立评估或可验证推理入口，直接复用受缺失代码许可限制。

## 可复用模块与资源

### datasets

- `Fasta.txt`
  - 能力：input_fasta_or_sample_list
  - 用途：可能是 FASTA 序列输入或样本清单；仅凭静态清单无法确认是否为训练/测试数据集
  - 复用状态：unknown；类型：unknown

### reusable_assets

- `dataset1_num2_train_network.py`
  - 能力：model_architecture
  - 用途：定义 dataset1 的 PepCNN 网络结构/训练网络
  - 复用状态：blocked；类型：code_entry
- `dataset2_num2_train_network.py`
  - 能力：model_architecture
  - 用途：定义 dataset2 的 PepCNN 网络结构/训练网络
  - 复用状态：blocked；类型：code_entry

### training

- `dataset1_PepCNN_train.py`
  - 能力：training_module
  - 用途：文件名显示为 dataset1 的训练脚本/训练辅助模块；未读取内容，无法确认是否入口
  - 复用状态：blocked；类型：code_entry
- `dataset2_PepCNN_train.py`
  - 能力：training_module
  - 用途：文件名显示为 dataset2 的训练脚本/训练辅助模块；未读取内容，无法确认是否入口
  - 复用状态：blocked；类型：code_entry

## 使用限制

- not_executed_static_analysis_only
- dependencies_not_installed
- repository_code_not_executed
- tests_not_run
- submodules_not_initialized
- large_blobs_over_5MiB_may_be_promisor_only
- path_presence_is_not_reproduction_evidence

## 仍未知

- `dataset1_num1_extraction_of_samples.py` 与 `dataset2_num1_extraction_of_samples.py` 的具体作用未从内容确认，可能是样本提取/预处理模块。
- `dataset1_PepCNN.py` 与 `dataset2_PepCNN.py` 的具体职责未从内容确认，可能是模型驱动、包装或推断相关脚本。
- `Fasta.txt` 是否为正式数据集、示例输入还是引用列表未确认。
- 仓库中没有可验证的 inference、evaluation 或 checkpoint 资产。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
