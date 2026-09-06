# ak422/CATH-ddG

- **仓库：** [https://github.com/ak422/CATH-ddG](https://github.com/ak422/CATH-ddG)
- **固定 commit：** `500117a1896875890cdd3b4e5611ea11e357b79d`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 31

## 仓库摘要

仓库静态展示了 CATH-ddG 论文相关的代码、数据切分、训练/推理配置、评估脚本与若干已训练权重；但未发现显式 LICENSE，且未执行代码或测试，因此只能给出静态可复用性与边界判断，不能证明可复现。

## 可复用模块与资源

### checkpoints

- `trained_models/CATH_model_0.pt`
  - 能力：CATH ensemble 权重
  - 用途：CATH 模型权重之一
  - 复用状态：unknown；类型：model_weight
- `trained_models/CATH_model_1.pt`
  - 能力：CATH ensemble 权重
  - 用途：CATH 模型权重之一
  - 复用状态：unknown；类型：model_weight
- `trained_models/CATH_model_2.pt`
  - 能力：CATH ensemble 权重
  - 用途：CATH 模型权重之一
  - 复用状态：unknown；类型：model_weight
- `trained_models/PPIFORMER.pt`
  - 能力：PPIformer 权重
  - 用途：PPIformer 基线/比较模型权重
  - 复用状态：unknown；类型：model_weight
- `trained_models/case_study.pt`
  - 能力：case study 权重
  - 用途：案例研究模型权重
  - 复用状态：unknown；类型：model_weight

### datasets

- `data/SKEMPI2/skempi_v2.csv`
  - 能力：SKEMPI2 主表
  - 用途：突变效应数据主集
  - 复用状态：unknown；类型：unknown
- `data/SKEMPI2/skempi_v2_cache/skempi_v2.csv`
  - 能力：SKEMPI2 缓存副本
  - 用途：缓存化的数据副本
  - 复用状态：unknown；类型：unknown
- `data/SKEMPI2/skempi_v2_with_all_results.csv`
  - 能力：SKEMPI2 汇总结果表
  - 用途：聚合后的实验结果/预测结果表
  - 复用状态：unknown；类型：unknown
- `data/SKEMPI2/HER2.csv`
  - 能力：HER2 子集
  - 用途：HER2 case study 子集
  - 复用状态：unknown；类型：unknown
- `data/SKEMPI2/HER2_PDBs/1N8Z.pdb`
  - 能力：HER2 结构文件
  - 用途：HER2 子集的结构输入
  - 复用状态：unknown；类型：unknown
- `data/SKEMPI2/S285.csv`
  - 能力：S285 子集
  - 用途：S285 case study 子集
  - 复用状态：unknown；类型：unknown
- `data/SKEMPI2/S285_PDBs/6M0J.pdb`
  - 能力：S285 结构文件
  - 用途：S285 子集的结构输入
  - 复用状态：unknown；类型：unknown
- `data/SKEMPI2/zero_domain_foldseek.csv`
  - 能力：Foldseek 派生特征
  - 用途：零域/结构域相关派生特征
  - 复用状态：unknown；类型：unknown

### evaluation

- `test_DDAffinity.py`
  - 能力：测试脚本
  - 用途：静态测试/回归检查入口
  - 复用状态：blocked；类型：code_entry
- `DDAffinity/linear/calibrate.py`
  - 能力：校准评估
  - 用途：后验校准与分数评估
  - 复用状态：blocked；类型：code_entry
- `DDAffinity/linear/entropy.py`
  - 能力：不确定性/熵分析
  - 用途：熵相关的评估或分析
  - 复用状态：blocked；类型：code_entry

### inference

- `case_study.py`
  - 能力：案例推理入口
  - 用途：对 HER2/S285 等案例执行推理与结果输出
  - 复用状态：blocked；类型：code_entry
- `configs/inference/case_study_HER2.yml`
  - 能力：推理配置
  - 用途：HER2 推理参数与路径配置
  - 复用状态：blocked；类型：config
- `configs/inference/case_study_S285.yml`
  - 能力：推理配置
  - 用途：S285 推理参数与路径配置
  - 复用状态：blocked；类型：config

### reusable_assets

- `DDAffinity/models/DDAffinity.py`
  - 能力：主模型结构
  - 用途：定义 CATH-ddG 的核心网络，用于蛋白-蛋白相互作用突变效应预测
  - 复用状态：blocked；类型：code_entry
- `DDAffinity/models/transfer_model.py`
  - 能力：迁移/封装模型
  - 用途：提供迁移学习或推断封装逻辑
  - 复用状态：blocked；类型：code_entry
- `DDAffinity/datasets/build_mutant_skempi.py`
  - 能力：突变数据构建
  - 用途：从 SKEMPI2 组装突变样本与训练/评估输入
  - 复用状态：blocked；类型：code_entry
- `DDAffinity/datasets/build_mutant_case.py`
  - 能力：案例数据构建
  - 用途：构建 case study 所需的突变输入
  - 复用状态：blocked；类型：code_entry
- `train_DDAffinity.py`
  - 能力：训练入口
  - 用途：主训练脚本入口
  - 复用状态：blocked；类型：code_entry
- `case_study.py`
  - 能力：案例推理脚本
  - 用途：面向 HER2/S285 的案例推理与结果汇总
  - 复用状态：blocked；类型：code_entry
- `DDAffinity/linear/calibrate.py`
  - 能力：校准/后处理
  - 用途：线性校准与分数后处理
  - 复用状态：blocked；类型：code_entry

### training

- `train_DDAffinity.py`
  - 能力：主训练入口
  - 用途：训练主模型与实验配置调度
  - 复用状态：blocked；类型：code_entry
- `configs/train/CATH.yml`
  - 能力：训练配置
  - 用途：CATH 模型训练超参数与数据路径配置
  - 复用状态：blocked；类型：config
- `configs/train/PPIformer.yml`
  - 能力：训练配置
  - 用途：PPIformer 相关训练配置
  - 复用状态：blocked；类型：config
- `configs/train/Case_study.yml`
  - 能力：训练配置
  - 用途：case study 训练/微调配置
  - 复用状态：blocked；类型：config
- `DDAffinity/utils/train_mpnn.py`
  - 能力：训练辅助模块
  - 用途：训练循环与优化辅助
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态清点，未执行仓库代码、依赖安装或测试。
- path presence 不能证明训练、推理或复现实验真的成功。
- 未见显式 LICENSE，代码/权重的直接复用受限。
- SKEMPI2、PDB 和派生 CSV 的上游来源与许可边界未核验。
- data/esm2_t33_650M_UR50D 仅见 .gitkeep，占位目录不代表实际权重已提供。

## 仍未知

- train_DDAffinity.py 实际采用的训练数据划分、超参数和随机种子未知。
- case_study.py 与两个 inference YAML 的完整执行链未知。
- trained_models/*.pt 是否都能在当前环境加载未知。
- DDAffinity/models/protein_mpnn_utils.py 等支持代码的上游来源是否为 vendored third-party 未核验。
- data/SKEMPI2/skempi_v2_with_all_results.csv 是人工汇总结果还是自动生成结果，静态证据不足。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
