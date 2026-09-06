# KavrakiLab/TL-MHC

- **仓库：** [https://github.com/KavrakiLab/TL-MHC](https://github.com/KavrakiLab/TL-MHC)
- **固定 commit：** `ec58087383f59f8afa9c1e8fbc8c5bb68e752ccb`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 20

## 仓库摘要

该冻结仓库包含 TLBind、TLImm、TLStab 三个子模块，覆盖 pMHC binding、immunogenicity 与 stability 的训练、推理、结果输出和 checkpoint；但未检出 LICENSE，且仅做静态盘点，无法证明可执行或可复现。

## 可复用模块与资源

### checkpoints

- `TLBind/models/Pretrained_BA-EL.pt`
  - 能力：TLBind 预训练权重
  - 用途：binding affinity / eluted ligand 预训练 checkpoint
  - 复用状态：unknown；类型：model_weight
- `TLImm/models/weights/TLImm_1.pt`
  - 能力：TLImm 权重集合
  - 用途：15 个 TLImm checkpoint 中的代表文件，供 ensemble 或多次实验加载
  - 复用状态：unknown；类型：model_weight
- `TLStab/models/weights/TLStab_1.pt`
  - 能力：TLStab 权重集合
  - 用途：10 个 TLStab checkpoint 中的代表文件，供 ensemble 或多次实验加载
  - 复用状态：unknown；类型：model_weight

### datasets

- `TLBind/examples/SARS-CoV-2_peptides_example.csv`
  - 能力：SARS-CoV-2 示例输入
  - 用途：各任务的示例输入 CSV
  - 复用状态：unknown；类型：unknown
- `TLBind/misc/updated_pseudosequences.csv`
  - 能力：MHC pseudosequence 特征表
  - 用途：HLA/MHC pseudosequence 输入特征
  - 复用状态：unknown；类型：unknown
- `TLStab/misc/datasets/training_data/cleaned_data/cleaned_train_data.csv`
  - 能力：TLStab 清洗训练数据与 fold 划分
  - 用途：TLStab 的清洗数据和 10-fold 划分
  - 复用状态：unknown；类型：unknown
- `TLImm/misc/training_data/cleaned_data/Bin_train_data.csv`
  - 能力：TLImm 训练数据与 fold 划分
  - 用途：TLImm 的二分类/连续值训练集与多套 fold 划分
  - 复用状态：unknown；类型：unknown

### evaluation

- `TLImm/src/RF_feature_importance_plots.R`
  - 能力：特征重要性与后验分析
  - 用途：绘制 feature importance / 分析图
  - 复用状态：blocked；类型：code_entry
- `TLImm/TLImm_out.csv`
  - 能力：示例输出与结果表
  - 用途：示例预测结果、输出模板与结果表
  - 复用状态：unknown；类型：unknown
- `TLStab/misc/datasets/Ebola_pan_results_v2.csv`
  - 能力：Ebola/Pox 泛抗原结果表
  - 用途：外部样本的预测/验证结果表
  - 复用状态：unknown；类型：unknown

### inference

- `TLBind/TLBind.py`
  - 能力：TLBind 命令行推理
  - 用途：对输入 peptides 运行 binding prediction
  - 复用状态：blocked；类型：code_entry
- `TLImm/TLImm.py`
  - 能力：TLImm 命令行推理
  - 用途：对输入样本运行 immunogenicity prediction
  - 复用状态：blocked；类型：code_entry
- `TLStab/TLStab.py`
  - 能力：TLStab 命令行推理
  - 用途：对输入 peptides 运行 stability prediction
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `TLBind/model.py`
  - 能力：共享模型定义
  - 用途：三模块共享同一 model.py，定义 pMHC 预测网络主体
  - 复用状态：blocked；类型：code_entry
- `TLBind/dataloader.py`
  - 能力：共享数据装载器
  - 用途：读取 peptide/MHC 输入并构造模型特征
  - 复用状态：blocked；类型：code_entry

### training

- `TLBind/src/train.py`
  - 能力：TLBind 训练入口
  - 用途：训练/微调 binding model
  - 复用状态：blocked；类型：code_entry
- `TLBind/src/5-fold_train.py`
  - 能力：TLBind 交叉验证训练脚本
  - 用途：5-fold 训练与评估流程
  - 复用状态：blocked；类型：code_entry
- `TLStab/src/train.py`
  - 能力：TLStab 训练入口
  - 用途：训练 stability model
  - 复用状态：blocked；类型：code_entry
- `TLStab/src/10-fold_train.py`
  - 能力：TLStab 交叉验证训练脚本
  - 用途：10-fold 训练与评估流程
  - 复用状态：blocked；类型：code_entry
- `TLBind/src/Dataset_processing.R`
  - 能力：数据清洗与 fold 生成脚本
  - 用途：数据清洗、分层与训练集划分
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态盘点，未安装依赖、未运行训练/推理/测试。
- 未检出 LICENSE，无法确认代码、数据与模型的再利用边界。
- 文件存在不等于训练完成、评估完成或论文结果可复现。
- 部分大文件可能受 LFS/promisor 限制，未验证内容完整性。

## 仍未知

- TLImm 的独立训练入口未在冻结清单中出现，训练流程是否外置不明。
- 各 CSV 数据的原始来源、分发许可与去重规则未确认。
- 各 .pt 权重是否为仓库自训或外部预训练迁移而来未确认。
- TLImm_out.csv / TLStab_out.csv 是否对应正式论文评估未验证。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
