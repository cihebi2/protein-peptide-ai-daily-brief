# alberdom88/ALCHIMIA

- **仓库：** [https://github.com/alberdom88/ALCHIMIA](https://github.com/alberdom88/ALCHIMIA)
- **固定 commit：** `2e4ff4aa35c3913fb4bce41f03df84caa46b80a0`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 32

## 仓库摘要

这是论文对应的分子优化仓库：含RL-guided GA主流程、变异算子、SA打分/收敛监控、GLIDE/LigPrep脚本、训练入口、CSV资源与12个checkpoint；仅做静态盘点，未发现LICENSE，且未验证可运行性。

## 可复用模块与资源

### checkpoints

- `genetic/models/policy_final_1.pt`
  - 能力：policy_checkpoint
  - 用途：策略网络权重，用于后续搜索或推理
  - 复用状态：blocked；类型：model_weight
- `genetic/models/policy_final_2.pt`
  - 能力：policy_checkpoint
  - 用途：策略网络权重，用于后续搜索或推理
  - 复用状态：blocked；类型：model_weight
- `genetic/models/policy_final_3.pt`
  - 能力：policy_checkpoint
  - 用途：策略网络权重，用于后续搜索或推理
  - 复用状态：blocked；类型：model_weight
- `models/policy_m1.pt`
  - 能力：policy_checkpoint
  - 用途：策略网络权重，用于后续搜索或推理
  - 复用状态：blocked；类型：model_weight
- `models/policy_m2.pt`
  - 能力：policy_checkpoint
  - 用途：策略网络权重，用于后续搜索或推理
  - 复用状态：blocked；类型：model_weight
- `models/policy_m3.pt`
  - 能力：policy_checkpoint
  - 用途：策略网络权重，用于后续搜索或推理
  - 复用状态：blocked；类型：model_weight
- `models/policy_m4.pt`
  - 能力：policy_checkpoint
  - 用途：策略网络权重，用于后续搜索或推理
  - 复用状态：blocked；类型：model_weight
- `models/policy_m5.pt`
  - 能力：policy_checkpoint
  - 用途：策略网络权重，用于后续搜索或推理
  - 复用状态：blocked；类型：model_weight
- `models/policy_m6.pt`
  - 能力：policy_checkpoint
  - 用途：策略网络权重，用于后续搜索或推理
  - 复用状态：blocked；类型：model_weight
- `models/policy_m7.pt`
  - 能力：policy_checkpoint
  - 用途：策略网络权重，用于后续搜索或推理
  - 复用状态：blocked；类型：model_weight
- `models/policy_m8.pt`
  - 能力：policy_checkpoint
  - 用途：策略网络权重，用于后续搜索或推理
  - 复用状态：blocked；类型：model_weight
- `models/policy_m9.pt`
  - 能力：policy_checkpoint
  - 用途：策略网络权重，用于后续搜索或推理
  - 复用状态：blocked；类型：model_weight

### datasets

- `brics_10_top01.csv`
  - 能力：molecule_sets
  - 用途：BRICS片段/候选变换资源
  - 复用状态：unknown；类型：unknown
- `genetic/brics_10_top01.csv`
  - 能力：molecule_sets
  - 用途：BRICS片段/候选变换资源的复制件
  - 复用状态：unknown；类型：unknown
- `start.csv`
  - 能力：molecule_sets
  - 用途：起始分子集合
  - 复用状态：unknown；类型：unknown
- `train.csv`
  - 能力：molecule_sets
  - 用途：训练/示例分子集合
  - 复用状态：unknown；类型：unknown
- `genetic/best_so_far`
  - 能力：run_state_artifacts
  - 用途：遗传搜索过程中保留的历史最优结果记录
  - 复用状态：unknown；类型：unknown
- `genetic/done_so_far`
  - 能力：run_state_artifacts
  - 用途：遗传搜索过程中已处理条目的状态记录
  - 复用状态：unknown；类型：unknown
- `fpscores.pkl.gz`
  - 能力：score_lookup
  - 用途：SA score 查表数据
  - 复用状态：blocked；类型：unknown
- `genetic/fpscores.pkl.gz`
  - 能力：score_lookup
  - 用途：SA score 查表数据的复制件
  - 复用状态：blocked；类型：unknown

### evaluation

- `sascorer.py`
  - 能力：sa_scoring
  - 用途：Synthetic Accessibility 评分实现
  - 复用状态：blocked；类型：code_entry
- `genetic/sascorer.py`
  - 能力：sa_scoring
  - 用途：Synthetic Accessibility 评分实现的复制件
  - 复用状态：blocked；类型：code_entry
- `genetic/convergence.py`
  - 能力：monitoring
  - 用途：收敛曲线/训练过程监控
  - 复用状态：blocked；类型：code_entry

### inference

- `genetic/genetic.py`
  - 能力：search_and_screening
  - 用途：遗传搜索/候选分子生成与筛选主流程
  - 复用状态：blocked；类型：code_entry
- `genetic/glide.in`
  - 能力：search_and_screening
  - 用途：GLIDE docking 输入模板
  - 复用状态：blocked；类型：unknown
- `genetic/glide.sh`
  - 能力：search_and_screening
  - 用途：调用外部 GLIDE 流程的 shell 包装
  - 复用状态：blocked；类型：code_entry
- `genetic/ligprep.inp`
  - 能力：search_and_screening
  - 用途：LigPrep 输入模板
  - 复用状态：blocked；类型：unknown
- `genetic/ligprep.sh`
  - 能力：search_and_screening
  - 用途：调用外部 LigPrep 流程的 shell 包装
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `mut_all.py`
  - 能力：mutation_operators
  - 用途：分子变异/结构变换算子库，可被搜索流程复用
  - 复用状态：blocked；类型：code_entry
- `genetic/mut_all.py`
  - 能力：mutation_operators
  - 用途：分子变异/结构变换算子库的另一份复制件
  - 复用状态：blocked；类型：code_entry

### training

- `train.py`
  - 能力：training_entrypoint
  - 用途：RL-guided GA 策略训练入口
  - 复用状态：blocked；类型：code_entry
- `genetic/train.py`
  - 能力：training_entrypoint
  - 用途：RL-guided GA 策略训练入口的复制件
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态审查，未执行代码、测试或训练/推理流程
- 依赖未安装，无法验证脚本链路、外部 docking 工具或 checkpoint 可用性
- 未发现 LICENSE，直接复用前需补充授权确认
- 部分数据/权重的来源与生成过程仅能从文件名推断，未能独立验证

## 仍未知

- README 内容未在本次输出中展开，模块职责主要依据文件名与路径推断
- `brics_10_top01.csv`、`start.csv`、`train.csv` 的生成来源与授权未确认
- `genetic/best_so_far` 与 `genetic/done_so_far` 的精确定义未确认
- `sascorer.py`/`fpscores.pkl.gz` 是否为第三方捆绑件及其原始许可未确认
- 这些 checkpoint 是否为本仓库训练所得，或只是导入的预训练权重，均未验证

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
