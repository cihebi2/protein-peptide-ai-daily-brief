# fuyw-aisw/GALA

- **仓库：** [https://github.com/fuyw-aisw/GALA](https://github.com/fuyw-aisw/GALA)
- **固定 commit：** `d8de87b78dada61c7236fb6f6df8fd05c31cfe00`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 37

## 仓库摘要

该冻结仓库看起来是 GALA 的蛋白功能预测实现快照：包含模型结构、训练/推理/评估脚本、若干 GO 相关数据切分、Ontology/统计文件和 6 个 `.pt` 权重。代码许可证为 MIT，但数据与权重未见独立许可边界，静态库存不足以证明可直接复现或重跑。

## 可复用模块与资源

### checkpoints

- `sortedmodel/model_bpsort_by_id_bp.pt`
  - 能力：checkpoint
  - 用途：BP 分支的已训练权重。
  - 复用状态：partial；类型：model_weight
- `sortedmodel/model_bpsort_by_id_bp_AF2.pt`
  - 能力：checkpoint
  - 用途：BP 分支的 AF2 变体权重。
  - 复用状态：partial；类型：model_weight
- `sortedmodel/model_ccsort_by_id_cc.pt`
  - 能力：checkpoint
  - 用途：CC 分支的已训练权重。
  - 复用状态：partial；类型：model_weight
- `sortedmodel/model_ccsort_by_id_cc_AF2.pt`
  - 能力：checkpoint
  - 用途：CC 分支的 AF2 变体权重。
  - 复用状态：partial；类型：model_weight
- `sortedmodel/model_mfsort_by_id_mf.pt`
  - 能力：checkpoint
  - 用途：MF 分支的已训练权重。
  - 复用状态：partial；类型：model_weight
- `sortedmodel/model_mfsort_by_id_mf_AF2.pt`
  - 能力：checkpoint
  - 用途：MF 分支的 AF2 变体权重。
  - 复用状态：partial；类型：model_weight

### datasets

- `data/nrPDB-GO_2019.06.18_sequences.fasta`
  - 能力：dataset
  - 用途：nrPDB-GO 蛋白序列语料/特征输入。
  - 复用状态：partial；类型：unknown
- `data/nrPDB-GO_2019.06.18_annot.tsv`
  - 能力：dataset
  - 用途：nrPDB-GO 注释表，保存 GO 标签对齐信息。
  - 复用状态：partial；类型：unknown
- `data/nrPDB-GO_2019.06.18_train_sequences.fasta`
  - 能力：dataset
  - 用途：nrPDB-GO 训练切分。
  - 复用状态：partial；类型：unknown
- `data/nrPDB-GO_2019.06.18_val_sequences.fasta`
  - 能力：dataset
  - 用途：nrPDB-GO 验证切分。
  - 复用状态：partial；类型：unknown
- `data/nrPDB-GO_2019.06.18_test_sequences.fasta`
  - 能力：dataset
  - 用途：nrPDB-GO 测试切分。
  - 复用状态：partial；类型：unknown
- `data/nrSwiss-Model-GO_sequences.fasta`
  - 能力：dataset
  - 用途：nrSwiss-Model-GO 蛋白序列语料/输入。
  - 复用状态：partial；类型：unknown
- `data/nrSwiss-Model-GO_annot.tsv`
  - 能力：dataset
  - 用途：nrSwiss-Model-GO 注释表。
  - 复用状态：partial；类型：unknown
- `data/nrAF-Model-GO_train_sequences.fasta`
  - 能力：dataset
  - 用途：nrAF-Model-GO 训练切分。
  - 复用状态：partial；类型：unknown
- `data/nrAF-Model-GO_val_sequences.fasta`
  - 能力：dataset
  - 用途：nrAF-Model-GO 验证切分。
  - 复用状态：partial；类型：unknown
- `data/nrAF-Model-GO_test_sequences.fasta`
  - 能力：dataset
  - 用途：nrAF-Model-GO 测试切分。
  - 复用状态：partial；类型：unknown
- `data/AFch/train_AFch.txt`
  - 能力：dataset
  - 用途：AFch 训练清单/切分文本。
  - 复用状态：partial；类型：unknown
- `data/AFch/val_AFch.txt`
  - 能力：dataset
  - 用途：AFch 验证清单/切分文本。
  - 复用状态：partial；类型：unknown
- `data/AFch/test_AFch.txt`
  - 能力：dataset
  - 用途：AFch 测试清单/切分文本。
  - 复用状态：partial；类型：unknown
- `data/PDBch/train_PDBch.txt`
  - 能力：dataset
  - 用途：PDBch 训练清单/切分文本。
  - 复用状态：partial；类型：unknown
- `data/PDBch/val_PDBch.txt`
  - 能力：dataset
  - 用途：PDBch 验证清单/切分文本。
  - 复用状态：partial；类型：unknown
- `data/PDBch/test_PDBch.txt`
  - 能力：dataset
  - 用途：PDBch 测试清单/切分文本。
  - 复用状态：partial；类型：unknown
- `data/go-basic.obo`
  - 能力：dataset
  - 用途：GO ontology 基础文件，供标签/层级解析。
  - 复用状态：unknown；类型：unknown
- `data/ic_count.pkl`
  - 能力：dataset
  - 用途：信息内容/频次统计缓存。
  - 复用状态：partial；类型：unknown
- `data/SourceData.zip`
  - 能力：dataset
  - 用途：原始源数据打包归档。
  - 复用状态：unknown；类型：unknown
- `data/1P4U-A.pdb`
  - 能力：dataset
  - 用途：蛋白结构 PDB 示例/输入文件。
  - 复用状态：unknown；类型：unknown

### evaluation

- `evaluation_matrics.py`
  - 能力：evaluation_script
  - 用途：评估指标计算脚本。
  - 复用状态：ready_for_review；类型：code_entry
- `test.py`
  - 能力：evaluation_script
  - 用途：测试/评估驱动脚本，可能串联 checkpoint 推理与指标计算。
  - 复用状态：ready_for_review；类型：code_entry

### inference

- `predictor.py`
  - 能力：inference_entrypoint
  - 用途：推理/预测入口；从命名看可能加载 sortedmodel/*.pt 输出功能预测。
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `network.py`
  - 能力：model_architecture
  - 用途：核心模型结构实现，负责图/Transformer 风格前向计算的主体组织。
  - 复用状态：ready_for_review；类型：code_entry
- `graph_data.py`
  - 能力：data_processing
  - 用途：图数据构造、样本读入或批处理辅助模块。
  - 复用状态：ready_for_review；类型：code_entry
- `pool.py`
  - 能力：model_component
  - 用途：pooling/readout 组件。
  - 复用状态：ready_for_review；类型：code_entry
- `nt_xent.py`
  - 能力：training_component
  - 用途：对比学习损失或 NT-Xent 辅助实现。
  - 复用状态：ready_for_review；类型：code_entry
- `utils.py`
  - 能力：utility
  - 用途：通用工具函数，可能被训练/推理/评估共享。
  - 复用状态：ready_for_review；类型：code_entry
- `Dockerfile`
  - 能力：environment
  - 用途：容器化运行环境定义。
  - 复用状态：ready_for_review；类型：unknown
- `environment.yml`
  - 能力：environment
  - 用途：conda 环境与依赖版本描述。
  - 复用状态：ready_for_review；类型：config

### training

- `train.py`
  - 能力：training_entrypoint
  - 用途：训练主入口；从命名看应组织数据加载、模型、损失与优化过程。
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态清单审查，未执行代码、未安装依赖、未运行测试。
- 路径存在不等于可复现或可重训；checkpoint 和数据来源未验证。
- 数据与权重未见独立许可证或 provenance 说明，复用边界需要额外核验。
- 仓库中可能存在可下载/派生资源，但此审查只基于冻结清单。

## 仍未知

- `predictor.py` 与 `test.py` 的实际运行分工未通过执行确认。
- `SourceData.zip`、`ic_count.pkl`、`go-basic.obo`、`1P4U-A.pdb` 的具体来源与许可未核验。
- 6 个 `.pt` 权重是否由 `train.py` 直接训练得到、还是部分导入/再打包，未验证。
- 训练超参数、数据预处理细节与指标实现细节未从静态库存中完全确认。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
