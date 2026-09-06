# wan-mlab/samp

- **仓库：** [https://github.com/wan-mlab/samp](https://github.com/wan-mlab/samp)
- **固定 commit：** `2b17ff863ca9fbec5c6190062819a6e9c7d2e5a4`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 9

## 仓库摘要

仓库是 SAMP 的静态参考实现：可见模型/特征/评估辅助代码与训练、独立测试数据，但没有训练入口、独立推理脚本或 checkpoint；同时未发现 LICENSE，外部复用边界不清。

## 可复用模块与资源

### datasets

- `Training_Dataset/iAMPpred_pos_fasta.txt`
  - 能力：training_dataset
  - 用途：训练集正负样本集合；清单中可见 iAMPpred_pos_fasta.txt 与 iAMPpred_neg_fasta.txt。
  - 复用状态：blocked；类型：unknown
- `Independent_Dataset/amphibian_Negative.txt`
  - 能力：independent_evaluation_dataset
  - 用途：独立测试/外部验证数据；清单中可见 amphibian、bacteria、human、plant 的正负样本及 combined_* 文件。
  - 复用状态：blocked；类型：unknown

### evaluation

- `SAMP/_evaluation.py`
  - 能力：evaluation_support
  - 用途：评估辅助函数；未见独立推理或批量验证入口。
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `SAMP/_model.py`
  - 能力：model_architecture
  - 用途：模型主体定义，按文件名与仓库主题判断为 SAMP 二分类器核心。
  - 复用状态：blocked；类型：code_entry
- `SAMP/_feature.py`
  - 能力：feature_engineering
  - 用途：特征构造辅助模块；很可能服务于 proportionalized split amino acid composition。
  - 复用状态：blocked；类型：code_entry
- `buildFeatures.R`
  - 能力：feature_engineering
  - 用途：R 侧特征生成/预处理脚本。
  - 复用状态：blocked；类型：code_entry
- `SAMP/_evaluation.py`
  - 能力：evaluation_support
  - 用途：评估辅助函数；未见独立测试脚本或命令行评测入口。
  - 复用状态：blocked；类型：code_entry
- `setup.py`
  - 能力：packaging
  - 用途：安装/打包元数据。
  - 复用状态：blocked；类型：code_entry
- `environment.yml`
  - 能力：environment_spec
  - 用途：Conda 环境依赖声明。
  - 复用状态：blocked；类型：config

## 使用限制

- 仅做静态清单审查，未执行仓库代码、未运行测试、未安装依赖。
- 未发现训练入口、推理脚本或 checkpoint，因此无法确认可复现训练/推理流程。
- 数据集用途主要依据目录名与文件名推断，未核对文件内容。
- 仓库未见 LICENSE 文件，代码和数据的再利用边界不明确。

## 仍未知

- SAMP/_model.py 的具体网络结构与是否包含训练逻辑无法仅凭清单确认。
- _feature.py、_evaluation.py、buildFeatures.R 之间的调用关系未确认。
- Tutorial.ipynb 与 test_version1.ipynb 是否承载实验、评测或教程流程未确认。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
