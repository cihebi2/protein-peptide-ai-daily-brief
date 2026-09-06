# MeshchaninovViacheslav/DiMA

- **仓库：** [https://github.com/MeshchaninovViacheslav/DiMA](https://github.com/MeshchaninovViacheslav/DiMA)
- **固定 commit：** `18f4a2e67988efe1cc5593fcaec1ece8f09fdac0`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 15

## 仓库摘要

该仓库实现了基于蛋白语言模型编码的扩散式序列生成主干、相关 encoder/metric/数据加载与训练脚本，并提供少量 AFDB 分布缓存；当前可复用边界主要是 MIT 代码，未见独立的可执行 inference 入口或 tracked checkpoint 权重。

## 可复用模块与资源

### checkpoints

- `src/utils/pretrained_utils.py`
  - 能力：预训练权重加载工具
  - 用途：加载或管理外部预训练权重与 checkpoint 路径；未见 tracked 权重本体
  - 复用状态：partial；类型：code_entry

### datasets

- `data/distributions/AFDB-v2.npy`
  - 能力：AFDB-v2 长度/分布缓存
  - 用途：作为 AFDB-v2 的分布或统计缓存，供采样或预处理
  - 复用状态：partial；类型：unknown
- `data/distributions/AFDB-v2-64-510.npy`
  - 能力：AFDB-v2 64-510 子集分布缓存
  - 用途：作为指定长度区间子集的分布或统计缓存
  - 复用状态：partial；类型：unknown

### evaluation

- `src/metrics/fid.py`
  - 能力：分布质量评估
  - 用途：衡量生成样本与参考分布差异
  - 复用状态：ready_for_review；类型：code_entry
- `src/metrics/mmd.py`
  - 能力：样本集距离评估
  - 用途：以 MMD 比较生成集与参考集
  - 复用状态：ready_for_review；类型：code_entry
- `src/metrics/plddt.py`
  - 能力：结构质量/置信度评估
  - 用途：评估生成结构或相关预测的 pLDDT 指标
  - 复用状态：ready_for_review；类型：code_entry
- `src/metrics/esmpppl.py`
  - 能力：语言模型困惑度评估
  - 用途：计算 ESM perplexity 作为序列质量 proxy
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `src/diffusion/dima.py`
  - 能力：核心扩散生成主干
  - 用途：实现 DiMA 的扩散式蛋白序列生成与训练主流程
  - 复用状态：ready_for_review；类型：code_entry
- `src/encoders/esm2.py`
  - 能力：蛋白序列表征编码器适配
  - 用途：将 ESM2 等语言模型表征接入生成模型
  - 复用状态：ready_for_review；类型：code_entry
- `src/datasets/load_hub.py`
  - 能力：数据读取与 hub 拉取
  - 用途：从远端 hub 或本地缓存读取数据集/样本
  - 复用状态：partial；类型：code_entry
- `src/helpers/prepare_length_distribution.py`
  - 能力：长度分布预处理
  - 用途：构造长度采样分布缓存，供生成阶段采样
  - 复用状态：partial；类型：code_entry
- `src/configs/structure_generation/default.yaml`
  - 能力：训练/生成配置 recipe
  - 用途：定义结构/序列生成默认超参模板
  - 复用状态：ready_for_review；类型：config

### training

- `train_diffusion.py`
  - 能力：主训练入口
  - 用途：驱动 DiMA diffusion 训练
  - 复用状态：ready_for_review；类型：code_entry
- `src/preprocessing/train_decoder.py`
  - 能力：decoder 预训练流程
  - 用途：训练 decoder 预处理/前置模块
  - 复用状态：ready_for_review；类型：code_entry
- `src/utils/training_utils.py`
  - 能力：训练辅助工具
  - 用途：提供训练循环、优化与日志等公共辅助
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态审查，未运行代码、未安装依赖，也未验证任何结果。
- 未发现独立的 inference 入口脚本；生成流程可能分散在 diffusion/solver 模块中。
- 未见 tracked 的权重文件或 checkpoint 二进制；当前只有加载工具。
- `*.npy` 分布缓存的具体内容、来源与生成条件无法仅凭静态路径确认。
- 仓库内未提供外部 encoder/weight 的上游许可文本，`ESM2`、`ESMC`、`SaProt` 相关依赖需另行核查。

## 仍未知

- `src/datasets/load_hub.py` 实际拉取的数据源、版本和访问条件未验证。
- `AFDB-v2*.npy` 是否完全由仓库内代码生成，还是来自外部预处理，未能确认。
- `src/utils/pretrained_utils.py` 会指向哪些外部 checkpoint/URL 未能确认。
- `src/configs/encoder/*.yaml` 依赖的第三方 encoder 权重与许可未在仓库中明确。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
