# Fenglei104/DiffPROTACs

- **仓库：** [https://github.com/Fenglei104/DiffPROTACs](https://github.com/Fenglei104/DiffPROTACs)
- **固定 commit：** `ac20a851e545733e8ddf4463b2ef182a38a83e43`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 19

## 仓库摘要

这是 DiffPROTACs 的冻结仓库快照，包含 PROTAC 预处理、数据切分、DDP 训练、采样推理、测试脚本以及 3 个 `.ckpt` 与 3 个 `.pt` 资产；未发现 LICENSE，且未执行代码，因此只能做静态可复用性盘点，不能证明复现或直接复用。

## 可复用模块与资源

### checkpoints

- `checkpoints/protacs_best.ckpt`
  - 能力：PROTAC 生成模型权重
  - 用途：用于恢复 PROTAC 生成/优化模型。
  - 复用状态：blocked；类型：model_weight
- `checkpoints/geom_best.ckpt`
  - 能力：几何模块权重
  - 用途：用于恢复几何相关子模块。
  - 复用状态：blocked；类型：model_weight
- `checkpoints/zinc_best.ckpt`
  - 能力：ZINC 相关权重
  - 用途：用于恢复与 ZINC 相关的预训练或对照模型。
  - 复用状态：blocked；类型：model_weight

### datasets

- `datasets/protacs_train.pt`
  - 能力：训练集数据切分
  - 用途：训练阶段使用的数据张量/样本切分；`.pt` 在冻结清单里也被归入 checkpoint 候选，语义需人工复核。
  - 复用状态：blocked；类型：unknown
- `datasets/protacs_val.pt`
  - 能力：验证集数据切分
  - 用途：验证阶段使用的数据张量/样本切分；`.pt` 语义与 checkpoint 有歧义。
  - 复用状态：blocked；类型：unknown
- `datasets/protacs_test.pt`
  - 能力：测试集数据切分
  - 用途：测试阶段使用的数据张量/样本切分；`.pt` 语义与 checkpoint 有歧义。
  - 复用状态：blocked；类型：unknown
- `preprocess/protacDB_smiles.csv`
  - 能力：原始/中间 SMILES 表
  - 用途：作为 PROTAC SMILES 原始或中间输入表。
  - 复用状态：blocked；类型：unknown

### evaluation

- `test_ddp.py`
  - 能力：测试/评测
  - 用途：分布式测试或验证流程。
  - 复用状态：blocked；类型：code_entry

### inference

- `sample.py`
  - 能力：采样与推理
  - 用途：从 checkpoint 进行候选生成/采样。
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `dataset.py`
  - 能力：数据集封装
  - 用途：把预处理后的样本张量组织成训练可用的数据对象。
  - 复用状态：blocked；类型：code_entry
- `preprocess/prepare_dataset.py`
  - 能力：数据集构建与切分
  - 用途：从原始样本生成训练/验证/测试划分。
  - 复用状态：blocked；类型：code_entry
- `preprocess/prepare_protac.py`
  - 能力：PROTAC 原始样本预处理
  - 用途：清洗和规范化 PROTAC 输入表示。
  - 复用状态：blocked；类型：code_entry
- `preprocess/remove_h.py`
  - 能力：去氢与结构清洗
  - 用途：去除氢原子/清理结构后处理。
  - 复用状态：blocked；类型：code_entry
- `compute.py`
  - 能力：几何/构象计算辅助
  - 用途：支持坐标、距离或几何相关计算。
  - 复用状态：blocked；类型：code_entry
- `egnn.py`
  - 能力：EGNN 模型模块
  - 用途：提供等变图网络式特征建模。
  - 复用状态：blocked；类型：code_entry
- `graphormer_3d.py`
  - 能力：3D graph transformer 模块
  - 用途：提供三维图表示学习能力。
  - 复用状态：blocked；类型：code_entry
- `edm.py`
  - 能力：扩散生成核心
  - 用途：支持扩散式候选生成与反向采样。
  - 复用状态：blocked；类型：code_entry

### training

- `trainer.py`
  - 能力：训练循环
  - 用途：负责训练、优化与参数更新流程。
  - 复用状态：blocked；类型：code_entry
- `main_ddp.py`
  - 能力：分布式训练启动
  - 用途：作为 DDP 训练的主启动/调度脚本。
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态盘点，未运行仓库代码、未加载权重、未验证数据内容。
- 依赖未安装、tests 未跑，无法证明训练/推理/评测流程可执行。
- 仓库未发现 LICENSE，直接复用边界不清。
- `.pt` 文件在路径语义上像数据切分，但冻结清单同时将其计入 checkpoint 候选，存在歧义。

## 仍未知

- `datasets/protacs_*.pt` 的真实内容与生成方式未打开确认。
- `checkpoints/*.ckpt` 的训练配置、指标和来源未验证。
- `preprocess/protacDB_smiles.csv` 的外部来源与授权未确认。
- `egnn.py`、`graphormer_3d.py`、`edm.py` 是否为第三方改写或项目原生实现，静态清单无法判定。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
