# wanglabthu/biomolecule-al-decipher

- **仓库：** [https://github.com/wanglabthu/biomolecule-al-decipher](https://github.com/wanglabthu/biomolecule-al-decipher)
- **固定 commit：** `86020b8496820689ed0e0fbb11072fdceacf45a6`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 12

## 仓库摘要

该仓库提供 biomolecular active learning 的训练、UQ、AL 模拟与评估代码，并内置 14 个 CSV 基准数据集；冻结快照中未见 LICENSE、checkpoint 或独立推理入口，故代码与数据的直接复用边界未获授权确认。

## 可复用模块与资源

### datasets

- `data/D1_MPRALegNet_HepG2.csv`
  - 能力：benchmark_dataset
  - 用途：artifact_kind=unknown；MPRALegNet 三个 cell line 的基准 CSV
  - 复用状态：blocked；类型：unknown
- `data/D4_Malinois_HepG2.csv`
  - 能力：benchmark_dataset
  - 用途：artifact_kind=unknown；Malinois 三个 cell line 的基准 CSV
  - 复用状态：blocked；类型：unknown
- `data/D7_Ecoli_Wang_2020.csv`
  - 能力：benchmark_dataset
  - 用途：artifact_kind=unknown；Ecoli 两个实验批次的基准 CSV
  - 复用状态：blocked；类型：unknown
- `data/D9_Yeast_Aviv_2022.csv`
  - 能力：benchmark_dataset
  - 用途：artifact_kind=unknown；Yeast 与蛋白工程任务的其余基准 CSV
  - 复用状态：blocked；类型：unknown
- `data/data.zip`
  - 能力：dataset_archive
  - 用途：artifact_kind=unknown；打包的 CSV 数据归档，内容未单独解包核验
  - 复用状态：unknown；类型：unknown

### evaluation

- `src/evaluation.py`
  - 能力：evaluation_pipeline
  - 用途：artifact_kind=code_entry；评估流程与指标实现
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `src/AL_sim.py`
  - 能力：active_learning_simulation
  - 用途：artifact_kind=code_entry；AL 采样/查询模拟主流程，用于比较 active learning 策略在 biomolecular design 中的表现
  - 复用状态：blocked；类型：code_entry
- `src/UQ_DKL.py`
  - 能力：uncertainty_quantification
  - 用途：artifact_kind=code_entry；三类 UQ 后端（DKL、ensemble、Monte Carlo dropout），用于候选排序与 acquisition 选择
  - 复用状态：blocked；类型：code_entry
- `src/model_zoo.py`
  - 能力：model_architecture
  - 用途：artifact_kind=code_entry；通用与 DKL 专用模型结构定义，支撑 property prediction 与 AL 循环
  - 复用状态：blocked；类型：code_entry
- `src/configs.py`
  - 能力：configuration_and_helpers
  - 用途：artifact_kind=config；超参数、配置与通用辅助函数
  - 复用状态：blocked；类型：config
- `requirements.txt`
  - 能力：dependency_specification
  - 用途：artifact_kind=config；标准版与 DKL 版依赖声明
  - 复用状态：blocked；类型：unknown

### training

- `src/train.py`
  - 能力：training_entrypoint
  - 用途：artifact_kind=code_entry；标准模型与 DKL 变体的训练入口
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态审查，未运行仓库代码、测试或训练流程。
- dependencies 未安装，环境与可执行性未验证。
- 未发现 LICENSE/SPDX，代码与数据的直接复用受限。
- 未检出 tracked checkpoint 或 model weights，无法证明可复现推理产物。
- data.zip 的内容与各 CSV 的处理链未核验。

## 仍未知

- data/data.zip 是否仅为 CSV 归档，还是包含额外原始数据未知。
- train.py 与 train_DKL.py 的超参数、数据划分和早停策略未知。
- evaluation.py 与 metrics.py 的具体指标实现细节未知。
- 是否存在未跟踪的模型权重、缓存或外部下载产物未知。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
