# LtECoD/CoFlow

- **仓库：** [https://github.com/LtECoD/CoFlow](https://github.com/LtECoD/CoFlow)
- **固定 commit：** `b3c9d609e5ff215bc731d946a410e6f51199bc3c`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 12

## 仓库摘要

这是一个面向蛋白序列-结构联合设计的仓库。冻结清单显示核心可复用资产集中在模型、flow、数据预处理、训练入口和微调配置；未见独立 inference、evaluation 或 checkpoint 资产，也未发现 LICENSE 文件。由于仅做静态审计，训练可复现性、数据归属与权重来源仍无法确认。

## 可复用模块与资源

### datasets

- `7LUH.pdb`
  - 能力：single_pdb_example
  - 用途：仓库中唯一可见的结构文件，可能作为示例输入或测试样例
  - 复用状态：unknown；类型：unknown

### reusable_assets

- `source/model.py`
  - 能力：model_architecture
  - 用途：定义蛋白序列/结构联合生成模型的核心结构
  - 复用状态：blocked；类型：code_entry
- `source/flow.py`
  - 能力：flow_core
  - 用途：提供 generative flow 相关变换与采样逻辑
  - 复用状态：blocked；类型：code_entry
- `source/module.py`
  - 能力：module_core
  - 用途：封装模型子模块与层级组件
  - 复用状态：blocked；类型：code_entry
- `source/data.py`
  - 能力：data_loader
  - 用途：读取并组织训练所需输入数据
  - 复用状态：blocked；类型：code_entry
- `source/preprocess.py`
  - 能力：preprocessing
  - 用途：对结构/序列输入做预处理
  - 复用状态：blocked；类型：code_entry
- `source/train.py`
  - 能力：training_entrypoint
  - 用途：训练主程序入口
  - 复用状态：blocked；类型：code_entry
- `train.sh`
  - 能力：training_script
  - 用途：命令行训练启动脚本
  - 复用状态：blocked；类型：code_entry
- `config/finetune.yaml`
  - 能力：config_recipe
  - 用途：微调超参数与运行配置
  - 复用状态：blocked；类型：config

### training

- `source/train.py`
  - 能力：training_entrypoint
  - 用途：主训练流程
  - 复用状态：blocked；类型：code_entry
- `train.sh`
  - 能力：launch_script
  - 用途：启动训练命令
  - 复用状态：blocked；类型：code_entry
- `config/finetune.yaml`
  - 能力：finetune_config
  - 用途：训练/微调配置
  - 复用状态：blocked；类型：config

## 使用限制

- 仅做静态审计，未执行仓库代码
- 依赖未安装，无法验证运行环境
- 未运行测试或复现实验
- 未确认 tracked data file 的真实来源与用途
- 未发现 checkpoint 资产，无法核验权重可用性

## 仍未知

- 7LUH.pdb 是否属于训练集、测试集或仅为示例文件无法确认
- source/train.py 是否同时包含评估或推理逻辑无法仅凭路径确定
- README.md 的具体许可、数据下载与使用说明未展开核对
- source/flow.py、source/module.py 的外部依赖与版本约束未解析

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
