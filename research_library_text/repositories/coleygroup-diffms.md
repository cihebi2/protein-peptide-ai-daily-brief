# coleygroup/DiffMS

- **仓库：** [https://github.com/coleygroup/DiffMS](https://github.com/coleygroup/DiffMS)
- **固定 commit：** `814220bf0acf8433d8052e7f3e07be9fe7b6b9ca`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 18

## 仓库摘要

该仓库的冻结清单可确认 DiffMS 的扩散式分子生成主线、谱图编码与数据管线、评测模块，以及 MIT 代码许可；未发现 checkpoints、独立 inference 入口或可验证的数据/模型专门许可，且仅做静态审计。

## 可复用模块与资源

### datasets

- `data_processing/build_fp2mol_datasets.py`
  - 能力：fp2mol 数据下载与构建
  - 用途：下载后构建 fp2mol 数据集、切分与预处理。
  - 复用状态：partial；类型：code_entry
- `src/datasets/spec2mol_dataset.py`
  - 能力：CANOPUS / spec2mol 数据包装
  - 用途：封装 spec2mol 数据对象，并对接 CANOPUS 下载脚本。
  - 复用状态：partial；类型：code_entry
- `src/datasets/spectra_utils.py`
  - 能力：MSG 数据与谱图工具
  - 用途：对 MSG 数据与谱图特征/格式进行辅助处理。
  - 复用状态：partial；类型：code_entry
- `src/mist/data/datasets.py`
  - 能力：数据封装、特征化与切分辅助
  - 用途：提供数据对象、featurizer 与 splitter 支持。
  - 复用状态：partial；类型：code_entry

### evaluation

- `src/metrics/diffms_metrics.py`
  - 能力：DiffMS 专用评测
  - 用途：面向 DiffMS 任务的专用评测指标。
  - 复用状态：ready_for_review；类型：code_entry
- `src/metrics/molecular_metrics.py`
  - 能力：通用分子指标
  - 用途：分子质量、结构与相关通用指标计算。
  - 复用状态：ready_for_review；类型：code_entry
- `src/metrics/molecular_metrics_discrete.py`
  - 能力：离散分子表示评测
  - 用途：适配离散输出表示的指标变体。
  - 复用状态：ready_for_review；类型：code_entry

### inference

- `src/diffusion_model_fp2mol.py`
  - 能力：fp2mol 采样/推断实现
  - 用途：推断或采样阶段的核心模型实现；未见独立 inference wrapper。
  - 复用状态：partial；类型：code_entry
- `src/diffusion_model_spec2mol.py`
  - 能力：spec2mol 采样/推断实现
  - 用途：推断或采样阶段的核心模型实现；未见独立 inference wrapper。
  - 复用状态：partial；类型：code_entry
- `src/models/transformer_model.py`
  - 能力：Transformer 解码/生成骨架
  - 用途：推断阶段的 Transformer 公共组件。
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `configs/config.yaml`
  - 能力：配置与实验编排
  - 用途：统一组织数据集、模型与训练超参数；配套 dataset/model/train 默认配置。
  - 复用状态：ready_for_review；类型：config
- `src/diffusion_model_fp2mol.py`
  - 能力：fp2mol 条件扩散生成
  - 用途：fp2mol 任务的核心生成模型实现，配套 diffusion 相关模块完成条件扩散生成。
  - 复用状态：ready_for_review；类型：code_entry
- `src/diffusion_model_spec2mol.py`
  - 能力：spec2mol / Transformer 生成骨架
  - 用途：spec2mol 任务的分子生成实现，并与 Transformer 结构协同。
  - 复用状态：ready_for_review；类型：code_entry
- `src/mist/models/spectra_encoder.py`
  - 能力：谱图编码与 MIST 命名空间组件
  - 用途：mass spectra 编码、form embedding 与 Transformer 组件，支撑条件表示学习。
  - 复用状态：partial；类型：code_entry
- `src/models/transformer_model.py`
  - 能力：通用 Transformer 模型骨架
  - 用途：通用 Transformer 生成/解码骨架，可作为模型实现与推断的公共组件。
  - 复用状态：ready_for_review；类型：code_entry

### training

- `src/metrics/train_metrics.py`
  - 能力：训练阶段指标统计
  - 用途：训练过程中的指标汇总与日志统计。
  - 复用状态：partial；类型：code_entry
- `src/fp2mol_main.py`
  - 能力：fp2mol 主程序入口候选
  - 用途：可能承载 fp2mol 训练/运行流程；冻结审计未将其单独标记为 training_entrypoint。
  - 复用状态：unknown；类型：code_entry
- `src/spec2mol_main.py`
  - 能力：spec2mol 主程序入口候选
  - 用途：可能承载 spec2mol 训练/运行流程；冻结审计未将其单独标记为 training_entrypoint。
  - 复用状态：unknown；类型：code_entry

## 使用限制

- 仅做静态审计，未执行代码、依赖或测试。
- 冻结清单未发现 checkpoints。
- 冻结清单未发现独立 inference 入口。
- 数据下载脚本指向外部来源，但外部数据许可未在清单中解析。
- `src/mist/*` 命名空间是否为 vendored third-party 组件无法仅凭路径确认。

## 仍未知

- `src/fp2mol_main.py` 和 `src/spec2mol_main.py` 的实际职责（训练/推理/实验封装）未能从冻结清单确认。
- fp2mol/CANOPUS/MSG 外部数据集的具体许可与再分发边界未知。
- 是否存在未列入清单的预训练权重或大型 promisor blob 未能从静态审计证明。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
