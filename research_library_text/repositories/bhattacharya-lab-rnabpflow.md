# Bhattacharya-Lab/RNAbpFlow

- **仓库：** [https://github.com/Bhattacharya-Lab/RNAbpFlow](https://github.com/Bhattacharya-Lab/RNAbpFlow)
- **固定 commit：** `e8b1c077f7951d4d6ebe00c851d22c37777dfc9f`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0
- **资产记录数：** 12

## 仓库摘要

该冻结仓库主要提供 RNAbpFlow 的推理侧代码：包含 RNA 3D 结构生成模型、几何/数据处理模块、`inference.py` 与 `configs/inference.yaml`，并跟踪了少量示例输入/输出；未见训练入口、评估脚本或 checkpoint。

## 可复用模块与资源

### datasets

- `Inputs/2oiu_P/2oiu_P.fasta`
  - 能力：example_inputs
  - 用途：示例 RNA 序列输入；同目录含 `map1.npy`、`map2.npy`、`map3.npy` 作为配套特征。
  - 复用状态：partial；类型：unknown
- `Inputs/8tux_R/8tux_R.fasta`
  - 能力：example_inputs
  - 用途：示例 RNA 序列输入；同目录含 `map1.npy`、`map2.npy`、`map3.npy` 作为配套特征。
  - 复用状态：partial；类型：unknown
- `Predictions/2oiu_P/Sample_0.pdb`
  - 能力：example_outputs
  - 用途：仓库内示例生成结构输出；同目录可见 `.cif`/`.pdb` 成对样例，用于人工对照而非独立评测基准。
  - 复用状态：partial；类型：unknown

### inference

- `inference.py`
  - 能力：inference_entrypoint
  - 用途：命令行/脚本入口，串联配置、模型加载与生成推理。
  - 复用状态：ready_for_review；类型：code_entry
- `configs/inference.yaml`
  - 能力：config_recipe
  - 用途：推理参数、输入输出路径与运行配置。
  - 复用状态：ready_for_review；类型：config
- `src/models/flow_module_inf.py`
  - 能力：inference_module
  - 用途：推理侧模块封装、采样与生成流程。
  - 复用状态：ready_for_review；类型：code_entry
- `src/data/interpolant_inf.py`
  - 能力：inference_module
  - 用途：推理时的 interpolant / 连续采样逻辑。
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `src/models/flow_model.py`
  - 能力：model_architecture
  - 用途：RNA 3D 结构生成主干模型；将节点、边与几何模块组合为 flow matching 生成器。
  - 复用状态：ready_for_review；类型：code_entry
- `src/models/ipa_pytorch.py`
  - 能力：model_architecture
  - 用途：几何/IPA 风格模块，支撑结构更新与坐标相关计算。
  - 复用状态：ready_for_review；类型：code_entry
- `src/data/dataset.py`
  - 能力：data_loader
  - 用途：样本组织、特征读取与数据集构造。
  - 复用状态：ready_for_review；类型：code_entry
- `src/data/rigid_utils.py`
  - 能力：data_loader
  - 用途：刚体、坐标与 SO(3) 相关工具，支撑 RNA 结构表示与变换。
  - 复用状态：ready_for_review；类型：code_entry
- `src/data/data_transform.py`
  - 能力：data_loader
  - 用途：输入特征与坐标的转换、预处理与整理。
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态审计，未运行任何代码、未安装依赖、未执行测试。
- 未发现训练入口、评估脚本或 checkpoint 文件，无法验证训练与评测流程。
- 示例输入/输出文件虽被跟踪，但静态存在不等于可复用数据许可或可复现结果。

## 仍未知

- `Inputs/*` 与 `Predictions/*` 的来源、许可和是否可再分发未独立标注。
- 冻结清单未显示任何权重/ checkpoint；是否存在外部下载模型无法确认。
- 未执行推理，不能把仓库内 `Predictions/*` 当作已验证的重现实验结果。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
