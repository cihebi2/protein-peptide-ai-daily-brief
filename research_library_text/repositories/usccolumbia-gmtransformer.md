# usccolumbia/gmtransformer

- **仓库：** [https://github.com/usccolumbia/gmtransformer](https://github.com/usccolumbia/gmtransformer)
- **固定 commit：** `ef03c26cd167a8f1cd4f23ac02a83d2f7893000b`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **资产记录数：** 8

## 仓库摘要

仓库主要提供分子生成训练/推理脚本与两个数据压缩包；未见评测入口或检查点，代码许可为 Apache-2.0，但数据许可未明。

## 可复用模块与资源

### datasets

- `SELFIES_data.zip`
  - 能力：SELFIES molecular corpus archive
  - 用途：训练/预处理输入数据包；仅根据文件名判断为 SELFIES 编码分子数据，内容未解包验证。
  - 复用状态：partial；类型：unknown
- `SMILE_data.zip`
  - 能力：SMILES molecular corpus archive
  - 用途：训练/预处理输入数据包；仅根据文件名判断为 SMILES 分子数据，内容未解包验证。
  - 复用状态：partial；类型：unknown

### inference

- `generate.sh`
  - 能力：molecule generation inference
  - 用途：推理/采样入口脚本，负责触发生成流程。
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `train.sh`
  - 能力：molecule generation training entrypoint
  - 用途：启动训练流程的 shell 入口；仅静态确认存在，未执行。
  - 复用状态：ready_for_review；类型：code_entry
- `generate.sh`
  - 能力：molecule generation inference entrypoint
  - 用途：启动生成/采样流程的 shell 入口；仅静态确认存在，未执行。
  - 复用状态：ready_for_review；类型：code_entry
- `selfiestoken2smiles.py`
  - 能力：SELFIES to SMILES conversion helper
  - 用途：SELFIES token 到 SMILES 的转换辅助脚本，疑似用于预处理或后处理。
  - 复用状态：ready_for_review；类型：code_entry
- `convert2smiles.py`
  - 能力：SMILES normalization/conversion helper
  - 用途：分子字符串转换辅助脚本，疑似用于数据准备或输出整理。
  - 复用状态：ready_for_review；类型：code_entry

### training

- `train.sh`
  - 能力：molecule generation training
  - 用途：训练入口脚本，负责触发模型训练流程。
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态清单审阅，未运行仓库代码。
- 未安装依赖、未执行测试、未验证训练或生成结果。
- 两个 zip 数据包未解包，内容、来源与数据许可均未核实。
- 冻结仓库未见显式 checkpoints、evaluation 产物或模型权重文件。

## 仍未知

- SELFIES_data.zip 和 SMILE_data.zip 的具体内容与来源。
- convert2smiles.py 与 selfiestoken2smiles.py 的真实调用链与输入输出约束。
- train.sh 与 generate.sh 是否依赖外部下载资源或未冻结文件。
- 是否存在未被静态清单覆盖的隐含权重、评测脚本或数据许可声明。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
