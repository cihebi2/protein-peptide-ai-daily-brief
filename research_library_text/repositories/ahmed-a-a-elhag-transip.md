# Ahmed-A-A-Elhag/TransIP

- **仓库：** [https://github.com/Ahmed-A-A-Elhag/TransIP](https://github.com/Ahmed-A-A-Elhag/TransIP)
- **固定 commit：** `0a413593f5227a6166f084b223e37ade0d16574f`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 36

## 仓库摘要

仓库主要提供 TransIP 的 Transformer/attention 模型实现和一组 OMOL 数据、任务与 sweep 配置；静态清点未发现 bundled data、checkpoint、训练入口或独立推理入口，许可证为 MIT，但数据/模型边界未在仓库内闭合。

## 可复用模块与资源

### datasets

- `dataset/omol_4M.yaml`
  - 能力：OMOL 数据配置
  - 用途：OMOL 4M 数据划分/加载配置
  - 复用状态：partial；类型：config
- `dataset/omol_val.yaml`
  - 能力：OMOL 验证配置
  - 用途：OMOL 验证集配置
  - 复用状态：partial；类型：config
- `dataset/sweep_omol_2M.yaml`
  - 能力：OMOL sweep 数据配置
  - 用途：OMOL 2M sweep 数据配置
  - 复用状态：partial；类型：config
- `dataset/sweep_omol_4M.yaml`
  - 能力：OMOL sweep 数据配置
  - 用途：OMOL 4M sweep 数据配置
  - 复用状态：partial；类型：config
- `element_refs/iso_atom_elem_refs.yaml`
  - 能力：元素参考表
  - 用途：孤立原子元素参考表
  - 复用状态：partial；类型：config
- `element_refs/oc20_elem_refs.yaml`
  - 能力：元素参考表
  - 用途：OC20 元素参考表
  - 复用状态：partial；类型：config
- `element_refs/omol_elem_refs_dense.yaml`
  - 能力：元素参考表
  - 用途：OMOL 稠密元素参考表
  - 复用状态：partial；类型：config
- `mendeleev.yml`
  - 能力：元素属性表
  - 用途：元素属性/查表数据；来源与生成方式未核验
  - 复用状态：unknown；类型：config

### evaluation

- `omol_eval.yaml`
  - 能力：评测配置
  - 用途：显式评测配置；静态上未见独立评测入口
  - 复用状态：partial；类型：config

### reusable_assets

- `Dockerfile`
  - 能力：环境与依赖
  - 用途：定义容器构建与运行环境骨架
  - 复用状态：ready_for_review；类型：unknown
- `pyproject.toml`
  - 能力：环境与依赖
  - 用途：定义 Python 包元数据、依赖约束与构建入口
  - 复用状态：ready_for_review；类型：config
- `transip/models/__init__.py`
  - 能力：包初始化
  - 用途：仅提供包命名空间，不含核心算法逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `transip/models/attn_runtime.py`
  - 能力：attention 运行时
  - 用途：attention 运行时支撑/加速封装
  - 复用状态：ready_for_review；类型：code_entry
- `transip/models/heads_equiv_loss.py`
  - 能力：输出头
  - 用途：带等变损失约束的输出头
  - 复用状态：ready_for_review；类型：code_entry
- `transip/models/heads_transformer_direct.py`
  - 能力：输出头
  - 用途：直接预测输出头
  - 复用状态：ready_for_review；类型：code_entry
- `transip/models/heads_transformer_grad.py`
  - 能力：输出头
  - 用途：基于梯度的输出头
  - 复用状态：ready_for_review；类型：code_entry
- `transip/models/prefix_unit.py`
  - 能力：prefix 模块
  - 用途：prefix / 条件化单元
  - 复用状态：ready_for_review；类型：code_entry
- `transip/models/shims.py`
  - 能力：兼容 shim
  - 用途：接口兼容与适配层
  - 复用状态：ready_for_review；类型：code_entry
- `transip/models/shims_collate.py`
  - 能力：batch collate
  - 用途：batch 组装与 collate 辅助
  - 复用状态：ready_for_review；类型：code_entry
- `transip/models/transformer.py`
  - 能力：Transformer 模型
  - 用途：高层 Transformer 模型组装
  - 复用状态：ready_for_review；类型：code_entry
- `transip/models/transformer_core.py`
  - 能力：Transformer 核心
  - 用途：核心 Transformer 层、块与内部计算
  - 复用状态：ready_for_review；类型：code_entry

### training

- `sweep/train_sweep_omol.yaml`
  - 能力：训练 sweep 入口
  - 用途：OMOL 训练 sweep 入口配置
  - 复用状态：partial；类型：config
- `cluster/local.yaml`
  - 能力：本地执行配置
  - 用途：本地训练/实验执行配置
  - 复用状态：partial；类型：config
- `cluster/sweep_local.yaml`
  - 能力：本地 sweep 编排
  - 用途：本地 sweep 编排配置
  - 复用状态：partial；类型：config
- `cluster/sweep_slurm.yaml`
  - 能力：Slurm sweep 编排
  - 用途：Slurm 环境下的 sweep 编排配置
  - 复用状态：partial；类型：config
- `backbone/transformer.yaml`
  - 能力：backbone 配置
  - 用途：Transformer backbone 超参配置
  - 复用状态：partial；类型：config
- `backbone/esen.yaml`
  - 能力：backbone 配置
  - 用途：另一 backbone 配置
  - 复用状态：partial；类型：config
- `tasks/omol.yaml`
  - 能力：任务定义
  - 用途：OMOL 任务定义
  - 复用状态：partial；类型：config
- `tasks/omol_e_force.yaml`
  - 能力：任务定义
  - 用途：能量+力任务定义
  - 复用状态：partial；类型：config
- `tasks/omol_e_force_augment.yaml`
  - 能力：任务定义
  - 用途：能量+力增强任务定义
  - 复用状态：partial；类型：config
- `tasks/omol_energy_only.yaml`
  - 能力：任务定义
  - 用途：仅能量任务定义
  - 复用状态：partial；类型：config
- `tasks/omol_energy_only_augment.yaml`
  - 能力：任务定义
  - 用途：仅能量增强任务定义
  - 复用状态：partial；类型：config
- `omol.yaml`
  - 能力：顶层 OMOL 配置
  - 用途：OMOL 顶层实验/任务配置
  - 复用状态：partial；类型：config
- `omol_augment.yaml`
  - 能力：增强配置
  - 用途：OMOL 增强实验配置
  - 复用状态：partial；类型：config
- `omol_sweep.yaml`
  - 能力：sweep 配置
  - 用途：OMOL sweep 顶层配置
  - 复用状态：partial；类型：config
- `omol_sweep_augment.yaml`
  - 能力：增强 sweep 配置
  - 用途：OMOL 增强 sweep 配置
  - 复用状态：partial；类型：config

## 使用限制

- 仅做静态审阅，未安装依赖、未运行代码、未跑测试。
- clone_depth=1 且 large blobs 可能为 promisor only，存在未展开内容的风险。
- 未发现独立训练入口、推理入口或评测入口脚本；只有 YAML 配置与模型源码。
- 未发现 tracked checkpoint/权重文件，也未发现 bundled 原始数据。
- YAML 配置、数据路径与外部资源的可执行性未核验。

## 仍未知

- `dataset/*.yaml` 与 `tasks/*.yaml` 指向的实际数据位置、split 规则和下载源未知。
- `attn_runtime.py` 是否依赖未跟踪的编译扩展或特定 CUDA 环境未知。
- `mendeleev.yml` 是否为项目生成还是 vendored 第三方数据未知。
- `element_refs/*.yaml` 的生成流程与许可来源未核验。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
