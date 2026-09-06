# marieoestreich/drugdiff

- **仓库：** [https://github.com/marieoestreich/drugdiff](https://github.com/marieoestreich/drugdiff)
- **固定 commit：** `195c1a142cb72088d80b3b8539a9dd23e126451e`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 17

## 仓库摘要

DrugDiff 仓库是面向小分子生成的 diffusion 实现，含无/单/多属性 guidance 生成、target affinity predictor 训练和评估；静态清单未见 LICENSE 与 checkpoint。

## 可复用模块与资源

### datasets

- `data/guacamol/guacamol_v1_train_filt.smiles`
  - 能力：Guacamol smiles 语料
  - 用途：生成模型训练/基准语料的一部分
  - 复用状态：blocked；类型：unknown
- `data/zinc250k/zinc250k_smiles.txt`
  - 能力：ZINC250k smiles 语料
  - 用途：生成模型训练/基准语料的一部分
  - 复用状态：blocked；类型：unknown

### evaluation

- `notebooks/evaluation_without_guidance.ipynb`
  - 能力：无 guidance 评估
  - 用途：复现实验或统计无 guidance 生成结果
  - 复用状态：blocked；类型：unknown
- `notebooks/evaluation_with_single_property_guidance.ipynb`
  - 能力：单属性 guidance 评估
  - 用途：复现实验或统计单属性 guidance 生成结果
  - 复用状态：blocked；类型：unknown
- `notebooks/evaluation_with_multi_property_guidance.ipynb`
  - 能力：多属性 guidance 评估
  - 用途：复现实验或统计多属性 guidance 生成结果
  - 复用状态：blocked；类型：unknown
- `notebooks/eval_predictor_target_affinity.ipynb`
  - 能力：target affinity 评估
  - 用途：评估 predictor 的 target affinity 表现
  - 复用状态：blocked；类型：unknown
- `src/models/components/evaluation.py`
  - 能力：评估指标与打分逻辑
  - 用途：实现或封装评估相关计算逻辑
  - 复用状态：blocked；类型：code_entry

### inference

- `scripts/generate_without_guidance.py`
  - 能力：无 guidance 生成
  - 用途：执行不带属性引导的分子生成
  - 复用状态：blocked；类型：code_entry
- `scripts/generate_with_single_property_guidance.py`
  - 能力：单属性 guidance 生成
  - 用途：执行单属性条件生成
  - 复用状态：blocked；类型：code_entry
- `scripts/generate_with_multi_property_guidance.py`
  - 能力：多属性 guidance 生成
  - 用途：执行多属性条件生成
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `src/models/ddpm.py`
  - 能力：核心 diffusion 生成模型
  - 用途：实现主生成模型与相关 dense diffusion 组件的核心代码
  - 复用状态：blocked；类型：code_entry
- `src/models/ddpm_guacamol.py`
  - 能力：Guacamol 变体与 VAE 组件
  - 用途：面向 Guacamol 任务的生成变体与 latent 组件
  - 复用状态：blocked；类型：code_entry
- `src/utils/diff_utils.py`
  - 能力：采样与字符串转换辅助
  - 用途：分子扩散、采样与辅助处理逻辑
  - 复用状态：blocked；类型：code_entry
- `src/utils/sascorer.py`
  - 能力：SA score 辅助
  - 用途：分子可合成性相关打分与碎片分数表
  - 复用状态：blocked；类型：code_entry
- `data/guacamol/idx_to_symbol.pickle`
  - 能力：Guacamol tokenizer/config
  - 用途：符号映射与序列长度配置，不应视为模型权重
  - 复用状态：blocked；类型：unknown
- `data/zinc250k/idx_to_symbol.pickle`
  - 能力：ZINC250k tokenizer/config
  - 用途：符号映射与序列长度配置，不应视为模型权重
  - 复用状态：blocked；类型：unknown

### training

- `scripts/train_predictor_target_affinity.py`
  - 能力：target affinity predictor 训练
  - 用途：训练用于 guidance 的 target affinity predictor
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅基于冻结清单做静态审阅，未执行代码、未安装依赖、未运行测试。
- 未发现任何明确的模型 checkpoint/权重文件；`.pickle` 更像词表/长度配置，不应按权重处理。
- 数据集文件的外部来源与许可未在冻结清单中核实。
- `src/utils/sascorer.py` 与 `src/utils/fpscores.pkl.gz` 的第三方来源仅能从文件名推测，未做内容级确认。

## 仍未知

- 仓库中的数据集是否为项目自建、整理镜像或外部下载，无法仅凭静态清单确认。
- 是否存在仓库外部下载的模型权重或运行时资源，冻结清单未显示。
- `README.md` 未在本次任务中展开逐段核读，因此关于流程细节只能依据文件名和清单推断。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
