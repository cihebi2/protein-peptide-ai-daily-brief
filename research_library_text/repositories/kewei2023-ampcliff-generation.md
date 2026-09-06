# kewei2023/ampcliff-generation

- **仓库：** [https://github.com/kewei2023/ampcliff-generation](https://github.com/kewei2023/ampcliff-generation)
- **固定 commit：** `2bfd359e2bc09dc69724631763a5ac0a049a3d49`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 12

## 仓库摘要

仓库提供AMP cliff 生成/预处理脚本与若干内置矩阵数据；未见训练、评测或checkpoint，且当前未找到许可证边界。

## 可复用模块与资源

### datasets

- `data/blosum62.csv`
  - 能力：similarity_matrix
  - 用途：BLOSUM62 代换矩阵输入资源
  - 复用状态：blocked；类型：unknown
- `data/blosum62_normalized.csv`
  - 能力：normalized_similarity_matrix
  - 用途：归一化后的 BLOSUM62 矩阵
  - 复用状态：blocked；类型：unknown
- `data/grampa_s_aureus_7_25.csv`
  - 能力：benchmark_dataset
  - 用途：AMP cliff/活性数据的基准输入集
  - 复用状态：blocked；类型：unknown
- `data/tanimoto.csv`
  - 能力：similarity_matrix
  - 用途：Tanimoto 相似性矩阵输入资源
  - 复用状态：blocked；类型：unknown
- `data/tanimoto_normalized.csv`
  - 能力：normalized_similarity_matrix
  - 用途：归一化后的 Tanimoto 矩阵
  - 复用状态：blocked；类型：unknown

### inference

- `generate_cliffs.py`
  - 能力：code_entry
  - 用途：主 cliff 生成脚本
  - 复用状态：blocked；类型：code_entry
- `generate_cliffs.sh`
  - 能力：code_entry
  - 用途：cliff 生成的 shell 封装入口
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `environment.yaml`
  - 能力：config
  - 用途：Conda 环境依赖描述与安装约束
  - 复用状态：blocked；类型：config
- `data_partition.py`
  - 能力：data_loader
  - 用途：数据划分与预处理辅助
  - 复用状态：blocked；类型：code_entry
- `fingerprint_2d.py`
  - 能力：feature_engineering
  - 用途：SMILES/分子2D 指纹特征提取
  - 复用状态：blocked；类型：code_entry
- `similarity_matrix_normalization.py`
  - 能力：preprocessing
  - 用途：相似性矩阵归一化处理
  - 复用状态：blocked；类型：code_entry
- `grampa_show.py`
  - 能力：visualization
  - 用途：结果/数据展示脚本
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态清单审阅，未执行仓库代码。
- 依赖未安装，测试与评测未运行。
- 不存在已识别的 checkpoint 文件或训练入口。
- 路径存在不等于可复现或可直接复用。

## 仍未知

- cpp_smiles.json 的具体用途未能从冻结清单确认。
- 各 CSV 的原始来源与授权条款未从静态清单中建立。
- generate_cliffs.py 是否需要外部输入文件或网络资源无法确认。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
