# charlesxu90/helm-gpt

- **仓库：** [https://github.com/charlesxu90/helm-gpt](https://github.com/charlesxu90/helm-gpt)
- **固定 commit：** `a145be297a86af6bd9d653a58637a0b42763874e`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 35

## 仓库摘要

这是一个面向 HELM/macrocyclic peptide de novo design 的静态代码仓库审查。代码侧有 MIT 许可证，但 bundled 数据、结果文件和 checkpoint 的来源与许可边界未被静态证明；可复用性主要集中在模型、采样、训练、评估与 scoring 管线。

## 可复用模块与资源

### checkpoints

- `data/perm_prior/gpt_model_final_0.105.pt`
  - 能力：prior checkpoint
  - 用途：主 prior 模型权重
  - 复用状态：partial；类型：model_weight
- `data/cpp/regression_rf.pkl`
  - 能力：CPP regression model
  - 用途：CPP 回归基线/预测器快照
  - 复用状态：partial；类型：unknown
- `data/cpp/pred_cpp_perm.pkl`
  - 能力：CPP permeability predictor
  - 用途：CPP 渗透性预测器快照
  - 复用状态：partial；类型：unknown
- `data/kras_kd/kras_xgboost_reg.pkl`
  - 能力：KRAS regression model
  - 用途：KRAS KD 回归模型快照
  - 复用状态：partial；类型：unknown
- `result/agent/cpp/cpp_agent_permeability.pkl`
  - 能力：CPP agent snapshot
  - 用途：CPP agent 的序列优化结果/快照
  - 复用状态：partial；类型：unknown
- `result/agent/kras_kd/kras_kd_agent.pkl`
  - 能力：KRAS agent snapshot
  - 用途：KRAS agent 的序列优化结果/快照
  - 复用状态：partial；类型：unknown

### datasets

- `data/prior/CycPeptMPDB/CycPeptMPDB_Peptide_All.csv`
  - 能力：macrocyclic peptide corpus
  - 用途：prior 训练语料的一部分
  - 复用状态：partial；类型：unknown
- `data/prior/CycPeptMPDB/CycPeptMPDB_Monomer_All.csv`
  - 能力：monomer corpus
  - 用途：prior 训练中的单体词表/语料来源
  - 复用状态：partial；类型：unknown
- `data/prior/chembl32/biotherapeutics_dict_prot.csv`
  - 能力：protein dictionary
  - 用途：基于 ChEMBL32 的蛋白/生物治疗分子字典
  - 复用状态：partial；类型：unknown
- `data/prior/chembl32/biotherapeutics_dict_prot_flt.csv`
  - 能力：filtered protein dictionary
  - 用途：过滤后的 ChEMBL32 蛋白字典
  - 复用状态：partial；类型：unknown
- `data/prior/monomer_library.csv`
  - 能力：monomer library
  - 用途：仓库内单体库/构件表
  - 复用状态：partial；类型：unknown
- `data/prior/prior_data.csv`
  - 能力：combined prior corpus
  - 用途：prior 阶段汇总训练集
  - 复用状态：partial；类型：unknown
- `data/cpp/all.csv.gz`
  - 能力：CPP dataset
  - 用途：CPP 相关主数据集/表格语料
  - 复用状态：partial；类型：unknown
- `data/cpp/X_dps.npy`
  - 能力：CPP feature matrix
  - 用途：CPP 模型输入特征矩阵
  - 复用状态：partial；类型：unknown
- `data/cpp/X_fps.npy`
  - 能力：CPP feature matrix
  - 用途：CPP 模型输入特征矩阵
  - 复用状态：partial；类型：unknown

### evaluation

- `utils/metrics_utils.py`
  - 能力：metric computation
  - 用途：评价指标计算与汇总
  - 复用状态：ready_for_review；类型：code_entry
- `1.eval_cpp_pred.ipynb`
  - 能力：CPP evaluation notebook
  - 用途：CPP 预测/基线评估分析
  - 复用状态：partial；类型：unknown
- `1.cpp_baselines.ipynb`
  - 能力：CPP baseline notebook
  - 用途：CPP 基线比较与分析
  - 复用状态：partial；类型：unknown
- `2.kras_pred_model.ipynb`
  - 能力：KRAS evaluation notebook
  - 用途：KRAS 预测模型分析
  - 复用状态：partial；类型：unknown
- `3.cpl_loss_effect.ipynb`
  - 能力：ablation notebook
  - 用途：损失项/训练效果分析
  - 复用状态：partial；类型：unknown

### inference

- `generate.py`
  - 能力：generation CLI
  - 用途：候选序列/分子生成入口
  - 复用状态：ready_for_review；类型：code_entry
- `model/sampler.py`
  - 能力：sampling helper
  - 用途：推理时采样与候选展开
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `model/model.py`
  - 能力：model architecture
  - 用途：核心 GPT 生成模型定义
  - 复用状态：ready_for_review；类型：code_entry
- `model/sampler.py`
  - 能力：sampling/generation
  - 用途：从模型中采样候选序列/HELM 表示
  - 复用状态：ready_for_review；类型：code_entry
- `utils/dataset.py`
  - 能力：data loading/preprocessing
  - 用途：训练数据读取、切分与批处理
  - 复用状态：ready_for_review；类型：code_entry
- `utils/helm_utils.py`
  - 能力：HELM utilities
  - 用途：HELM 字符串与结构表示辅助
  - 复用状态：ready_for_review；类型：code_entry
- `utils/bpe.py`
  - 能力：tokenization/BPE utilities
  - 用途：序列分词与编码辅助
  - 复用状态：ready_for_review；类型：code_entry
- `agent/scoring_functions.py`
  - 能力：reward/scoring composition
  - 用途：把多个性质打分组合成 agent 奖励
  - 复用状态：ready_for_review；类型：code_entry
- `agent/scoring/permeability.py`
  - 能力：permeability scoring
  - 用途：CPP permeability 相关打分/约束
  - 复用状态：ready_for_review；类型：code_entry
- `agent/scoring/kras.py`
  - 能力：target-specific scoring
  - 用途：KRAS 相关打分
  - 复用状态：ready_for_review；类型：code_entry
- `data/perm_prior/gpt_model_final_0.105.json`
  - 能力：training config
  - 用途：与 prior checkpoint 配套的超参数/模型配置
  - 复用状态：ready_for_review；类型：config

### training

- `train_prior.py`
  - 能力：prior training entrypoint
  - 用途：启动 prior 预训练
  - 复用状态：ready_for_review；类型：code_entry
- `prior/trainer.py`
  - 能力：prior trainer helper
  - 用途：prior 训练循环与优化逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `train_agent.py`
  - 能力：agent training entrypoint
  - 用途：启动 agent 微调/优化训练
  - 复用状态：ready_for_review；类型：code_entry
- `agent/agent_trainer.py`
  - 能力：agent trainer helper
  - 用途：agent 训练辅助逻辑
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态审查，未运行任何代码、训练、推理或评估。
- 依赖未安装，测试未执行，不能证明仓库可复现。
- 结果目录中的 CSV/pkl 只是静态存在，不能证明其与论文图表或指标一致。
- 外部数据集与序列化模型的原始授权、派生关系和可再分发边界未被完全证明。

## 仍未知

- `data/prior/monomer_library.csv` 和 `data/prior/prior_data.csv` 的精确来源与许可未在静态 inventory 中明确。
- `data/perm_prior/gpt_model_final_0.105.pt` 是否为论文主实验最终权重、还是中间 checkpoint，静态证据不足。
- `utils/sascore/` 是否为 vendored 第三方实现及其许可边界未明确。
- 多个 `result/*` 产物是最终报告、实验缓存还是中间输出，无法仅凭路径区分。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
