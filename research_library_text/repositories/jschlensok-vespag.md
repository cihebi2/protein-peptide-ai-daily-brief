# jschlensok/vespag

- **仓库：** [https://github.com/jschlensok/vespag](https://github.com/jschlensok/vespag)
- **固定 commit：** `3d4758252dbd423249e694d6f7d195c707f72a92`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0
- **资产记录数：** 27

## 仓库摘要

该仓库静态呈现出一套面向蛋白 fitness prediction 的完整流水线：以 ESM2/ProtT5 相关权重或嵌入为输入，提供模型定义、训练入口、推断脚本、评估模块与测试夹具；同时包含示例 FASTA、DMS/score CSV、HDF5 embeddings 和三份 .pt 权重文件。代码许可证为 GPL-3.0，但数据与权重未见独立许可说明，且未执行代码或测试。

## 可复用模块与资源

### checkpoints

- `model_weights/v1/esm2.pt`
  - 能力：模型权重
  - 用途：v1 权重文件/检查点
  - 复用状态：blocked；类型：model_weight
- `model_weights/v2/esm2.pt`
  - 能力：模型权重
  - 用途：v2 权重文件/检查点
  - 复用状态：blocked；类型：model_weight
- `model_weights/v2/prott5.pt`
  - 能力：模型权重
  - 用途：v2 权重文件/检查点
  - 复用状态：blocked；类型：model_weight

### datasets

- `data/example/example.fasta`
  - 能力：示例输入序列
  - 用途：仓库示例 FASTA
  - 复用状态：partial；类型：unknown
- `tests/test_data/test.fasta`
  - 能力：测试输入序列
  - 用途：测试用 FASTA
  - 复用状态：partial；类型：unknown
- `tests/test_data/dms_scores/dms_scores.csv`
  - 能力：DMS 基准表
  - 用途：DMS 标签/真值表
  - 复用状态：partial；类型：unknown
- `tests/test_data/dms_scores/raw_vespag_scores_esm2.csv`
  - 能力：ESM2 原始分数夹具
  - 用途：ESM2 分数输出对照
  - 复用状态：partial；类型：unknown
- `tests/test_data/dms_scores/raw_vespag_scores_prott5.csv`
  - 能力：ProtT5 原始分数夹具
  - 用途：ProtT5 分数输出对照
  - 复用状态：partial；类型：unknown
- `tests/test_data/esm2_embeddings.h5`
  - 能力：预计算 embeddings 夹具
  - 用途：ESM2 embedding 测试数据
  - 复用状态：partial；类型：unknown
- `tests/test_data/prott5_embeddings.h5`
  - 能力：预计算 embeddings 夹具
  - 用途：ProtT5 embedding 测试数据
  - 复用状态：partial；类型：unknown
- `tests/test_data/scores_esm2/seq1.csv`
  - 能力：按序列分数夹具
  - 用途：ESM2 序列级分数对照
  - 复用状态：partial；类型：unknown
- `tests/test_data/scores_esm2/seq2.csv`
  - 能力：按序列分数夹具
  - 用途：ESM2 序列级分数对照
  - 复用状态：partial；类型：unknown
- `tests/test_data/scores_prott5/seq1.csv`
  - 能力：按序列分数夹具
  - 用途：ProtT5 序列级分数对照
  - 复用状态：partial；类型：unknown
- `tests/test_data/scores_prott5/seq2.csv`
  - 能力：按序列分数夹具
  - 用途：ProtT5 序列级分数对照
  - 复用状态：partial；类型：unknown

### evaluation

- `vespag/eval/eval.py`
  - 能力：评估入口
  - 用途：结果评估与汇总
  - 复用状态：ready_for_review；类型：code_entry
- `vespag/utils/eval.py`
  - 能力：评估工具
  - 用途：指标计算与结果整理辅助
  - 复用状态：ready_for_review；类型：code_entry

### inference

- `vespag/predict/predict.py`
  - 能力：推断入口
  - 用途：序列打分与预测流程
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `vespag/models/cnn.py`
  - 能力：蛋白 fitness 预测模型结构
  - 用途：CNN 预测器结构
  - 复用状态：ready_for_review；类型：code_entry
- `vespag/models/fnn.py`
  - 能力：蛋白 fitness 预测模型结构
  - 用途：FNN 预测器结构
  - 复用状态：ready_for_review；类型：code_entry
- `vespag/models/utils.py`
  - 能力：共享模型工具
  - 用途：模型相关辅助函数
  - 复用状态：ready_for_review；类型：code_entry
- `vespag/data/embeddings.py`
  - 能力：嵌入数据加载
  - 用途：加载与处理 ESM2/ProtT5 embeddings
  - 复用状态：ready_for_review；类型：code_entry
- `vespag/data/gemme.py`
  - 能力：GEMME/突变数据适配
  - 用途：适配突变与打分数据源
  - 复用状态：ready_for_review；类型：code_entry
- `vespag/utils/mutations.py`
  - 能力：突变解析工具
  - 用途：突变表示与序列编辑辅助
  - 复用状态：ready_for_review；类型：code_entry
- `vespag/utils/proteingym.py`
  - 能力：ProteinGym 工具
  - 用途：基准数据与分数处理辅助
  - 复用状态：ready_for_review；类型：code_entry

### training

- `vespag/training/train.py`
  - 能力：训练入口
  - 用途：训练命令行/入口脚本
  - 复用状态：ready_for_review；类型：code_entry
- `vespag/training/trainer.py`
  - 能力：训练循环
  - 用途：训练过程封装与优化逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `vespag/training/dataset.py`
  - 能力：训练数据集构造
  - 用途：训练样本读取与组装
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态清单审查，未执行代码、训练或测试。
- 依赖未安装，无法验证导入、命令行或运行路径。
- `model_weights/*.pt`、HDF5 夹具与 CSV 夹具的生成来源和可再分发权限未被静态证实。
- tracked 路径存在不等于可复现，尤其是大文件与 checkpoint。

## 仍未知

- `model_weights/v1/esm2.pt`、`model_weights/v2/esm2.pt`、`model_weights/v2/prott5.pt` 是项目自训练检查点还是外部 vendored 权重，无法仅凭路径确认。
- `tests/test_data/dms_scores/*` 与 `scores_*/*.csv` 是否对应论文主结果或仅为测试夹具，冻结清单无法确认。
- `train.py`、`eval.py` 的具体 loss、metric、超参数和命令行参数未读取文件内容，无法确认。
- `README.md` 中的安装与使用声明未核验。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
