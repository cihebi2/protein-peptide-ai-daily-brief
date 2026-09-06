# yangling0818/binddm

- **仓库：** [https://github.com/yangling0818/binddm](https://github.com/yangling0818/binddm)
- **固定 commit：** `bd0d53f9ba07ab45886036b987bf14ac21146a5a`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 36

## 仓库摘要

BindDM 主仓库覆盖数据清洗、扩散模型训练、口袋条件采样和多类评估；冻结快照未见 LICENSE、checkpoint 或 bundled data，且仅作静态审计。

## 可复用模块与资源

### datasets

- `datasets/pl_data.py`
  - 能力：Protein-ligand 数据加载
  - 用途：artifact_kind=code_entry；组织和读取 PL 样本。
  - 复用状态：blocked；类型：code_entry
- `datasets/pl_pair_dataset.py`
  - 能力：配对样本 Dataset
  - 用途：artifact_kind=code_entry；构造蛋白-配体配对数据接口。
  - 复用状态：blocked；类型：code_entry
- `utils/data.py`
  - 能力：数据工具
  - 用途：artifact_kind=code_entry；batch 组织、采样与数据预处理辅助。
  - 复用状态：blocked；类型：code_entry
- `scripts/data_preparation/clean_crossdocked.py`
  - 能力：CrossDocked 清洗
  - 用途：artifact_kind=code_entry；清洗原始 CrossDocked 结构数据。
  - 复用状态：blocked；类型：code_entry
- `scripts/data_preparation/extract_pockets.py`
  - 能力：口袋提取
  - 用途：artifact_kind=code_entry；从复合物中提取 protein pocket。
  - 复用状态：blocked；类型：code_entry
- `scripts/data_preparation/split_pl_dataset.py`
  - 能力：数据切分
  - 用途：artifact_kind=code_entry；生成训练/验证/测试划分。
  - 复用状态：blocked；类型：code_entry

### evaluation

- `evaluate.py`
  - 能力：主评估入口
  - 用途：artifact_kind=code_entry；统一评估调度。
  - 复用状态：blocked；类型：code_entry
- `scripts/evaluate_diffusion.py`
  - 能力：扩散输出评估
  - 用途：artifact_kind=code_entry；对 diffusion 生成结果做评估。
  - 复用状态：blocked；类型：code_entry
- `scripts/evaluate_from_meta.py`
  - 能力：元数据驱动评估
  - 用途：artifact_kind=code_entry；从 meta 信息批量运行评估。
  - 复用状态：blocked；类型：code_entry
- `scripts/likelihood_est_diffusion.py`
  - 能力：likelihood 估计
  - 用途：artifact_kind=code_entry；扩散模型 likelihood 估计与辅助评估。
  - 复用状态：blocked；类型：code_entry
- `utils/evaluation/analyze.py`
  - 能力：结果分析
  - 用途：artifact_kind=code_entry；统计与分析评估输出。
  - 复用状态：blocked；类型：code_entry
- `utils/evaluation/atom_num.py`
  - 能力：原子数统计
  - 用途：artifact_kind=code_entry；计算原子数分布/约束。
  - 复用状态：blocked；类型：code_entry
- `utils/evaluation/atom_num_config.py`
  - 能力：原子数配置
  - 用途：artifact_kind=code_entry；原子数评估参数配置。
  - 复用状态：blocked；类型：config
- `utils/evaluation/docking_qvina.py`
  - 能力：docking 评估 - qvina
  - 用途：artifact_kind=code_entry；调用 qvina 进行 docking 评估。
  - 复用状态：blocked；类型：code_entry
- `utils/evaluation/docking_vina.py`
  - 能力：docking 评估 - vina
  - 用途：artifact_kind=code_entry；调用 vina 进行 docking 评估。
  - 复用状态：blocked；类型：code_entry
- `utils/evaluation/eval_atom_type.py`
  - 能力：原子类型评估
  - 用途：artifact_kind=code_entry；评估生成分子的原子类型质量。
  - 复用状态：blocked；类型：code_entry
- `utils/evaluation/eval_bond_length.py`
  - 能力：键长评估
  - 用途：artifact_kind=code_entry；评估键长分布。
  - 复用状态：blocked；类型：code_entry
- `utils/evaluation/eval_bond_length_config.py`
  - 能力：键长配置
  - 用途：artifact_kind=code_entry；键长评估参数配置。
  - 复用状态：blocked；类型：config
- `utils/evaluation/sascorer.py`
  - 能力：SA score 计算
  - 用途：artifact_kind=code_entry；计算合成可及性（SA score）。
  - 复用状态：unknown；类型：code_entry
- `utils/evaluation/scoring_func.py`
  - 能力：综合打分函数
  - 用途：artifact_kind=code_entry；汇总多项分子质量指标。
  - 复用状态：blocked；类型：code_entry
- `utils/evaluation/similarity.py`
  - 能力：相似性计算
  - 用途：artifact_kind=code_entry；计算生成分子与参考分子的相似性。
  - 复用状态：blocked；类型：code_entry

### inference

- `sample.py`
  - 能力：采样入口
  - 用途：artifact_kind=code_entry；主采样/生成入口。
  - 复用状态：blocked；类型：code_entry
- `scripts/sample_diffusion.py`
  - 能力：扩散采样脚本
  - 用途：artifact_kind=code_entry；执行 diffusion 生成。
  - 复用状态：blocked；类型：code_entry
- `scripts/sample_for_pocket.py`
  - 能力：口袋条件采样
  - 用途：artifact_kind=code_entry；按 protein pocket 进行条件生成。
  - 复用状态：blocked；类型：code_entry
- `configs/sampling.yml`
  - 能力：采样配置
  - 用途：artifact_kind=config；采样超参与输出设置。
  - 复用状态：blocked；类型：config

### reusable_assets

- `models/egnn.py`
  - 能力：模型架构 - EGNN
  - 用途：artifact_kind=code_entry；蛋白-配体图上的等变消息传递与几何更新核心模块。
  - 复用状态：blocked；类型：code_entry
- `models/uni_transformer.py`
  - 能力：模型架构 - UniTransformer
  - 用途：artifact_kind=code_entry；用于上下文编码/条件表征的 Transformer 组件。
  - 复用状态：blocked；类型：code_entry
- `models/molopt_score_model.py`
  - 能力：模型架构 - score model
  - 用途：artifact_kind=code_entry；扩散生成/优化中的打分与条件建模主干。
  - 复用状态：blocked；类型：code_entry
- `models/common.py`
  - 能力：通用模型组件
  - 用途：artifact_kind=code_entry；共享层、embedding、MLP 等基础组件。
  - 复用状态：blocked；类型：code_entry
- `utils/transforms.py`
  - 能力：几何变换与重建工具
  - 用途：artifact_kind=code_entry；坐标/特征变换与分子构象处理辅助。
  - 复用状态：blocked；类型：code_entry
- `utils/reconstruct.py`
  - 能力：分子重建工具
  - 用途：artifact_kind=code_entry；从生成表示恢复分子结构。
  - 复用状态：blocked；类型：code_entry
- `utils/evaluation/fpscores.pkl.gz`
  - 能力：SA score 查表资源
  - 用途：artifact_kind=unknown；供 `sascorer.py` 计算 SA score 的参考查表数据。
  - 复用状态：unknown；类型：unknown

### training

- `train.py`
  - 能力：训练入口
  - 用途：artifact_kind=code_entry；主训练调度入口。
  - 复用状态：blocked；类型：code_entry
- `scripts/train_diffusion.py`
  - 能力：扩散训练脚本
  - 用途：artifact_kind=code_entry；训练 diffusion 模型。
  - 复用状态：blocked；类型：code_entry
- `utils/train.py`
  - 能力：训练辅助模块
  - 用途：artifact_kind=code_entry；训练循环、优化器、日志与调度辅助。
  - 复用状态：blocked；类型：code_entry
- `configs/training.yml`
  - 能力：训练配置
  - 用途：artifact_kind=config；训练超参、路径和实验设置。
  - 复用状态：blocked；类型：config

## 使用限制

- 仅做静态审计，未执行仓库代码、测试或训练/采样流程。
- 依赖未安装、submodule 未初始化，外部工具（如 docking）可用性未验证。
- 未发现 tracked checkpoint/weight 文件，也未见 bundled data，无法验证复现产物。
- 仓库未找到 LICENSE，第三方辅助资源与数据来源许可未核验。

## 仍未知

- `utils/evaluation/fpscores.pkl.gz` 的来源与许可未能从冻结快照确认。
- 训练与采样的默认超参是否与论文设置一致，静态审计无法证明。
- 外部数据集（如 CrossDocked 相关来源）的具体版本、下载地址与许可未核验。
- 是否存在未跟踪的权重、缓存或 release artifact，当前快照无法判断。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
