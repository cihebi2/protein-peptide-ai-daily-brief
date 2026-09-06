# MiJia-ID/GGN-GO

- **仓库：** [https://github.com/MiJia-ID/GGN-GO](https://github.com/MiJia-ID/GGN-GO)
- **固定 commit：** `67f77e79b10e1aabbb26ff8bdfb5313d0f6e140c`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 19

## 仓库摘要

这是一个面向 GO 蛋白功能预测的静态仓库，包含 GVP/图网络模型、训练与推理脚本、预计算特征数据和 6 个 checkpoint；代码许可清晰为 MIT，但数据、权重与示例输出的独立许可边界未被充分标注。

## 可复用模块与资源

### checkpoints

- `Model/model_bp.pt`
  - 能力：BP checkpoint
  - 用途：BP 任务权重
  - 复用状态：unknown；类型：model_weight
- `Model/model_bp_pdb.pt`
  - 能力：BP PDB variant checkpoint
  - 用途：BP 的 PDB/结构增强变体权重
  - 复用状态：unknown；类型：model_weight
- `Model/model_cc.pt`
  - 能力：CC checkpoint
  - 用途：CC 任务权重
  - 复用状态：unknown；类型：model_weight
- `Model/model_cc_pdb.pt`
  - 能力：CC PDB variant checkpoint
  - 用途：CC 的 PDB/结构增强变体权重
  - 复用状态：unknown；类型：model_weight
- `Model/model_mf.pt`
  - 能力：MF checkpoint
  - 用途：MF 任务权重
  - 复用状态：unknown；类型：model_weight
- `Model/model_mf_pdb.pt`
  - 能力：MF PDB variant checkpoint
  - 用途：MF 的 PDB/结构增强变体权重
  - 复用状态：unknown；类型：model_weight

### datasets

- `data/nrPDB-GO_sequences.fasta`
  - 能力：nrPDB-GO 语料
  - 用途：主要 GO 训练/验证/测试序列与注释集合
  - 复用状态：unknown；类型：unknown
- `data/nrSwiss-Model-GO_sequences.fasta`
  - 能力：nrSwiss-Model-GO 语料
  - 用途：Swiss-Model 版本的序列/注释集
  - 复用状态：unknown；类型：unknown
- `data/go-basic.obo`
  - 能力：GO 本体
  - 用途：GO DAG 与术语约束
  - 复用状态：blocked；类型：unknown
- `data/ic_count.pkl`
  - 能力：GO 信息内容统计
  - 用途：用于 GO term 的信息内容统计或加权
  - 复用状态：unknown；类型：unknown
- `data/bpDataSet/structure_data/3GDT-A.npy`
  - 能力：bpDataSet 预计算多模态特征
  - 用途：仓库内置的结构、DSSP、ESM2、ProtTrans 预计算张量示例
  - 复用状态：unknown；类型：unknown

### evaluation

- `Script/test.py`
  - 能力：测试/评估脚本
  - 用途：仓库内唯一显式测试入口；静态上可用于评估流程审阅
  - 复用状态：partial；类型：code_entry

### inference

- `Script/predict.py`
  - 能力：预测执行流程
  - 用途：读取权重、运行前向推理并输出结果文件
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `Script/model.py`
  - 能力：GGN/GVP 主模型
  - 用途：定义 GO 功能预测主干网络与输出头
  - 复用状态：ready_for_review；类型：code_entry
- `Script/my_Features.py`
  - 能力：多尺度特征与数据预处理
  - 用途：组织 DSSP、ESM2、ProtTrans 与结构输入
  - 复用状态：ready_for_review；类型：code_entry
- `Script/nt_xent.py`
  - 能力：对比学习/损失辅助模块
  - 用途：为训练过程提供 contrastive loss 或辅助目标
  - 复用状态：ready_for_review；类型：code_entry
- `Script/train.py`
  - 能力：训练入口
  - 用途：启动模型训练与数据装配
  - 复用状态：ready_for_review；类型：code_entry
- `Script/predict.py`
  - 能力：推理入口
  - 用途：加载权重并生成预测结果
  - 复用状态：ready_for_review；类型：code_entry

### training

- `Script/train.py`
  - 能力：监督训练流水线
  - 用途：组织 batch、loss、验证与 checkpoint 保存
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态清单审查，未执行仓库代码、训练或推理。
- 依赖未安装，无法验证 `requirements.txt` / `environment.yml` 能否复现。
- 未见独立 metrics 报告、CI 或测试结果，不能据此证明性能。
- `Predict/` 下的 CSV 更像示例输出或中间结果，不能当作复现证据。
- `go-basic.obo` 与其他数据/权重文件的独立授权未被完整确认。

## 仍未知

- `Script/test.py` 是否与论文正式评测流程一致，静态路径无法确认。
- `*_pdb.pt` 与非 `*_pdb.pt` checkpoint 的具体差异只能根据命名推断。
- `data/bpDataSet/` 是否为正式训练集、验证集还是示例子集，未从清单本身确认。
- `ic_count.pkl`、预计算 `.npy` 特征与外部模型/数据的衍生关系未被逐一追踪。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
