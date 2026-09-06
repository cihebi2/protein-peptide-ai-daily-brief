# MateeullahKhan/DeepAVP-TPPred

- **仓库：** [https://github.com/MateeullahKhan/DeepAVP-TPPred](https://github.com/MateeullahKhan/DeepAVP-TPPred)
- **固定 commit：** `8957e8aa65a81a0f61577db1bcec75d47400e5a7`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** mixed
- **资产记录数：** 11

## 仓库摘要

该仓库是 DeepAVP-TPPred 的 MATLAB 代码/数据包，主要包含 PSSM 与 LBP_SMR 特征提取、BTGA 特征选择，以及若干 AVP 数据和预计算特征；静态清单未见完整训练、推理、评估或 checkpoint 资产。

## 可复用模块与资源

### datasets

- `1_FeatureExtractionCode/data/antiviral_dataset.txt`
  - 能力：AVP main dataset
  - 用途：主 AVP 样本/标签文本数据。
  - 复用状态：blocked；类型：unknown
- `1_FeatureExtractionCode/data/AVP_Independent_1.txt`
  - 能力：AVP independent test set 1
  - 用途：独立评测集 1。
  - 复用状态：blocked；类型：unknown
- `1_FeatureExtractionCode/data/AVP_Independent_2.txt`
  - 能力：AVP independent test set 2
  - 用途：独立评测集 2。
  - 复用状态：blocked；类型：unknown
- `1_FeatureExtractionCode/data/feature_LBP_SMR_951.mat`
  - 能力：precomputed feature matrix
  - 用途：预计算的 LBP_SMR 特征矩阵。
  - 复用状态：blocked；类型：unknown
- `1_FeatureExtractionCode/data/feature_PsePSSM_951.mat`
  - 能力：precomputed feature matrix
  - 用途：预计算的 PsePSSM 特征矩阵。
  - 复用状态：blocked；类型：unknown
- `1_FeatureExtractionCode/data/features_LBP_PSSM_951.mat`
  - 能力：precomputed feature matrix
  - 用途：预计算的 LBP_PSSM 特征矩阵。
  - 复用状态：blocked；类型：unknown

### reusable_assets

- `PSSM_based_Feature_Extraction.m`
  - 能力：PSSM feature extraction
  - 用途：从 PSSM 相关输入生成序列特征，供后续筛选/分类流程使用。
  - 复用状态：blocked；类型：unknown
- `LBP_SMR_Feature_Extraction.m`
  - 能力：LBP_SMR feature extraction
  - 用途：生成 LBP_SMR / transformed image-based localized descriptors 特征。
  - 复用状态：blocked；类型：unknown
- `1_FeatureExtractionCode/lib/Read_Text_files_PSSM.m`
  - 能力：PSSM text reader
  - 用途：读取/解析 PSSM 文本输入，支撑特征提取流程。
  - 复用状态：blocked；类型：unknown
- `2_featureSelectionCode/BinaryTreeGrowthAlgorithmforFeatureSelection/jBTGA.m`
  - 能力：BTGA feature selection
  - 用途：执行 binary tree growth algorithm 的特征子集搜索。
  - 复用状态：blocked；类型：unknown
- `2_featureSelectionCode/BinaryTreeGrowthAlgorithmforFeatureSelection/jFitnessFunction.m`
  - 能力：BTGA fitness evaluation
  - 用途：为 BTGA 搜索计算适应度函数。
  - 复用状态：blocked；类型：unknown

## 使用限制

- 仅做静态清单审查，未执行代码、未安装依赖、未运行测试。
- 仓库根级 license 不存在；当前不能把代码或数据默认视为可再发布资产。
- `.mat` 文件更像预计算特征而不是模型 checkpoint。
- 未见独立的 training / inference / evaluation 入口脚本。
- 文件路径存在不代表可复现或已验证。

## 仍未知

- `3_ClassificationCode/readmi.txt` 仅显示为说明文本，未见可执行分类代码。
- 各数据文件的原始来源、拆分规则与许可条款未从静态清单中确认。
- `license.txt` 的具体条款未核对，无法确认 BTGA 子目录的精确再利用边界。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
