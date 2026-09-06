# mosGraph/mosGraphGPT

- **仓库：** [https://github.com/mosGraph/mosGraphGPT](https://github.com/mosGraph/mosGraphGPT)
- **固定 commit：** `217cdf3a17cb255c3b491f2ff6cc407ad3fb5242`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 12

## 仓库摘要

仓库主要包含多组学图模型的训练脚本、图数据加载/解码器实现、ROSMAP/UCSC/Cora 数据与少量结果表；未发现 LICENSE，且仅做静态审查，故代码、数据与权重的直接复用边界均未被验证。

## 可复用模块与资源

### checkpoints

- `MaskGAE-GraphClas.pt`
  - 能力：trained_weights
  - 用途：图分类模型权重；`MaskGAE-GraphClas copy.pt` 为同名拷贝/镜像文件
  - 复用状态：blocked；类型：model_weight

### datasets

- `data/Cora/raw/ind.cora.x`
  - 能力：benchmark_graph_data
  - 用途：Cora 基准图数据与 PyG 处理缓存；包含 raw 文件及 data.pt/pre_filter.pt/pre_transform.pt
  - 复用状态：blocked；类型：unknown
- `ROSMAP-graph-data/all-gene-edge.csv`
  - 能力：project_graph_data
  - 用途：ROSMAP 图、边表、随机生存标签与拆分文件
  - 复用状态：blocked；类型：unknown
- `UCSC-graph-data/all-gene-edge.csv`
  - 能力：project_graph_data
  - 用途：UCSC 图、边表、随机生存标签与拆分文件
  - 复用状态：blocked；类型：unknown
- `ROSMAP-analysis/avg/survival1.csv`
  - 能力：analysis_tables
  - 用途：生存分析/平均化结果 CSV，偏静态分析产物
  - 复用状态：blocked；类型：unknown

### evaluation

- `rosmap_model_comparison_table.csv`
  - 能力：result_tables
  - 用途：静态模型对比/损失结果表；未见可执行评测脚本
  - 复用状态：blocked；类型：unknown

### reusable_assets

- `maskgae/model.py`
  - 能力：model_architecture
  - 用途：定义 MaskGAE 核心模型结构
  - 复用状态：blocked；类型：code_entry
- `enc_dec/geo_gat_decoder.py`
  - 能力：decoder_variants
  - 用途：提供 GAT/GCN/GIN/GFormer 及 pretrain_gformer 解码器变体
  - 复用状态：blocked；类型：code_entry
- `load_data.py`
  - 能力：data_loading
  - 用途：读取、采样与组织图数据
  - 复用状态：blocked；类型：code_entry
- `ROSMAP_process_for_plot.ipynb`
  - 能力：analysis_visualization
  - 用途：ROSMAP 后处理、统计与可视化辅助
  - 复用状态：blocked；类型：unknown

### training

- `train_graphclas.py`
  - 能力：graph_classification_training
  - 用途：主要 graph classification 训练脚本；同目录还有 analysis/other 变体
  - 复用状态：blocked；类型：code_entry
- `geo_ROSMAP_tmain_gat.py`
  - 能力：task_specific_training
  - 用途：ROSMAP/UCSC 的 GAT/GCN/GFormer/GIN 训练入口家族
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态审查，未运行代码、未安装依赖、未执行测试。
- 未发现 LICENSE 文件，代码/数据/权重的法律复用边界无法确认。
- ROSMAP/UCSC/Cora 的来源与处理流程只能从文件名推断，不能证明可再分发。
- `MaskGAE-GraphClas*.pt` 与 `data/Cora/processed/*.pt` 仅能证明存在，不能证明训练或导出过程。
- 未见明确的独立 inference 入口。

## 仍未知

- ROSMAP/UCSC 原始数据的授权与可再分发状态未知。
- 训练脚本与各 checkpoint 的对应关系、训练配置和数据切分方式未知。
- `data/Cora/processed/*.pt` 更像 PyG 缓存或派生产物，但其生成方式未被验证。
- README.md 的具体使用说明/许可声明在当前审计元数据中不可见。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
