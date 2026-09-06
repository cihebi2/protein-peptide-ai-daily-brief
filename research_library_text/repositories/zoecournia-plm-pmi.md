# zoecournia/plm-pmi

- **仓库：** [https://github.com/zoecournia/plm-pmi](https://github.com/zoecournia/plm-pmi)
- **固定 commit：** `c37747e2a1f96fa52ba3c1fba7f7583624a9f00b`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0
- **资产记录数：** 17

## 仓库摘要

仓库主要提供蛋白-膜界面预测的数据整理、训练产物与可视化脚本；已见 GPL-3.0 代码许可，但数据与模型许可边界未被静态证实。

## 可复用模块与资源

### checkpoints

- `models/best_model_esm/saved_model.pb`
  - 能力：TensorFlow SavedModel（ESM）
  - 用途：ESM 特征下的最佳模型权重与变量。
  - 复用状态：partial；类型：model_weight
- `models/best_model_protTrans/saved_model.pb`
  - 能力：TensorFlow SavedModel（ProtTrans）
  - 用途：ProtTrans 特征下的最佳模型权重与变量。
  - 复用状态：partial；类型：model_weight
- `models/lgbm_model_pdb_esm.pkl`
  - 能力：LightGBM 模型（PDB/ESM）
  - 用途：PDB/ESM 特征的 LightGBM 训练产物。
  - 复用状态：partial；类型：unknown
- `models/lgbm_model_pdb_protTrans.pkl`
  - 能力：LightGBM 模型（PDB/ProtTrans）
  - 用途：PDB/ProtTrans 特征的 LightGBM 训练产物。
  - 复用状态：partial；类型：unknown

### datasets

- `Datasets/PDB_dataset/all_pdb.fasta`
  - 能力：PDB 数据集 bundle
  - 用途：PDB 来源的全量/过滤集、DREAMM 子集、CD-HIT 结果与派生 CSV/FASTA。
  - 复用状态：partial；类型：unknown
- `Datasets/Uniprot_dataset/uniprot_proteins.json`
  - 能力：UniProt 数据集 bundle
  - 用途：UniProt 蛋白、序列、聚类/对齐、拆分与膜面残基注释。
  - 复用状态：partial；类型：config
- `Datasets/dreamm.json`
  - 能力：DREAMM 元数据/目标
  - 用途：DREAMM 相关目标或样本元数据。
  - 复用状态：partial；类型：config
- `extra_proteins/proteins.json`
  - 能力：补充蛋白列表
  - 用途：补充蛋白条目/ID 列表。
  - 复用状态：partial；类型：config

### inference

- `scripts/generate_pymol.py`
  - 能力：PyMOL 可视化脚本生成
  - 用途：把预测/结构结果转成 PyMOL 脚本。
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `scripts/dataset-pdb.py`
  - 能力：数据集构建与过滤
  - 用途：构建/清洗 PDB 数据集并输出 CSV/FASTA 中间文件。
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/get_proteins.py`
  - 能力：蛋白抓取与整理
  - 用途：获取/整理蛋白条目，支撑 UniProt/PDB 数据准备。
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/pairwise_seq_ident.py`
  - 能力：序列相似度计算
  - 用途：计算 pairwise sequence identity，用于聚类与去冗余。
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/examine_new_proteins.py`
  - 能力：新蛋白检查
  - 用途：检查新增蛋白条目及其预测/注释结果。
  - 复用状态：ready_for_review；类型：code_entry
- `requirement.txt`
  - 能力：运行环境依赖清单
  - 用途：列出 Python 依赖，辅助环境重建。
  - 复用状态：partial；类型：unknown
- `scripts/pymol_template.txt`
  - 能力：PyMOL 脚本模板
  - 用途：与 generate_pymol.py 配合生成可视化脚本。
  - 复用状态：ready_for_review；类型：unknown

### training

- `scripts/ml_tune.ipynb`
  - 能力：超参调优/训练探索 notebook
  - 用途：模型调参与实验探索；未见独立训练入口。
  - 复用状态：partial；类型：unknown
- `scripts/embeddings_lm.ipynb`
  - 能力：语言模型嵌入生成 notebook
  - 用途：生成蛋白语言模型嵌入，供下游训练/推理使用。
  - 复用状态：partial；类型：unknown

## 使用限制

- 仅做静态清单审核，未执行代码、测试或模型加载。
- 依赖未安装，submodules 未初始化。
- 大文件可能受 promisor/LFS 限制，静态存在不代表内容完整可读。
- 路径存在不等于训练或推理可复现。

## 仍未知

- 未见独立训练入口；scripts/ml_tune.ipynb 与 scripts/embeddings_lm.ipynb 是否覆盖全部训练流程无法确认。
- 未见固定评测脚本或 benchmark 流程，结果复现性无法静态证明。
- 数据集与模型文件缺少独立许可说明，PDB/UniProt/DREAMM 及导出模型的再利用边界不明。
- SavedModel 与 pkl 产物是否对应论文最终版本、以及是否与 README 叙述一致，均无法仅凭静态清单确认。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
