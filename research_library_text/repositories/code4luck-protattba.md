# code4luck/protattba

- **仓库：** [https://github.com/code4luck/protattba](https://github.com/code4luck/protattba)
- **固定 commit：** `9adbf9899a7b3aa69da4ea00f5b3ca9e14bddbbd`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 31

## 仓库摘要

仓库实现了抗体结合亲和力变化的序列级预测，覆盖 cross_validation 与 seq-identity_sig-mul 两条训练/评估链路，包含模型、数据拆分、测试回调和注意力可视化；但未见 LICENSE、checkpoint 或独立推理入口，静态审查无法验证复现。

## 可复用模块与资源

### datasets

- `source_data/AB-bind/AB-Bind_experimental_data.csv`
  - 能力：AB-Bind 原始实验数据
  - 用途：提供抗体-抗原结合亲和力变化的原始标签来源
  - 复用状态：blocked；类型：unknown
- `source_data/AB-bind/PDB/1DQJ.pdb`
  - 能力：AB-Bind 结构样本
  - 用途：AB-Bind 结构输入示例之一，属于 PDB 结构集合
  - 复用状态：blocked；类型：unknown
- `source_data/SKEMPI/SKEMPI_1.1.csv`
  - 能力：SKEMPI 1.1 原始数据
  - 用途：提供 SKEMPI 相关标签来源
  - 复用状态：blocked；类型：unknown
- `source_data/SKEMPI/S1131/PDB/1A22.pdb`
  - 能力：S1131 结构样本
  - 用途：S1131 结构输入示例之一，属于 PDB 结构集合
  - 复用状态：blocked；类型：unknown
- `cross_validation/data/csv/AB1101.csv`
  - 能力：cross_validation 数据集 AB1101
  - 用途：AB1101 交叉验证分支的数据切分
  - 复用状态：blocked；类型：unknown
- `cross_validation/data/csv/AB645.csv`
  - 能力：cross_validation 数据集 AB645
  - 用途：AB645 交叉验证分支的数据切分
  - 复用状态：blocked；类型：unknown
- `cross_validation/data/csv/S1131.csv`
  - 能力：cross_validation 数据集 S1131
  - 用途：S1131 交叉验证分支的数据切分
  - 复用状态：blocked；类型：unknown
- `seq-identity_sig-mul/data/identity_data/csv/AB1101.csv`
  - 能力：identity 数据集 AB1101
  - 用途：AB1101 的 sequence-identity 数据输入
  - 复用状态：blocked；类型：unknown
- `seq-identity_sig-mul/data/identity_data/mmseqs_file/AB1101_file/AB1101_clu.tsv`
  - 能力：MMseqs 聚类文件
  - 用途：辅助 sequence-identity 划分与聚类约束
  - 复用状态：blocked；类型：unknown
- `seq-identity_sig-mul/data/sigmul_data/AB1101_single.csv`
  - 能力：sigmul 单突变样本
  - 用途：sigmul 分支中的单突变样本集合
  - 复用状态：blocked；类型：unknown
- `seq-identity_sig-mul/data/sigmul_data/AB1101_multiple.csv`
  - 能力：sigmul 多突变样本
  - 用途：sigmul 分支中的多突变样本集合
  - 复用状态：blocked；类型：unknown

### evaluation

- `seq-identity_sig-mul/eval.py`
  - 能力：评估入口
  - 用途：执行 seq-identity_sig-mul 的评估流程
  - 复用状态：blocked；类型：code_entry
- `seq-identity_sig-mul/utils/test_callback.py`
  - 能力：测试回调
  - 用途：记录或汇总测试阶段指标
  - 复用状态：blocked；类型：code_entry
- `cross_validation/utils/test_callback.py`
  - 能力：测试回调
  - 用途：记录或汇总 cross_validation 阶段指标
  - 复用状态：blocked；类型：code_entry
- `cross_validation/results/AB1101_results.csv`
  - 能力：交叉验证结果
  - 用途：保存 AB1101 的评估输出
  - 复用状态：blocked；类型：unknown
- `cross_validation/results/AB645_results.csv`
  - 能力：交叉验证结果
  - 用途：保存 AB645 的评估输出
  - 复用状态：blocked；类型：unknown
- `cross_validation/results/S1131_results.csv`
  - 能力：交叉验证结果
  - 用途：保存 S1131 的评估输出
  - 复用状态：blocked；类型：unknown
- `seq-identity_sig-mul/results/result_sigmul/sigmul_res.csv`
  - 能力：sigmul 结果汇总
  - 用途：保存 sigmul 分支结果汇总
  - 复用状态：blocked；类型：unknown

### reusable_assets

- `seq-identity_sig-mul/model.py`
  - 能力：核心序列预测模型
  - 用途：定义主模型结构，用于亲和力变化预测
  - 复用状态：blocked；类型：code_entry
- `seq-identity_sig-mul/model_module/rope_attn.py`
  - 能力：RoPE attention 模块
  - 用途：提供注意力层的相对位置编码实现
  - 复用状态：blocked；类型：code_entry
- `seq-identity_sig-mul/lit_model.py`
  - 能力：Lightning 封装
  - 用途：封装训练/验证/测试流程
  - 复用状态：blocked；类型：code_entry
- `seq-identity_sig-mul/dataset.py`
  - 能力：数据集封装
  - 用途：构建 identity 与 sigmul 相关输入样本
  - 复用状态：blocked；类型：code_entry
- `cross_validation/src_ab1101/model.py`
  - 能力：AB1101 模型变体
  - 用途：AB1101 交叉验证分支的模型定义
  - 复用状态：blocked；类型：code_entry
- `cross_validation/src_ab645/model.py`
  - 能力：AB645 模型变体
  - 用途：AB645 交叉验证分支的模型定义
  - 复用状态：blocked；类型：code_entry
- `cross_validation/src_s1131/model.py`
  - 能力：S1131 模型变体
  - 用途：S1131 交叉验证分支的模型定义
  - 复用状态：blocked；类型：code_entry
- `cross_validation/utils/data_split.py`
  - 能力：交叉验证拆分逻辑
  - 用途：生成或管理 cross-validation 数据划分
  - 复用状态：blocked；类型：code_entry

### training

- `seq-identity_sig-mul/trainer_identity.py`
  - 能力：identity 训练流程
  - 用途：训练 identity 分支模型
  - 复用状态：blocked；类型：code_entry
- `seq-identity_sig-mul/trainer_sigmul.py`
  - 能力：sigmul 训练流程
  - 用途：训练 sigmul 分支模型
  - 复用状态：blocked；类型：code_entry
- `cross_validation/src_ab1101/trainer.py`
  - 能力：AB1101 训练模块
  - 用途：AB1101 交叉验证训练模块
  - 复用状态：blocked；类型：code_entry
- `cross_validation/src_ab645/trainer.py`
  - 能力：AB645 训练模块
  - 用途：AB645 交叉验证训练模块
  - 复用状态：blocked；类型：code_entry
- `cross_validation/src_s1131/trainer.py`
  - 能力：S1131 训练模块
  - 用途：S1131 交叉验证训练模块
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态审查，未运行代码、测试、训练或推理。
- 未见 LICENSE；在许可未澄清前，代码与数据不应视为可直接复用。
- 未见 checkpoint/model weight；tracked_paths 中的 .pkl 更像注意力或分析产物，不等同模型权重。
- 依赖未安装、子模块未初始化，外部环境与完整运行链路不可验证。

## 仍未知

- 训练超参数、优化器、epoch、batch size 与具体 split 规则未从静态路径确认。
- 评估脚本与结果 CSV 的具体指标列和主结果数值未核实。
- source_data 中 AB-Bind / SKEMPI 上游授权与清洗流程未核实。
- attention_analysis 下的 .pkl / .png 是否仅用于解释性分析、是否进入论文主流程未核实。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
