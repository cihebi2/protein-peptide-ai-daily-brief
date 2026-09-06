# ai4protein/Venus-MAXWELL

- **仓库：** [https://github.com/ai4protein/Venus-MAXWELL](https://github.com/ai4protein/Venus-MAXWELL)
- **固定 commit：** `bb26a0c3d945da17eaa2e9878da2028fc1fc8f7a`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** found
- **资产记录数：** 11

## 仓库摘要

该仓库是面向蛋白突变稳定性/ΔΔG 预测的静态代码包，包含 ESM2 与 ESM-IF 两套模型、对应数据加载与训练入口、预测脚本，以及训练/验证/测试样例数据；但未检出可直接复用的实际 checkpoint，评估代码也不完整，数据与模型许可边界仍需单独确认。

## 可复用模块与资源

### checkpoints

- `weights/.gitkeep`
  - 能力：checkpoint 占位符
  - 用途：仅保留权重目录，占位而非可直接加载的模型权重
  - 复用状态：blocked；类型：unknown

### datasets

- `example_datasets/train/fasta/1A32.fasta`
  - 能力：训练集样例
  - 用途：训练/拟合蛋白突变稳定性模型，目录内同时提供 fasta、mutant.csv 与 pdb 配套文件
  - 复用状态：partial；类型：unknown
- `example_datasets/valid/fasta/1E0L.fasta`
  - 能力：验证集样例
  - 用途：训练过程中的验证/早停检查，目录内同样提供 fasta、mutant.csv 与 pdb 配套文件
  - 复用状态：partial；类型：unknown
- `example_data/fireprotdb_1AG2_ddG.csv`
  - 能力：示例输入数据
  - 用途：单条示例预测输入；与对应 PDB 一起说明数据格式
  - 复用状态：partial；类型：unknown

### evaluation

- `example_datasets/test/fasta/fireprotdb_1AG2_ddG.fasta`
  - 能力：测试集评测样例
  - 用途：离线评测/回归测试输入；包含多来源 ddG 样例
  - 复用状态：partial；类型：unknown

### inference

- `predict_ddg.py`
  - 能力：ddG 预测入口
  - 用途：对输入蛋白突变样本执行推理并输出稳定性预测
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `maxwell/esm2/model.py`
  - 能力：ESM2 稳定性回归模块
  - 用途：蛋白突变稳定性预测主干实现
  - 复用状态：partial；类型：code_entry
- `maxwell/esmif/model.py`
  - 能力：ESM-IF 稳定性回归模块
  - 用途：结构感知的蛋白突变稳定性预测主干实现
  - 复用状态：partial；类型：code_entry
- `predict_ddg.py`
  - 能力：预测命令行入口
  - 用途：加载输入样本并输出 ddG/稳定性预测
  - 复用状态：partial；类型：code_entry

### training

- `maxwell/esm2/train.py`
  - 能力：ESM2 训练流程
  - 用途：训练 ESM2 稳定性预测模型
  - 复用状态：partial；类型：code_entry
- `maxwell/esmif/train.py`
  - 能力：ESM-IF 训练流程
  - 用途：训练 ESM-IF 稳定性预测模型
  - 复用状态：partial；类型：code_entry

## 使用限制

- 仅做静态审查，未执行代码或测试。
- 未安装依赖，无法验证训练、推理与数据流水线。
- 权重目录仅见 .gitkeep，占位不等于真实 checkpoint。
- 未发现独立的 evaluation 脚本或指标计算入口。
- 数据集来源、授权与是否为论文原始训练集，静态元数据无法确认。

## 仍未知

- example_datasets 中的大量样本是论文原始数据、裁剪样例还是复用数据，静态证据无法区分。
- 模型权重是否通过外部下载、私有发布或未跟踪文件提供，仓库内无法确认。
- check_dataset.py 的具体校验逻辑未执行，无法判断其是否覆盖全部数据格式风险。
- maxwell/prosst/.gitkeep 仅表明预留目录，未见对应实现文件。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
