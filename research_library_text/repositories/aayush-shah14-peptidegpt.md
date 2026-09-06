# aayush-shah14/PeptideGPT

- **仓库：** [https://github.com/aayush-shah14/PeptideGPT](https://github.com/aayush-shah14/PeptideGPT)
- **固定 commit：** `9e452c8b1536748b0d34fcdceeab528432fa4f41`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 9

## 仓库摘要

该冻结仓库仅静态暴露 `inference.py`、`requirements.txt` 和多组数据文件；未见 training 入口、evaluation 脚本、checkpoint 或 LICENSE。`Data/Soluble/sol_{train,test}.txt` 虽在 tracked_paths 中，但未被 bundled_data 能力显式标注，故其来源与用途仍需保守处理。

## 可复用模块与资源

### datasets

- `Data/Hemolytic/hemo_train.csv`
  - 能力：hemolytic peptide dataset
  - 用途：溶血性相关训练集分片
  - 复用状态：blocked；类型：unknown
- `Data/Hemolytic/hemo_test.csv`
  - 能力：hemolytic peptide dataset
  - 用途：溶血性相关测试集分片
  - 复用状态：blocked；类型：unknown
- `Data/Non-Fouling/nf_train.csv`
  - 能力：Non-Fouling peptide dataset
  - 用途：Non-Fouling 训练集分片
  - 复用状态：blocked；类型：unknown
- `Data/Non-Fouling/nf_test.csv`
  - 能力：Non-Fouling peptide dataset
  - 用途：Non-Fouling 测试集分片
  - 复用状态：blocked；类型：unknown
- `Data/Soluble/sol_train.txt`
  - 能力：solubility peptide dataset
  - 用途：Soluble 训练集文本分片；具体字段格式未核实
  - 复用状态：blocked；类型：unknown
- `Data/Soluble/sol_test.txt`
  - 能力：solubility peptide dataset
  - 用途：Soluble 测试集文本分片；具体字段格式未核实
  - 复用状态：blocked；类型：unknown
- `Data/hull_equations.npz`
  - 能力：auxiliary constraint data
  - 用途：辅助约束/几何数据；从文件名推断与 hull equations 相关
  - 复用状态：blocked；类型：unknown

### inference

- `inference.py`
  - 能力：peptide candidate generation inference
  - 用途：推理入口；具体生成/打分逻辑未从静态清单核实
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `requirements.txt`
  - 能力：environment dependency specification
  - 用途：Python 依赖清单，用于搭建运行环境
  - 复用状态：unknown；类型：unknown

## 使用限制

- 仅静态盘点，未执行代码或测试
- 依赖未安装，无法验证运行时行为
- 未发现 training entrypoint、training module、evaluation 脚本或 checkpoints
- repository 级 LICENSE 缺失，直接复用受限
- tracked_paths 中的 Soluble 文本文件未进入 bundled_data 能力条目，来源与用途仍不确定

## 仍未知

- README.md 具体内容未展开
- inference.py 的模型结构、解码策略和参数未核实
- Data/Hemolytic 与 Data/Non-Fouling 文件的外部来源与授权未核实
- Data/Soluble/sol_{train,test}.txt 的字段格式与任务定位未核实
- Data/hull_equations.npz 的生成流程与授权未核实

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
