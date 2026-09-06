# Aalto-QuML/Hourglass

- **仓库：** [https://github.com/Aalto-QuML/Hourglass](https://github.com/Aalto-QuML/Hourglass)
- **固定 commit：** `ed1338af188733c9c613d5ecce29bb6f75fba875`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 12

## 仓库摘要

该仓库是一个以 GNN、PersLay、RephINE 和持久同调自定义算子为核心的研究代码库，包含训练、推理、结果汇总与复现实验脚本；静态清单未见 bundled 数据或 checkpoint，代码许可证为 MIT。

## 可复用模块与资源

### datasets

- `results/main/IMDB-BINARY/2/8/16_hidden/64_outdim/True_dim1/summary.json`
  - 能力：graph benchmark reference: IMDB-BINARY
  - 用途：结果树表明仓库在 IMDB-BINARY 上做了 main 与 PersLay 评测；未见原始数据文件
  - 复用状态：blocked；类型：config
- `results/main/NCI1/2/8/16_hidden/64_outdim/True_dim1/summary.json`
  - 能力：graph benchmark reference: NCI1
  - 用途：结果树表明仓库在 NCI1 上做了 main 与 PersLay 评测；未见原始数据文件
  - 复用状态：blocked；类型：config
- `results/main/NCI109/2/8/16_hidden/64_outdim/True_dim1/summary.json`
  - 能力：graph benchmark reference: NCI109
  - 用途：结果树表明仓库在 NCI109 上做了 main 与 PersLay 评测；未见原始数据文件
  - 复用状态：blocked；类型：config
- `results/main/PROTEINS/2/8/16_hidden/64_outdim/True_dim1/summary.json`
  - 能力：graph benchmark reference: PROTEINS
  - 用途：结果树表明仓库在 PROTEINS 上做了 main 与 PersLay 评测；未见原始数据文件
  - 复用状态：blocked；类型：config

### evaluation

- `results.ipynb`
  - 能力：main experiment result summaries
  - 用途：汇总 main 线路在 IMDB-BINARY、NCI1、NCI109、PROTEINS 上的对比结果
  - 复用状态：partial；类型：unknown
- `results_perslay.ipynb`
  - 能力：PersLay result summaries
  - 用途：汇总 PersLay 线路在 IMDB-BINARY、NCI1、NCI109、PROTEINS 上的重复实验结果
  - 复用状态：partial；类型：unknown

### inference

- `runners/run_inference.py`
  - 能力：inference runner
  - 用途：执行已训练模型的推理流程
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `models/gnn.py`
  - 能力：core model and layer implementations
  - 用途：实现 GCN/GIN/PNA 及图等变/置换等变层，并封装 PersLay、RephINE、TopoGNN 等模型变体
  - 复用状态：ready_for_review；类型：code_entry
- `torch_ph/ph/forward_only_mt_cpu.cpp`
  - 能力：custom persistent-homology CPU extension
  - 用途：提供 forward/backward、extended persistence、rephine 等自定义持久同调扩展实现
  - 复用状态：ready_for_review；类型：unknown
- `reproducibility/cli_main.py`
  - 能力：reproducibility and experiment orchestration utilities
  - 用途：封装实验配置保存、主流程调度与可复现实验 CLI
  - 复用状态：ready_for_review；类型：code_entry

### training

- `train.py`
  - 能力：main training entrypoint
  - 用途：主训练脚本，驱动 GNN/拓扑模型的训练流程
  - 复用状态：ready_for_review；类型：code_entry
- `main_perslay.py`
  - 能力：PersLay training / experiment CLI
  - 用途：PersLay 分支的训练与实验入口
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- not_executed_static_analysis_only
- dependencies_not_installed
- repository_code_not_executed
- tests_not_run
- submodules_not_initialized
- large_blobs_over_5MiB_may_be_promisor_only
- path_presence_is_not_reproduction_evidence
- no_bundled_raw_dataset_found
- no_checkpoint_files_found

## 仍未知

- `torch_ph` C++ extension 是否包含第三方 vendored 代码，静态清单未给出来源说明。
- `*.results` 与 notebook 输出是否对应论文中的最终数值，无法仅凭路径确认。
- 外部基准数据的具体下载来源与许可未在冻结清单中出现。
- shallow clone 下是否遗漏了较大的模型权重或数据分片，无法从路径存在性判断。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
