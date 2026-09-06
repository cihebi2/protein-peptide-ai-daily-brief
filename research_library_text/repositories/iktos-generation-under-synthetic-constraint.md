# iktos/generation-under-synthetic-constraint

- **仓库：** [https://github.com/iktos/generation-under-synthetic-constraint](https://github.com/iktos/generation-under-synthetic-constraint)
- **固定 commit：** `86e298cd2f1437f86c310f91e168118e6e6de470`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 40

## 仓库摘要

该仓库是一个以 GuacaMol 基准、SMILES/graph 生成器和多种 synthetic scorer 为核心的分子设计代码库；静态清点到训练、推断、评测与若干预训练权重，但未运行任何代码，第三方数据/模型许可仍需逐项核实。

## 可复用模块与资源

### checkpoints

- `guacamol_baselines/smiles_lstm_hc/pretrained_model/model_final_chembl.pt`
  - 能力：SMILES LSTM Chembl 预训练权重
  - 用途：用于 hard-constraint 生成器初始化/推断。
  - 复用状态：partial；类型：model_weight
- `guacamol_baselines/smiles_lstm_hc/pretrained_model/model_final_pi3kmtor.pt`
  - 能力：SMILES LSTM PI3K/mTOR 预训练权重
  - 用途：用于 PI3K/mTOR 任务的生成模型初始化/推断。
  - 复用状态：partial；类型：model_weight
- `guacamol_baselines/smiles_lstm_hc/pretrained_model/model_final_chembl.json`
  - 能力：SMILES LSTM Chembl 配置快照
  - 用途：保存模型结构/超参数配置。
  - 复用状态：partial；类型：config
- `guacamol_baselines/smiles_lstm_hc/pretrained_model/model_final_pi3kmtor.json`
  - 能力：SMILES LSTM PI3K/mTOR 配置快照
  - 用途：保存 PI3K/mTOR 任务模型配置。
  - 复用状态：partial；类型：config
- `pi3kmtor/weights_pi3k.json`
  - 能力：PI3K 权重表
  - 用途：为 PI3K 打分/生成提供权重参数。
  - 复用状态：partial；类型：config
- `pi3kmtor/weights_mtor.json`
  - 能力：mTOR 权重表
  - 用途：为 mTOR 打分/生成提供权重参数。
  - 复用状态：partial；类型：config
- `synthetic_scorers/RAscore/models/DNN_chembl_fcfp_counts/model.h5`
  - 能力：RAscore 神经网络权重
  - 用途：推断合成可及性分数。
  - 复用状态：partial；类型：model_weight
- `synthetic_scorers/RSPred/models/chembl_230K_final_87.0.pickle`
  - 能力：RSPred 二进制权重
  - 用途：推断 RSPred 性质/可合成性分数。
  - 复用状态：partial；类型：unknown
- `synthetic_scorers/RSPred/predictor_continuous_chembl_0.pickle`
  - 能力：RSPred 连续预测器权重
  - 用途：连续性质预测。
  - 复用状态：partial；类型：unknown
- `synthetic_scorers/scscore/models/full_reaxys_model_1024bool/model.ckpt-10654.as_numpy.pickle`
  - 能力：SCScore 模型参数
  - 用途：推断合成复杂度/可行性。
  - 复用状态：partial；类型：checkpoint_adjacent
- `synthetic_scorers/scscore/models/full_reaxys_model_1024bool/model.ckpt-10654.as_numpy.json.gz`
  - 能力：SCScore 参数快照
  - 用途：与 SCScore 模型参数配套的序列化快照。
  - 复用状态：partial；类型：checkpoint_adjacent
- `synthetic_scorers/sascore/fpscores.pkl.gz`
  - 能力：SA score 指纹表
  - 用途：支撑 SA score 计算的指纹/权重表。
  - 复用状态：partial；类型：unknown

### datasets

- `data/guacamol_v1_train.smiles`
  - 能力：GuacaMol 训练集拆分
  - 用途：SMILES 训练分割，用于分布学习/生成器预训练。
  - 复用状态：partial；类型：unknown
- `data/guacamol_v1_valid.smiles`
  - 能力：GuacaMol 验证集拆分
  - 用途：模型验证与超参选择。
  - 复用状态：partial；类型：unknown
- `data/guacamol_v1_test.smiles`
  - 能力：GuacaMol 测试集拆分
  - 用途：生成质量或分布匹配的保留评测拆分。
  - 复用状态：partial；类型：unknown
- `data/guacamol_v1_all.smiles`
  - 能力：GuacaMol 汇总拆分
  - 用途：全量分子集合，通常用于索引、汇总或辅助分析。
  - 复用状态：partial；类型：unknown
- `pi3kmtor/pi3kmtor.smiles`
  - 能力：PI3K/mTOR 任务分子集
  - 用途：任务特定分子集合，用于 PI3K/mTOR 相关生成/筛选。
  - 复用状态：partial；类型：unknown
- `pi3kmtor/all_pi3k.csv`
  - 能力：PI3K/mTOR 汇总 CSV
  - 用途：PI3K/mTOR 数据汇总与分析。
  - 复用状态：partial；类型：unknown

### evaluation

- `guacamol/guacamol/assess_goal_directed_generation.py`
  - 能力：goal-directed 评测套件
  - 用途：评估目标导向生成任务的得分与排名。
  - 复用状态：ready_for_review；类型：code_entry
- `guacamol/guacamol/assess_distribution_learning.py`
  - 能力：distribution-learning 评测套件
  - 用途：评估生成分布与训练分布的一致性。
  - 复用状态：ready_for_review；类型：code_entry
- `guacamol/guacamol/benchmark_suites_original.py`
  - 能力：benchmark suite definition for evaluation
  - 用途：提供原始 benchmark 套件定义，作为对照评测。
  - 复用状态：ready_for_review；类型：code_entry
- `exploit_results/add_scores_to_db.py`
  - 能力：结果后处理/打分汇总
  - 用途：把生成结果与分数汇总到分析产物中。
  - 复用状态：partial；类型：code_entry

### inference

- `guacamol_baselines/smiles_lstm_hc/goal_directed_generation.py`
  - 能力：SMILES LSTM hard-constraint 生成
  - 用途：从已训模型生成候选分子并执行目标导向搜索。
  - 复用状态：ready_for_review；类型：code_entry
- `guacamol_baselines/smiles_lstm_ppo/goal_directed_generation.py`
  - 能力：PPO 生成器
  - 用途：用 PPO 策略执行目标分子生成。
  - 复用状态：ready_for_review；类型：code_entry
- `guacamol_baselines/random_smiles_sampler/generator.py`
  - 能力：随机 SMILES 采样器
  - 用途：构造随机采样生成基线。
  - 复用状态：ready_for_review；类型：code_entry
- `guacamol_baselines/best_from_chembl/goal_directed_generation.py`
  - 能力：ChEMBL 选择性/最优基线
  - 用途：从 ChEMBL 候选中筛选高分分子。
  - 复用状态：ready_for_review；类型：code_entry
- `synthetic_scorers/RSPred/predictorRS.py`
  - 能力：RSPred 推断器
  - 用途：对分子执行 RSPred 风格的性质/可达性预测。
  - 复用状态：ready_for_review；类型：code_entry
- `synthetic_scorers/sascore/sascorer.py`
  - 能力：SA score 推断器
  - 用途：计算 synthetic accessibility 分数。
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `guacamol/guacamol/benchmark_suites.py`
  - 能力：benchmark 套件与任务编排
  - 用途：定义 goal-directed / distribution-learning benchmark 集合与评测入口。
  - 复用状态：ready_for_review；类型：code_entry
- `guacamol/guacamol/common_scoring_functions_iktos.py`
  - 能力：Iktos 自定义 scoring/benchmark 扩展
  - 用途：提供项目特定的打分函数与约束变体。
  - 复用状态：ready_for_review；类型：code_entry
- `guacamol_baselines/smiles_lstm_hc/rnn_model.py`
  - 能力：SMILES LSTM hard-constraint 生成器
  - 用途：定义 SMILES 序列生成模型结构，服务于 hard-constraint 基线。
  - 复用状态：ready_for_review；类型：code_entry
- `guacamol_baselines/smiles_lstm_ppo/ppo_trainer.py`
  - 能力：PPO directed generation
  - 用途：用 PPO 优化生成策略以提升目标分子得分。
  - 复用状态：ready_for_review；类型：code_entry
- `guacamol_baselines/graph_ga/goal_directed_generation.py`
  - 能力：graph GA / MCTS 生成基线
  - 用途：基于图搜索的候选分子生成与局部变异/交叉。
  - 复用状态：ready_for_review；类型：code_entry
- `synthetic_scorers/RAscore/RAscore_NN.py`
  - 能力：synthetic scorer 运行时封装
  - 用途：在推断阶段调用 synthetic accessibility / retrosynthesis / property scorer。
  - 复用状态：ready_for_review；类型：code_entry

### training

- `guacamol_baselines/smiles_lstm_hc/train_smiles_lstm_model.py`
  - 能力：SMILES LSTM 训练入口
  - 用途：训练 hard-constraint SMILES LSTM 模型。
  - 复用状态：ready_for_review；类型：code_entry
- `guacamol_baselines/smiles_lstm_hc/rnn_trainer.py`
  - 能力：SMILES LSTM 训练/采样支撑
  - 用途：封装 RNN 训练循环、参数更新和采样协同逻辑。
  - 复用状态：ready_for_review；类型：code_entry
- `guacamol_baselines/smiles_lstm_ppo/ppo_trainer.py`
  - 能力：PPO 训练器
  - 用途：训练策略网络以执行目标导向分子优化。
  - 复用状态：ready_for_review；类型：code_entry
- `guacamol_baselines/moses_baselines/aae_train.py`
  - 能力：MOSES AAE 训练脚本
  - 用途：训练 AAE 分布学习基线。
  - 复用状态：ready_for_review；类型：code_entry
- `guacamol_baselines/moses_baselines/organ_train.py`
  - 能力：MOSES ORGAN 训练脚本
  - 用途：训练 ORGAN 分布学习基线。
  - 复用状态：ready_for_review；类型：code_entry
- `guacamol_baselines/moses_baselines/vae_train.py`
  - 能力：MOSES VAE 训练脚本
  - 用途：训练 VAE 分布学习基线。
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态清点，未运行训练、推断、评测或下载器。
- 依赖未安装，无法验证脚本可执行性或权重可加载性。
- 仓库中部分大文件可能是 promisor-only/未完全物化。
- Notebook 与 `exploit_results/results_data/*` 仅能证明存在，不能证明该 commit 的实验已复现。
- 顶层 MIT 许可不自动覆盖所有数据/模型工件。

## 仍未知

- `data/guacamol_v1_*` 与 `pi3kmtor/*` 的上游来源和具体许可未从冻结清单中确认。
- `synthetic_scorers/*` 中多个权重文件的原始训练数据、衍生关系与许可边界未确认。
- `guacamol/` 与 `guacamol_baselines/` 中哪些文件为上游 vendored 内容、哪些为本仓库修改，静态库存无法完全区分。
- `exploit_results/` 下的 CSV/JSON/PNG 是否对应本 commit 的真实运行结果，静态分析无法验证。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
