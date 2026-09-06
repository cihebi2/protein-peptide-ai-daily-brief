# luo-group/ConFit

- **仓库：** [https://github.com/luo-group/ConFit](https://github.com/luo-group/ConFit)
- **固定 commit：** `0135880a55bc3dee109bc0472ea29716f49360bd`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** BSD-3-Clause
- **资产记录数：** 15

## 仓库摘要

该冻结仓库以 ConFit 的训练、推理、数据加载与配置脚本为主；未见 bundled datasets、独立 evaluation 流程或 checkpoints，因此只能确认代码与配置层可复用，无法证明端到端复现。

## 可复用模块与资源

### evaluation

- `confit/stat_utils.py`
  - 能力：evaluation_helper
  - 用途：统计/汇总指标辅助，可能供评测或分析使用；仅凭路径名不能确认是完整 evaluation 流程
  - 复用状态：partial；类型：code_entry

### inference

- `confit/inference.py`
  - 能力：inference
  - 用途：推断入口与模型调用
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `confit/train.py`
  - 能力：training_module
  - 用途：训练主流程、优化与模型更新逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/train.sh`
  - 能力：training_entrypoint
  - 用途：封装并启动训练命令
  - 复用状态：ready_for_review；类型：code_entry
- `confit/data_utils.py`
  - 能力：data_loader
  - 用途：读取、拆分或预处理训练数据
  - 复用状态：ready_for_review；类型：code_entry
- `confit/inference.py`
  - 能力：inference
  - 用途：加载模型并执行推断
  - 复用状态：ready_for_review；类型：code_entry
- `config/training_config.yaml`
  - 能力：config_recipe
  - 用途：训练超参与实验配置
  - 复用状态：ready_for_review；类型：config
- `config/parallel_config.yaml`
  - 能力：config_recipe
  - 用途：并行或分布式执行配置
  - 复用状态：ready_for_review；类型：config
- `requirements.txt`
  - 能力：dependency_manifest
  - 用途：记录 Python 依赖与版本约束
  - 复用状态：ready_for_review；类型：unknown
- `scripts/download.sh`
  - 能力：download_recipe
  - 用途：下载外部数据或资源；不是 bundled data
  - 复用状态：partial；类型：code_entry

### training

- `confit/train.py`
  - 能力：training_module
  - 用途：训练主流程、优化与模型更新逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/train.sh`
  - 能力：training_entrypoint
  - 用途：训练启动脚本
  - 复用状态：ready_for_review；类型：code_entry
- `confit/data_utils.py`
  - 能力：data_loader
  - 用途：训练数据读取与预处理
  - 复用状态：ready_for_review；类型：code_entry
- `config/training_config.yaml`
  - 能力：config_recipe
  - 用途：训练参数配置
  - 复用状态：ready_for_review；类型：config
- `config/parallel_config.yaml`
  - 能力：config_recipe
  - 用途：并行/分布式训练配置
  - 复用状态：ready_for_review；类型：config

## 使用限制

- 仅做静态审查，未执行仓库代码、未安装依赖、未运行测试。
- 冻结清单中未发现 bundled datasets 或 checkpoints，无法证明端到端训练/推理可复现。
- 存在 scripts/download.sh，但其外部资源来源与许可未在冻结材料中核实。
- path presence 不能等同于实际可运行或已复现。

## 仍未知

- 外部数据下载目标、数据集许可和完整性未知。
- 训练产物/模型权重是否需要仓库外文件未知。
- confit/stat_utils.py 是否构成正式评测流程仍不确定。
- 实际训练与推理是否与论文结果一致无法从静态材料确认。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
