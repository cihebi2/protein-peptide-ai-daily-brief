# 1705004/Pair-EGRET

- **仓库：** [https://github.com/1705004/Pair-EGRET](https://github.com/1705004/Pair-EGRET)
- **固定 commit：** `44a243ec8f034e8c006f50037c7f562793b15513`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 11

## 仓库摘要

这是 Pair-EGRET 的静态实现仓库，核心是蛋白-蛋白相互作用位点预测的图注意力网络与特征生成管线；盘点到数据加载、特征生成和推理脚本，但未见训练入口、评估脚本或 checkpoint，且缺少许可证文件。

## 可复用模块与资源

### datasets

- `inputs/dbd5/proteins.txt`
  - 能力：benchmark_manifest
  - 用途：DBD5 蛋白清单与样本规模统计
  - 复用状态：blocked；类型：unknown
- `inputs/dockground/proteins.txt`
  - 能力：benchmark_manifest
  - 用途：Dockground 蛋白清单与样本规模统计
  - 复用状态：blocked；类型：unknown
- `inputs/masif/proteins.txt`
  - 能力：benchmark_manifest
  - 用途：MaSIF 蛋白清单与样本规模统计
  - 复用状态：blocked；类型：unknown
- `inputs/hydro.json`
  - 能力：residue_hydrophobicity_table
  - 用途：残基疏水性查表资源
  - 复用状态：blocked；类型：config
- `inputs/residue_phychem_data.json`
  - 能力：residue_physicochemical_table
  - 用途：残基理化性质查表资源
  - 复用状态：blocked；类型：config

### inference

- `generate_all_features.py`
  - 能力：feature_generation_inference
  - 用途：生成推理所需的全套特征输入
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `models/Pair_EGRET.py`
  - 能力：model_architecture
  - 用途：Pair-EGRET 主模型封装与前向组合逻辑
  - 复用状态：blocked；类型：code_entry
- `models/EdgeAggregatedGAT_attention_visual.py`
  - 能力：graph_attention_module
  - 用途：边聚合 GAT / attention 组件及可视化相关实现
  - 复用状态：blocked；类型：code_entry
- `data_generator_attention_visual.py`
  - 能力：data_loader
  - 用途：生成训练/推理批次与输入张量
  - 复用状态：blocked；类型：code_entry
- `feature_generation/ProtBERT_feature_generator.py`
  - 能力：feature_generation_pipeline
  - 用途：生成 ProtBERT、ProtXLNet、距离/角度、疏水性、理化和残基可及性特征
  - 复用状态：blocked；类型：code_entry
- `requirements.txt`
  - 能力：environment_spec
  - 用途：记录 Python 依赖边界
  - 复用状态：blocked；类型：unknown

## 使用限制

- 仅做静态盘点，未执行代码、未安装依赖。
- 未发现训练入口/训练模块；`run_egret.py` 的具体角色未被冻结盘点确认。
- 未发现评估脚本或模型 checkpoint；`.pkl` 文件更像数据规模统计而非权重。
- 数据文件更像清单与特征表，原始基准集来源未核实。
- 缺少许可证文件，直接复用受限。

## 仍未知

- `inputs/*` 是否为外部基准集的派生物或仓库自建资源，未能从冻结清单确认。
- `run_egret.py` 是否承担训练、评估或推理入口，静态盘点未分类。
- 是否存在被 LFS/大文件过滤遗漏的权重或其他资产，无法确认。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
