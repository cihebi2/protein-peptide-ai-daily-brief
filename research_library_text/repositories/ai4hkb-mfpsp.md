# AI4HKB/MFPSP

- **仓库：** [https://github.com/AI4HKB/MFPSP](https://github.com/AI4HKB/MFPSP)
- **固定 commit：** `8f7724a87847c4d6ab617af2f9152f638473bf66`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 18

## 仓库摘要

静态清单显示该仓库是一个围绕 fungal phosphorylation site 预测的特征工程与推理包：包含 AAC、BINARY、CTDC、EAAC、PAAC、QSOrder、Embedding_features 等序列编码脚本，feature_combine.py 负责特征融合，predict.py 提供推理入口；数据侧只有 datasets.rar、sacch_s_testing.fasta、若干描述子文本表和 test_output.csv 样例输出。未发现可核验的训练入口、独立评估脚本或正式 checkpoint；`model/model.txt` 仅能视为文本型模型相关工件，未证实为可加载权重。

## 可复用模块与资源

### datasets

- `datasets/datasets.rar`
  - 能力：bundled_dataset_archive
  - 用途：打包数据集归档；未解包，具体内容不可静态确认
  - 复用状态：blocked；类型：unknown
- `MFPSP-master/data/CTD.txt`
  - 能力：descriptor_reference_table
  - 用途：CTD 特征参考表；代码树下还有同名镜像副本
  - 复用状态：blocked；类型：unknown
- `MFPSP-master/data/Grantham.txt`
  - 能力：descriptor_reference_table
  - 用途：Grantham 特征参考表；代码树下还有同名镜像副本
  - 复用状态：blocked；类型：unknown
- `MFPSP-master/data/PAAC.txt`
  - 能力：descriptor_reference_table
  - 用途：PAAC 特征参考表；代码树下还有同名镜像副本
  - 复用状态：blocked；类型：unknown
- `MFPSP-master/data/Schneider-Wrede.txt`
  - 能力：descriptor_reference_table
  - 用途：Schneider-Wrede 特征参考表；代码树下还有同名镜像副本
  - 复用状态：blocked；类型：unknown

### evaluation

- `MFPSP-master/results/test_output.csv`
  - 能力：static_prediction_output
  - 用途：静态预测输出样例；未见独立 metric 计算脚本
  - 复用状态：blocked；类型：unknown

### inference

- `MFPSP-master/feature_scripts/predict.py`
  - 能力：sequence_classification_inference
  - 用途：对输入序列执行 phosphorylation site 预测
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `MFPSP-master/MFPSP.py`
  - 能力：pipeline_orchestration
  - 用途：仓库级主流程脚本/包装入口，静态清单未进一步解析其调用链
  - 复用状态：unknown；类型：code_entry
- `MFPSP-master/feature_scripts/AAC.py`
  - 能力：feature_extraction
  - 用途：AAC 序列特征编码
  - 复用状态：blocked；类型：code_entry
- `MFPSP-master/feature_scripts/BINARY.py`
  - 能力：feature_extraction
  - 用途：氨基酸二值编码
  - 复用状态：blocked；类型：code_entry
- `MFPSP-master/feature_scripts/CTDC.py`
  - 能力：feature_extraction
  - 用途：CTD 组成特征构建
  - 复用状态：blocked；类型：code_entry
- `MFPSP-master/feature_scripts/EAAC.py`
  - 能力：feature_extraction
  - 用途：enhanced AAC（滑窗/扩展 AAC）编码
  - 复用状态：blocked；类型：code_entry
- `MFPSP-master/feature_scripts/Embedding_features.py`
  - 能力：feature_extraction
  - 用途：embedding-based 序列特征构建
  - 复用状态：blocked；类型：code_entry
- `MFPSP-master/feature_scripts/PAAC.py`
  - 能力：feature_extraction
  - 用途：pseudo AAC 特征构建
  - 复用状态：blocked；类型：code_entry
- `MFPSP-master/feature_scripts/QSOrder.py`
  - 能力：feature_extraction
  - 用途：sequence-order 特征构建
  - 复用状态：blocked；类型：code_entry
- `MFPSP-master/feature_scripts/feature_combine.py`
  - 能力：feature_fusion
  - 用途：多类特征拼接与融合
  - 复用状态：blocked；类型：code_entry
- `MFPSP-master/feature_scripts/readFasta.py`
  - 能力：fasta_io
  - 用途：FASTA 读取/校验/保存配套工具（与 checkFasta.py、sequence_read_save.py 协同）
  - 复用状态：blocked；类型：code_entry
- `MFPSP-master/model/model.txt`
  - 能力：model_artifact
  - 用途：模型目录中的文本型模型/参数相关工件；静态清单未证实其为可加载 checkpoint
  - 复用状态：unknown；类型：unknown

## 使用限制

- 仅做静态清点，未执行任何脚本、训练或测试。
- 依赖未安装，无法验证 predict.py 与特征脚本的实际行为。
- 大文件/压缩包未解包，数据集内容只能按路径推断。
- 仓库级 license 缺失，直接复用边界不成立。

## 仍未知

- `MFPSP-master/model/model.txt` 是否为可加载 checkpoint 仍不明确。
- `datasets/datasets.rar` 内含数据规模、样本标签与来源未核验。
- `feature_scripts/data/*.txt` 与 `data/*.txt` 是否为同一份外部描述子表的镜像副本未核验。
- `MFPSP-master/MFPSP.py` 的具体角色（主入口还是包装脚本）未从静态清单确认。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
