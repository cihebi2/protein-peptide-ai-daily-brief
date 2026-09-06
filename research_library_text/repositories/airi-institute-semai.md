# AIRI-Institute/SEMAi

- **仓库：** [https://github.com/AIRI-Institute/SEMAi](https://github.com/AIRI-Institute/SEMAi)
- **固定 commit：** `a153165133062ec17740f12c67ad172b06693a81`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 33

## 仓库摘要

该仓库以 SEMA/SEMAi 为核心，包含 B-cell conformational epitopes prediction 的数据构建、SEMA-1D/3D 与 PTM 训练/推理流程，以及一个基于 Foldseek 的结构比较模型；静态清单未见 LICENSE、checkpoint 或独立 evaluation 产物。

## 可复用模块与资源

### datasets

- `epitopes_prediction/data/sema_1.0/train_set.csv`
  - 能力：SEMA 1.0 epitope splits
  - 用途：SEMA-1D/相关 epitope 任务的训练集
  - 复用状态：blocked；类型：unknown
- `epitopes_prediction/data/sema_1.0/test_set.csv`
  - 能力：SEMA 1.0 epitope splits
  - 用途：SEMA-1D/相关 epitope 任务的测试集
  - 复用状态：blocked；类型：unknown
- `epitopes_prediction/data/sema_2.0/train_set.csv`
  - 能力：SEMA 2.0 epitope splits
  - 用途：SEMA-2.0 版本的训练集
  - 复用状态：blocked；类型：unknown
- `epitopes_prediction/data/sema_2.0/test_set.csv`
  - 能力：SEMA 2.0 epitope splits
  - 用途：SEMA-2.0 版本的测试集
  - 复用状态：blocked；类型：unknown
- `epitopes_prediction/data/test_pdb.pdb`
  - 能力：结构化示例输入
  - 用途：epitope prediction 示例结构输入
  - 复用状态：blocked；类型：unknown
- `epitopes_comparison/inference_examples/7LM9_A.pdb`
  - 能力：结构比较示例输入
  - 用途：结构比较/推理示例输入
  - 复用状态：blocked；类型：unknown
- `epitopes_comparison/inference_examples/7RBY_C.pdb`
  - 能力：结构比较示例输入
  - 用途：结构比较/推理示例输入
  - 复用状态：blocked；类型：unknown
- `epitopes_comparison/inference_examples/8FDW_A.pdb`
  - 能力：结构比较示例输入
  - 用途：结构比较/推理示例输入
  - 复用状态：blocked；类型：unknown
- `epitopes_comparison/inference_examples/8U1G_A.pdb`
  - 能力：结构比较示例输入
  - 用途：结构比较/推理示例输入
  - 复用状态：blocked；类型：unknown
- `epitopes_prediction/dataset_generation/all_dataset.pkl.gz`
  - 能力：序列/结构数据缓存
  - 用途：序列或结构相关的序列化数据缓存/中间数据
  - 复用状态：blocked；类型：unknown
- `epitopes_comparison/small_dataset.tar.gz`
  - 能力：快速实验数据包
  - 用途：用于小规模实验或示例的打包数据
  - 复用状态：blocked；类型：unknown
- `glycosylation_prediction/data/Nglyco_test.pkl`
  - 能力：PTM 数据
  - 用途：N-glycosylation/PTM 任务测试数据
  - 复用状态：blocked；类型：unknown
- `glycosylation_prediction/data/Nglyco_val.pkl`
  - 能力：PTM 数据
  - 用途：N-glycosylation/PTM 任务验证数据
  - 复用状态：blocked；类型：unknown

### inference

- `epitopes_comparison/epi_compare_inference.ipynb`
  - 能力：比较推理
  - 用途：对结构比较模型做推理/打分演示
  - 复用状态：blocked；类型：unknown
- `epitopes_prediction/SEMA_1D/SEMA-1D_inference.ipynb`
  - 能力：SEMA-1D inference
  - 用途：对 SEMA-1D 模型执行预测/推理
  - 复用状态：blocked；类型：unknown
- `epitopes_prediction/SEMA_3D/SEMA-3D_inference.ipynb`
  - 能力：SEMA-3D inference
  - 用途：对 SEMA-3D 模型执行预测/推理
  - 复用状态：blocked；类型：unknown
- `glycosylation_prediction/SEMA_PTM/PTM_inference.ipynb`
  - 能力：PTM inference
  - 用途：对 PTM/N-glycosylation 模型执行预测/推理
  - 复用状态：blocked；类型：unknown

### reusable_assets

- `epitopes_comparison/saprot_epi_compare_model.py`
  - 能力：结构比较模型
  - 用途：定义表位比较/打分模型结构，用于结构比较任务的建模与复用
  - 复用状态：blocked；类型：code_entry
- `epitopes_comparison/saprot_dataset.py`
  - 能力：数据集适配器
  - 用途：提供比较模型训练所需的数据封装/样本适配逻辑
  - 复用状态：blocked；类型：code_entry
- `epitopes_comparison/dataset_generation/01_afdb_prep.py`
  - 能力：AFDB预处理
  - 用途：为结构比较数据集准备 AlphaFold/结构输入
  - 复用状态：blocked；类型：code_entry
- `epitopes_comparison/dataset_generation/02_structure_based_alignment.py`
  - 能力：结构对齐
  - 用途：执行基于结构的对齐步骤，为后续特征或标签计算服务
  - 复用状态：blocked；类型：code_entry
- `epitopes_comparison/dataset_generation/03_calculate_sema_scores.py`
  - 能力：SEMA分数计算
  - 用途：计算 SEMA 相关评分，用于构建比较任务标签/监督信号
  - 复用状态：blocked；类型：code_entry
- `epitopes_comparison/dataset_generation/04_generate_ds.py`
  - 能力：数据集生成
  - 用途：汇总前序步骤，生成比较任务数据集
  - 复用状态：blocked；类型：code_entry
- `epitopes_prediction/dataset_generation/prepare_SEMA_dataset.ipynb`
  - 能力：SEMA数据准备
  - 用途：准备 epitope prediction 相关的训练/测试数据与预处理流程
  - 复用状态：blocked；类型：unknown
- `saprot_utils/foldseek_util.py`
  - 能力：Foldseek封装
  - 用途：封装 Foldseek 调用，支撑结构比对/结构检索相关流程
  - 复用状态：blocked；类型：code_entry
- `saprot_utils/bin/foldseek`
  - 能力：Foldseek二进制
  - 用途：提供结构比对所需的 vendored 可执行程序
  - 复用状态：unknown；类型：unknown

### training

- `epitopes_comparison/train.py`
  - 能力：比较模型训练
  - 用途：结构比较模型的训练入口
  - 复用状态：blocked；类型：code_entry
- `epitopes_prediction/SEMA_1D/SEMA-1D_finetuning_ESMV2_650.ipynb`
  - 能力：SEMA-1D fine-tuning
  - 用途：对 ESMV2-650 做 SEMA-1D 微调
  - 复用状态：blocked；类型：unknown
- `epitopes_prediction/SEMA_1D/SEMA-1D_finetuning_ESMV2_650-old_train.ipynb`
  - 能力：SEMA-1D fine-tuning
  - 用途：SEMA-1D 的旧版训练笔记本/历史训练流程
  - 复用状态：blocked；类型：unknown
- `epitopes_prediction/SEMA_1D/SEMA-1D_finetuning_ESMV2_3B.ipynb`
  - 能力：SEMA-1D fine-tuning
  - 用途：对 ESMV2-3B 做 SEMA-1D 微调
  - 复用状态：blocked；类型：unknown
- `epitopes_prediction/SEMA_1D/SEMA-1D_finetuning_ESMV2_3B-old_train.ipynb`
  - 能力：SEMA-1D fine-tuning
  - 用途：SEMA-1D 的旧版训练笔记本/历史训练流程
  - 复用状态：blocked；类型：unknown
- `epitopes_prediction/SEMA_3D/SEMA-3D_finetuning.ipynb`
  - 能力：SEMA-3D fine-tuning
  - 用途：3D 结构版本的训练/微调流程
  - 复用状态：blocked；类型：unknown
- `glycosylation_prediction/SEMA_PTM/PTM_finetuning.ipynb`
  - 能力：PTM fine-tuning
  - 用途：N-glycosylation/PTM 任务训练流程
  - 复用状态：blocked；类型：unknown

## 使用限制

- 仅做静态审计，未安装依赖、未运行代码、未执行测试。
- tracked path 的存在不等于可复现或已验证的运行结果。
- 未见独立 checkpoint 文件，无法从冻结清单确认已发布权重。
- 未见独立 evaluation 产物或基准脚本，评测流程可能埋在 notebook 内但未能从路径级证据拆分。

## 仍未知

- `epitopes_prediction/dataset_generation/all_dataset.pkl.gz` 与 `epitopes_comparison/small_dataset.tar.gz` 的生成来源、是否含派生标签，以及是否可公开复用，均未能仅凭路径确认。
- `saprot_utils/bin/foldseek` 作为 vendored 第三方二进制，其上游版本和许可边界未在冻结清单中明确。
- 多个 `*_old_train.ipynb` 看起来是历史训练变体，但其与最新 notebook 的差异未被静态确认。
- `epitopes_comparison/epi_compare_inference.ipynb` 可能同时包含推理与评价逻辑，但无法仅据文件名拆出独立 evaluation 入口。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
