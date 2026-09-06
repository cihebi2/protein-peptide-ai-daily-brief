# cschen-y/mvrbind

- **仓库：** [https://github.com/cschen-y/mvrbind](https://github.com/cschen-y/mvrbind)
- **固定 commit：** `067ec410d941eeed43a2e19fd830f4ad864a0eef`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 15

## 仓库摘要

这是一个面向 RNA-small molecule binding site prediction 的静态仓库复核：包含数据预处理、MSA/结构特征构建、模型定义、训练与推理脚本，以及若干 processed `.pt` 缓存和 `model.pt` 权重；未发现独立许可证文件，直接复用受限。

## 可复用模块与资源

### checkpoints

- `model_parameters/model.pt`
  - 能力：model_weight
  - 用途：训练后保存的主模型参数文件。
  - 复用状态：unknown；类型：model_weight
- `pt/kop8/processed/data_test.pt`
  - 能力：checkpoint_adjacent_cache
  - 用途：PyTorch 预处理数据缓存；属于输入缓存，不是可训练权重。
  - 复用状态：blocked；类型：model_weight

### datasets

- `data_process/data/fasta/2JUKA.fasta`
  - 能力：raw_example_input
  - 用途：RNA 序列示例输入；与 `data_process/data/pdb/2JUKA.pdb`、`data_process/data/msa/2JUKA_msa.fasta` 共同构成单样本演示数据。
  - 复用状态：unknown；类型：unknown
- `data_process/data/secondary_structure/2JUK/dssr-nc_visualization-hybrid-pseudoknots_as_paired_residues-varna/2JUK-elements.pdb`
  - 能力：derived_secondary_structure_bundle
  - 用途：二级结构派生与可视化文件集合（csv/pdb/txt/pdf/png/svg），用于结构特征整理。
  - 复用状态：blocked；类型：unknown
- `data_process/RCSB_all.csv`
  - 能力：dataset_index
  - 用途：样本/条目索引表，疑似用于组织 RCSB 来源记录。
  - 复用状态：unknown；类型：unknown

### evaluation

- `data_process/test_18_dataset.py`
  - 能力：dataset_smoke_test
  - 用途：仅见数据集连通性/单元测试，没有独立 benchmark 评测流程。
  - 复用状态：blocked；类型：code_entry

### inference

- `predict.py`
  - 能力：inference_entrypoint
  - 用途：通用推理入口，用于加载模型并输出预测。
  - 复用状态：blocked；类型：code_entry
- `predict_binding_site.py`
  - 能力：binding_site_inference
  - 用途：面向结合位点的推理/打分脚本。
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `model.py`
  - 能力：model_architecture
  - 用途：核心多视图模型结构定义，用于 RNA-小分子结合位点打分/分类。
  - 复用状态：blocked；类型：code_entry
- `data_process/msa.py`
  - 能力：msa_feature_extraction
  - 用途：生成 MSA 特征并喂给下游模型。
  - 复用状态：blocked；类型：code_entry
- `data_process/set_graph.py`
  - 能力：graph_construction
  - 用途：把序列/结构特征组装成图输入。
  - 复用状态：blocked；类型：code_entry
- `environment.yml`
  - 能力：environment_config
  - 用途：Conda/依赖环境定义，支撑本地安装与复现。
  - 复用状态：blocked；类型：config
- `clustalw/clustalw2`
  - 能力：alignment_backend
  - 用途：MSA 外部对齐程序，被预处理流水线调用。
  - 复用状态：unknown；类型：unknown

### training

- `train.py`
  - 能力：training_entrypoint
  - 用途：训练主入口，负责调用数据加载、优化与模型保存。
  - 复用状态：blocked；类型：code_entry
- `data_process/train_dataset.py`
  - 能力：training_dataset_builder
  - 用途：训练样本构建与划分逻辑。
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态复核，未运行仓库代码。
- 依赖未安装，无法验证 environment.yml 是否可复现。
- 未见独立 LICENSE，直接复用受限。
- 仅凭路径无法确认 `model.pt`、`pt/*/processed/*.pt` 的真实训练/生成来源。
- 未见正式 benchmark 评测脚本或外部结果文件。

## 仍未知

- `data_process/RCSB_all.csv` 与 `2JUKA` 相关输入是否全部来自公开数据库，静态清单无法确认。
- `model_parameters/model.pt` 是否为论文最终权重还是示例权重，不确定。
- `clustalw/clustalw2` 是否为完整 vendored binary 以及其许可证，不确定。
- `pt/*/processed/*.pt` 更偏训练缓存还是中间检查点，静态清单无法区分。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
