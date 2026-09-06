# linfeng-wang/TB-AMP-design

- **仓库：** [https://github.com/linfeng-wang/TB-AMP-design](https://github.com/linfeng-wang/TB-AMP-design)
- **固定 commit：** `c624559c5e864088cbafbcc13bd725bf0226192d`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 20

## 仓库摘要

该仓库是一个面向结核分枝杆菌靶向抗菌肽设计的静态代码与模型资产集合，核心方法围绕LSTM、BiLSTM、attention和transfer learning，兼具生成、分类、筛选与序列评估。

## 可复用模块与资源

### checkpoints

- `cache/models/best_model_lstm_generator_final.pt`
  - 能力：生成器权重
  - 用途：生成式 LSTM 最终检查点
  - 复用状态：blocked；类型：model_weight
- `model_scripts/weights/best_model_lstm_frozen.pt`
  - 能力：冻结编码器权重
  - 用途：冻结编码器迁移学习检查点
  - 复用状态：blocked；类型：model_weight
- `cache/models3 copy/lstm.onnx`
  - 能力：导出推理图
  - 用途：LSTM 的 ONNX 推理导出
  - 复用状态：blocked；类型：model_weight

### datasets

- `model_scripts/database_check/DBAASP_peptides.csv`
  - 能力：训练语料/数据库检查语料
  - 用途：肽序列语料的数据库检查与整理
  - 复用状态：unknown；类型：unknown
- `model_scripts/database_check/dramps_general_amps.txt`
  - 能力：训练语料/数据库检查语料
  - 用途：肽序列语料的数据库检查与整理
  - 复用状态：unknown；类型：unknown
- `cache/models/background_aa.fa`
  - 能力：背景序列参考
  - 用途：作为氨基酸背景参考或对照序列集
  - 复用状态：blocked；类型：unknown
- `generated/amp-scanner-v2_results/1746183770602_AMPCandidates.fa`
  - 能力：候选序列结果集
  - 用途：生成后候选肽序列输出
  - 复用状态：blocked；类型：unknown

### evaluation

- `model_scripts/seq_eval.ipynb`
  - 能力：序列级评估
  - 用途：做序列相似性/多样性/质量相关评估
  - 复用状态：blocked；类型：unknown
- `cache/models/csm_toxicity_results.csv`
  - 能力：毒性筛除评估
  - 用途：记录 CSM 相关毒性过滤结果
  - 复用状态：blocked；类型：unknown
- `cache/models1/blast_summary.csv`
  - 能力：同源/相似性检查
  - 用途：汇总 BLAST 检查结果
  - 复用状态：blocked；类型：unknown
- `model_scripts/temperature_similarity_diversity.csv`
  - 能力：温度/相似性/多样性分析
  - 用途：分析不同采样温度下的相似性与多样性
  - 复用状态：blocked；类型：unknown

### inference

- `model_implementation/tb_AMP_generation.py`
  - 能力：候选肽生成
  - 用途：从已训练生成器采样候选序列
  - 复用状态：blocked；类型：code_entry
- `model_implementation/tb_AMP_classification.py`
  - 能力：候选序列分类/筛选
  - 用途：对候选序列做分类或过滤
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `model_implementation/tb_AMP_generation.py`
  - 能力：生成模型实现
  - 用途：生成候选抗菌肽序列
  - 复用状态：blocked；类型：code_entry
- `model_implementation/tb_AMP_classification.py`
  - 能力：分类/筛选实现
  - 用途：对候选序列做活性/筛选相关推断
  - 复用状态：blocked；类型：code_entry
- `model_scripts/data_gen.ipynb`
  - 能力：数据构建与预处理
  - 用途：构建训练/推断所需序列数据
  - 复用状态：blocked；类型：unknown

### training

- `model_implementation/lstm_transfer.ipynb`
  - 能力：transfer learning 训练
  - 用途：训练转移学习版 LSTM / BiLSTM 模型
  - 复用状态：blocked；类型：unknown
- `model_implementation/gen-vanilla-lstm.ipynb`
  - 能力：生成模型训练
  - 用途：训练生成式 LSTM
  - 复用状态：blocked；类型：unknown
- `model_scripts/lstm_no_transfer.ipynb`
  - 能力：无迁移基线训练
  - 用途：训练非迁移学习基线模型
  - 复用状态：blocked；类型：unknown
- `model_scripts/lstm_transfer.ipynb`
  - 能力：迁移学习训练
  - 用途：训练迁移学习版本序列模型
  - 复用状态：blocked；类型：unknown

## 使用限制

- 仅基于冻结清单做静态审查，未运行任何 notebook、脚本或模型。
- 未安装依赖，无法验证训练、推理、评估与导出流程。
- 仓库中虽有大量 TensorBoard 日志、checkpoint 和生成结果，但静态存在不等于真实执行。
- 未发现可确认的许可证文件，直接复用受到明显限制。

## 仍未知

- 训练/验证/测试划分、数据来源授权与清洗规则不明。
- 各 `.pt`/`.onnx` 检查点对应的最佳指标、超参数和数据集版本不明。
- `generated/` 与 `cache/` 中的候选序列是否全部由当前冻结提交生成，不可仅凭路径确认。
- README.md 的具体说明内容未能通过静态清单进一步核实。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
