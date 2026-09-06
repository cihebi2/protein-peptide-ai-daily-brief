# AaronChen007/neoantigen

- **仓库：** [https://github.com/AaronChen007/neoantigen](https://github.com/AaronChen007/neoantigen)
- **固定 commit：** `f445d4a57218168d81fa98ef3aaa68e5622f73f3`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 10

## 仓库摘要

该仓库与 CNNeoPP 论文高度相关；静态清单仅确认了 3 个模型 notebook、1 个 workflow 文档、环境配置、训练/独立/示例数据以及 MIT 许可，未见独立训练入口、推理脚本、评估代码或 checkpoint，因此只能做静态复用评审。

## 可复用模块与资源

### datasets

- `training_data/training_data.xlsx`
  - 能力：training_dataset
  - 用途：从路径名看应为训练数据表。
  - 复用状态：partial；类型：unknown
- `training_data/MHC_pseudo.dat`
  - 能力：mhc_pseudo_resource
  - 用途：从文件名看应为 MHC pseudo 序列/特征资源，可能用于编码或预处理。
  - 复用状态：partial；类型：unknown
- `independent dataset/independent dataset.xlsx`
  - 能力：independent_evaluation_dataset
  - 用途：从路径名看应为独立测试/验证集。
  - 复用状态：partial；类型：unknown
- `data/example/input_features.csv`
  - 能力：example_input_features
  - 用途：从路径名看应为示例输入特征。
  - 复用状态：partial；类型：unknown
- `data/example/example_output.csv`
  - 能力：example_output
  - 用途：从路径名看应为示例输出结果。
  - 复用状态：partial；类型：unknown

### reusable_assets

- `models/CNNeo_CNN_BioBERT.ipynb`
  - 能力：model_architecture_notebook
  - 用途：从路径名看应为 CNN-BioBERT 版本的模型 notebook，可能包含结构定义与训练流程；未打开内容。
  - 复用状态：partial；类型：unknown
- `models/CNNeo_FCNN_BioBERT.ipynb`
  - 能力：model_architecture_notebook
  - 用途：从路径名看应为 FCNN-BioBERT 版本的模型 notebook，可能包含结构定义与训练流程；未打开内容。
  - 复用状态：partial；类型：unknown
- `models/CNNeo_FCN_TF.ipynb`
  - 能力：model_architecture_notebook
  - 用途：从路径名看应为 FCN-TF 版本的模型 notebook，可能包含结构定义与训练流程；未打开内容。
  - 复用状态：partial；类型：unknown
- `CNNeoPP workflow.docx`
  - 能力：workflow_documentation
  - 用途：从文件名看像是 CNNeoPP workflow 说明文档/流程图；未核实内容。
  - 复用状态：unknown；类型：unknown
- `environment.yml`
  - 能力：runtime_environment_recipe
  - 用途：定义 Conda 依赖环境，可能用于重建运行环境；未安装验证。
  - 复用状态：partial；类型：config

## 使用限制

- 仅基于静态清单与路径名，未读取 notebook、表格或文档内容。
- 未发现独立 training entrypoint、inference、evaluation 或 checkpoint 文件。
- `environment.yml` 仅说明依赖意图，未实际安装或验证运行环境。
- 仓库中的数据与可能的模型产物未见独立许可边界，不能推定与代码同权利范围。

## 仍未知

- 三个模型 notebook 内部是否同时包含训练、推理与评估逻辑未知。
- `CNNeoPP workflow.docx` 的具体内容与是否可复用未知。
- `training_data.xlsx`、`independent dataset.xlsx` 与 `MHC_pseudo.dat` 的来源、预处理方式及第三方依赖未知。
- `example_output.csv` 是否为真实模型输出还是手工示例未知。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
