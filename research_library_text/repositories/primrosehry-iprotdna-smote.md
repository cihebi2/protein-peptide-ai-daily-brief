# primrosehry/iprotdna-smote

- **仓库：** [https://github.com/primrosehry/iprotdna-smote](https://github.com/primrosehry/iprotdna-smote)
- **固定 commit：** `9d864b0e12b8be620998ae1b8a998f14c4b4da1a`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 21

## 仓库摘要

该仓库是一个 protein-DNA binding site prediction 项目的静态快照，含模型代码、Raw_data 文本、Graph_46 图碎片和三份 .pt 权重，但未见 LICENSE，且未执行任何代码。

## 可复用模块与资源

### checkpoints

- `Weights/573_129.pt`
  - 能力：model_weight
  - 用途：已保存权重文件；对应的训练配置和 split 关系未核实。
  - 复用状态：blocked；类型：model_weight
- `Weights/573_181.pt`
  - 能力：model_weight
  - 用途：已保存权重文件；对应的训练配置和 split 关系未核实。
  - 复用状态：blocked；类型：model_weight
- `Weights/646_46.pt`
  - 能力：model_weight
  - 用途：已保存权重文件；对应的训练配置和 split 关系未核实。
  - 复用状态：blocked；类型：model_weight

### datasets

- `Raw_data/DNA-573_Train.txt`
  - 能力：raw_dataset
  - 用途：训练样本文本之一；具体字段/标签格式未核实。
  - 复用状态：blocked；类型：unknown
- `Raw_data/DNA-646_Train.txt`
  - 能力：raw_dataset
  - 用途：训练样本文本之一；具体字段/标签格式未核实。
  - 复用状态：blocked；类型：unknown
- `Raw_data/DNA-129_Test.txt`
  - 能力：raw_dataset
  - 用途：测试样本文本之一；具体字段/标签格式未核实。
  - 复用状态：blocked；类型：unknown
- `Raw_data/DNA-181_Test.txt`
  - 能力：raw_dataset
  - 用途：测试样本文本之一；具体字段/标签格式未核实。
  - 复用状态：blocked；类型：unknown
- `Raw_data/DNA-46_Test.txt`
  - 能力：raw_dataset
  - 用途：测试样本文本之一；具体字段/标签格式未核实。
  - 复用状态：blocked；类型：unknown
- `Graph_46/46_1`
  - 能力：graph_feature_bundle
  - 用途：Graph_46 派生图碎片之一；生成链路与格式未核实。
  - 复用状态：blocked；类型：unknown
- `Graph_46/46_2`
  - 能力：graph_feature_bundle
  - 用途：Graph_46 派生图碎片之一；生成链路与格式未核实。
  - 复用状态：blocked；类型：unknown
- `Graph_46/46_3`
  - 能力：graph_feature_bundle
  - 用途：Graph_46 派生图碎片之一；生成链路与格式未核实。
  - 复用状态：blocked；类型：unknown
- `Graph_46/46_4`
  - 能力：graph_feature_bundle
  - 用途：Graph_46 派生图碎片之一；生成链路与格式未核实。
  - 复用状态：blocked；类型：unknown
- `Graph_46/46_5`
  - 能力：graph_feature_bundle
  - 用途：Graph_46 派生图碎片之一；生成链路与格式未核实。
  - 复用状态：blocked；类型：unknown

### evaluation

- `test.py`
  - 能力：evaluation_script
  - 用途：测试/验证脚本候选；未见指标文件或结果表。
  - 复用状态：blocked；类型：code_entry

### inference

- `model.py`
  - 能力：inference_model
  - 用途：模型定义，可配合 Weights/*.pt 做推理；未见独立 inference 脚本。
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `model.py`
  - 能力：model_architecture
  - 用途：模型结构定义；可供加载权重做推理或训练调用，但细节未核实。
  - 复用状态：blocked；类型：code_entry
- `main.py`
  - 能力：code_entry
  - 用途：脚本入口候选；可能协调数据读取、训练与保存结果。
  - 复用状态：blocked；类型：code_entry
- `utils.py`
  - 能力：helper_module
  - 用途：辅助函数与通用处理逻辑。
  - 复用状态：blocked；类型：code_entry
- `test.py`
  - 能力：evaluation_script
  - 用途：测试/验证脚本候选；未见独立评测报告。
  - 复用状态：blocked；类型：code_entry
- `Graph_46/Merge-Files.ps1`
  - 能力：code_entry
  - 用途：Graph_46 片段合并脚本候选；可用于整理派生图文件。
  - 复用状态：blocked；类型：code_entry

### training

- `main.py`
  - 能力：training_entrypoint
  - 用途：训练/实验入口候选；静态清单未证明其实际执行。
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

- 未读取文件内容，无法确认模型结构、损失函数、采样策略与超参。
- 未见独立配置或依赖清单，main.py、test.py 与 utils.py 的真实职责仍需人工验证。
- Graph_46 片段的生成流程、Raw_data 的来源与标签规范未知。
- 三份 Weights/*.pt 的训练数据、最佳 epoch、指标与随机种子未知。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
