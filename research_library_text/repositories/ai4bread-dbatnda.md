# AI4Bread/DBATNDA

- **仓库：** [https://github.com/AI4Bread/DBATNDA](https://github.com/AI4Bread/DBATNDA)
- **固定 commit：** `a3cd350a0cbe10b2a90f0147cf459e0989975443`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 15

## 仓库摘要

该冻结仓库主要提供图神经网络与自动编码器相关代码，含 `code/autoencoder.py`、`code/bat.py`、多组 `GAT/GCN/SAGE` 模块及若干 baseline 文件；未见 bundled data、训练/推理/评估入口或 checkpoints。LICENSE 缺失，使代码复用边界未闭合。

## 可复用模块与资源

### reusable_assets

- `code/autoencoder.py`
  - 能力：model_architecture
  - 用途：自动编码器/表示学习核心模块
  - 复用状态：blocked；类型：code_entry
- `code/bat.py`
  - 能力：model_architecture
  - 用途：主方法/图关联模型封装
  - 复用状态：blocked；类型：code_entry
- `code/nets/gat.py`
  - 能力：model_architecture
  - 用途：GAT backbone
  - 复用状态：blocked；类型：code_entry
- `code/nets/gcn.py`
  - 能力：model_architecture
  - 用途：GCN backbone
  - 复用状态：blocked；类型：code_entry
- `code/nets/sage.py`
  - 能力：model_architecture
  - 用途：SAGE backbone
  - 复用状态：blocked；类型：code_entry
- `code/nets/gens_networks/gat.py`
  - 能力：model_architecture
  - 用途：GAT 变体/子网络
  - 复用状态：blocked；类型：code_entry
- `code/nets/gens_networks/gcn.py`
  - 能力：model_architecture
  - 用途：GCN 变体/子网络
  - 复用状态：blocked；类型：code_entry
- `code/nets/gens_networks/sage.py`
  - 能力：model_architecture
  - 用途：SAGE 变体/子网络
  - 复用状态：blocked；类型：code_entry
- `code/graph_conversion.py`
  - 能力：preprocessing
  - 用途：图构建与特征转换辅助
  - 复用状态：blocked；类型：code_entry
- `code/main.py`
  - 能力：orchestration
  - 用途：实验调度/入口候选；静态上未证实为训练入口
  - 复用状态：blocked；类型：code_entry
- `code/utils.py`
  - 能力：utility
  - 用途：通用工具函数
  - 复用状态：blocked；类型：code_entry
- `code/baselines/graphens.py`
  - 能力：baseline_method
  - 用途：对比基线 GraphENS 实现
  - 复用状态：blocked；类型：code_entry
- `code/baselines/graphsmote.py`
  - 能力：baseline_method
  - 用途：对比基线 GraphSMOTE 实现
  - 复用状态：blocked；类型：code_entry
- `code/baselines/renode.py`
  - 能力：baseline_method
  - 用途：对比基线 ReNode 实现
  - 复用状态：blocked；类型：code_entry
- `code/baselines/reweight.py`
  - 能力：baseline_method
  - 用途：对比基线 ReWeight 实现
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态清单审计，未执行代码
- 依赖未安装，无法验证可运行性
- 未运行测试或 CI
- 未初始化子模块
- 存在大文件 promisor/截断风险
- 路径存在不等于可复现或可训练

## 仍未知

- `code/main.py` 是否承担真实训练/评估入口无法从文件名外确认
- `code/baselines/*` 是否为作者原创实现、第三方改写或直接移植无法确认
- 外部下载数据、隐藏 checkpoint 或运行时生成物未能仅凭静态清单排除

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
