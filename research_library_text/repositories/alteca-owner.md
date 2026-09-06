# alteca/OWNER

- **仓库：** [https://github.com/alteca/OWNER](https://github.com/alteca/OWNER)
- **固定 commit：** `d1e6cb7b5c33a6ff33c91ea5a050421a814ced65`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0
- **资产记录数：** 26

## 仓库摘要

该仓库更像 OWNER 的实验框架：包含多数据集预处理、训练、评估与复现实验配置；未见打包数据、checkpoint 或独立 inference 入口，代码许可为 GPL-3.0。

## 可复用模块与资源

### datasets

- `configs/data/conll2003.toml`
  - 能力：CoNLL-2003 家族数据集支持
  - 用途：CoNLL-2003 及 conll2003-ai / conll2003-music 的数据配置与预处理
  - 复用状态：partial；类型：config
- `configs/data/crossner.toml`
  - 能力：CrossNER 数据集支持
  - 用途：CrossNER 的数据配置与预处理
  - 复用状态：partial；类型：config
- `configs/data/fabner.toml`
  - 能力：FABNER 数据集支持
  - 用途：FABNER 的数据配置与预处理
  - 复用状态：partial；类型：config
- `configs/data/genia.toml`
  - 能力：GENIA 数据集支持
  - 用途：GENIA 的数据配置与预处理
  - 复用状态：partial；类型：config
- `configs/data/gentle.toml`
  - 能力：GENTLE 数据集配置
  - 用途：仅见数据配置；冻结清单中未见对应预处理器
  - 复用状态：partial；类型：config
- `configs/data/gum.toml`
  - 能力：GUM 数据集支持
  - 用途：GUM 的数据配置与预处理
  - 复用状态：partial；类型：config
- `configs/data/i2b2.toml`
  - 能力：i2b2 数据集支持
  - 用途：i2b2 的数据配置与预处理
  - 复用状态：partial；类型：config
- `configs/data/mit.toml`
  - 能力：MIT 数据集支持
  - 用途：MIT 的数据配置与预处理
  - 复用状态：partial；类型：config
- `configs/data/pilener.toml`
  - 能力：PILENER 家族数据集支持
  - 用途：PILENER 及 pilener-ai / pilener-i2b2 的数据配置与预处理
  - 复用状态：partial；类型：config
- `configs/data/wnut17.toml`
  - 能力：WNUT17 数据集支持
  - 用途：WNUT17 的数据配置与预处理
  - 复用状态：partial；类型：config

### evaluation

- `owner/evaluation/entity_typing.py`
  - 能力：实体类型评估
  - 用途：实体类型任务的指标计算与评估逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `owner/evaluation/mention_detection.py`
  - 能力：mention detection 评估
  - 用途：mention detection 任务的指标计算与评估逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `owner/baseline_evaluation.py`
  - 能力：评估基线驱动脚本
  - 用途：执行/汇总基线评估结果
  - 复用状态：partial；类型：code_entry
- `owner/evaluation/base.py`
  - 能力：评估基础抽象
  - 用途：为不同任务的评估器提供共同接口
  - 复用状态：ready_for_review；类型：code_entry

### inference

- `owner/models/entity_typing.py`
  - 能力：预测时模型定义（无独立 inference 入口）
  - 用途：加载训练权重后执行前向预测；冻结清单中未见专门 inference 目录
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `owner/prepare_data.py`
  - 能力：数据准备编排
  - 用途：串联各语料的准备/整理流程，便于复用为数据准备脚本
  - 复用状态：partial；类型：code_entry
- `owner/data/model.py`
  - 能力：共享数据表示与序列化
  - 用途：统一表示样本/模型相关数据结构，并支持序列化辅助
  - 复用状态：ready_for_review；类型：code_entry
- `owner/data/preprocessing/base.py`
  - 能力：预处理抽象层
  - 用途：为各数据集预处理器提供共同接口与基础逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `owner/models/entity_typing.py`
  - 能力：实体类型模型定义
  - 用途：实体类型预测的模型结构，可作为推理/训练的核心网络定义
  - 复用状态：ready_for_review；类型：code_entry
- `owner/models/mention_detection.py`
  - 能力：mention detection 模型定义
  - 用途：mention detection 的模型结构，可作为推理/训练的核心网络定义
  - 复用状态：ready_for_review；类型：code_entry
- `owner/training/base.py`
  - 能力：训练框架
  - 用途：统一训练循环与任务封装，供 NER / entity typing / mention detection 复用
  - 复用状态：ready_for_review；类型：code_entry
- `configs/baselines/uniner-uns.toml`
  - 能力：基线配置
  - 用途：定义 UniNER-UNS 基线实验参数
  - 复用状态：ready_for_review；类型：config
- `configs/reproducibility/runner.py`
  - 能力：复现实验 runner 与模板
  - 用途：批量运行复现实验；配合 template.toml 与 runs.csv
  - 复用状态：ready_for_review；类型：code_entry

### training

- `owner/training/ner.py`
  - 能力：NER 训练流程
  - 用途：整合 NER 任务的训练过程
  - 复用状态：ready_for_review；类型：code_entry
- `owner/training/entity_typing.py`
  - 能力：实体类型训练流程
  - 用途：实体类型任务的训练循环与参数封装
  - 复用状态：ready_for_review；类型：code_entry
- `owner/training/mention_detection.py`
  - 能力：mention detection 训练流程
  - 用途：mention detection 任务的训练循环与参数封装
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态清单分析，未执行代码、未安装依赖、未运行测试。
- 冻结 inventory 中未发现 bundled data 或 checkpoints。
- 仓库内容不足以证明任何训练/评估/推理已成功复现。
- 部分入口脚本（如 owner/main.py）未读内容，实际 CLI 角色仍不确定。

## 仍未知

- data/ 目录与 data/.raw/ 仅见占位文件；真实数据下载来源、版本与许可未确认。
- 是否存在运行时自动下载数据、缓存或外部权重，无法从静态路径本身判断。
- configs/reproducibility/* 是否足以完整复现实验，未执行验证。
- 未发现独立 checkpoints，因此模型权重发布方式与权重许可未知。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
