# encryptional/sofb

- **仓库：** [https://github.com/encryptional/sofb](https://github.com/encryptional/sofb)
- **固定 commit：** `2a421e81478af0db662edfa353635f654744cf33`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 30

## 仓库摘要

该仓库是DNA/RNA结合残基预测的推理型模型包，含多特征脚本、数据拆分文件与H5权重，但未见训练/评测入口且缺少许可证。

## 可复用模块与资源

### checkpoints

- `save_model/DNA/0.h5`
  - 能力：DNA model weight
  - 用途：DNA 模型权重文件，疑似 ensemble 成员之一
  - 复用状态：blocked；类型：model_weight
- `save_model/DNA/1.h5`
  - 能力：DNA model weight
  - 用途：DNA 模型权重文件，疑似 ensemble 成员之一
  - 复用状态：blocked；类型：model_weight
- `save_model/DNA/2.h5`
  - 能力：DNA model weight
  - 用途：DNA 模型权重文件，疑似 ensemble 成员之一
  - 复用状态：blocked；类型：model_weight
- `save_model/DNA/3.h5`
  - 能力：DNA model weight
  - 用途：DNA 模型权重文件，疑似 ensemble 成员之一
  - 复用状态：blocked；类型：model_weight
- `save_model/RNA/0.h5`
  - 能力：RNA model weight
  - 用途：RNA 模型权重文件，疑似 ensemble 成员之一
  - 复用状态：blocked；类型：model_weight
- `save_model/RNA/1.h5`
  - 能力：RNA model weight
  - 用途：RNA 模型权重文件，疑似 ensemble 成员之一
  - 复用状态：blocked；类型：model_weight
- `save_model/RNA/2.h5`
  - 能力：RNA model weight
  - 用途：RNA 模型权重文件，疑似 ensemble 成员之一
  - 复用状态：blocked；类型：model_weight
- `save_model/RNA/3.h5`
  - 能力：RNA model weight
  - 用途：RNA 模型权重文件，疑似 ensemble 成员之一
  - 复用状态：blocked；类型：model_weight
- `save_model/RNA/RNA_0.h5`
  - 能力：RNA model weight
  - 用途：额外的 RNA 权重变体；仅凭静态清单无法判断其与 `0.h5-3.h5` 的关系
  - 复用状态：blocked；类型：model_weight

### datasets

- `Datasets/DNA/DNA-573_Train.txt`
  - 能力：DNA train/test split
  - 用途：DNA 训练集拆分；同目录另有 DNA-129_Test.txt
  - 复用状态：blocked；类型：unknown
- `Datasets/DNA/DNA-129_Test.txt`
  - 能力：DNA train/test split
  - 用途：DNA 测试集拆分；同目录另有 DNA-573_Train.txt
  - 复用状态：blocked；类型：unknown
- `Datasets/RNA/RNA-495_Train.txt`
  - 能力：RNA train/test split
  - 用途：RNA 训练集拆分；同目录另有 RNA-117_Test.txt
  - 复用状态：blocked；类型：unknown
- `Datasets/RNA/RNA-117_Test.txt`
  - 能力：RNA train/test split
  - 用途：RNA 测试集拆分；同目录另有 RNA-495_Train.txt
  - 复用状态：blocked；类型：unknown
- `multi-feature/DNA/DNA_py_train1.txt`
  - 能力：DNA feature split
  - 用途：DNA 的 py 特征训练分片；同目录另有 train2/train3 与 test1/test2/test3
  - 复用状态：blocked；类型：unknown
- `multi-feature/DNA/DNA_train_PKx.txt`
  - 能力：DNA feature split
  - 用途：DNA 的 PKx 特征训练文件；同目录另有对应测试文件
  - 复用状态：blocked；类型：unknown
- `multi-feature/DNA/train_DNA_RAA.txt`
  - 能力：DNA feature split
  - 用途：DNA 的 RAA 特征训练文件；同目录另有对应测试文件
  - 复用状态：blocked；类型：unknown
- `multi-feature/DNA/HMM.pkl`
  - 能力：DNA feature cache
  - 用途：DNA HMM 特征缓存/中间文件
  - 复用状态：blocked；类型：unknown
- `multi-feature/DNA/PSSM.pkl`
  - 能力：DNA feature cache
  - 用途：DNA PSSM 特征缓存/中间文件
  - 复用状态：blocked；类型：unknown
- `multi-feature/RNA/RNA_py_train1.txt`
  - 能力：RNA feature split
  - 用途：RNA 的 py 特征训练分片；同目录另有 train2/train3 与 test1/test2/test3
  - 复用状态：blocked；类型：unknown
- `multi-feature/RNA/RNA_train_PKx.txt`
  - 能力：RNA feature split
  - 用途：RNA 的 PKx 特征训练文件；同目录另有对应测试文件
  - 复用状态：blocked；类型：unknown
- `multi-feature/RNA/train_RNA_RAA.txt`
  - 能力：RNA feature split
  - 用途：RNA 的 RAA 特征训练文件；同目录另有对应测试文件
  - 复用状态：blocked；类型：unknown
- `multi-feature/RNA/HMM.pkl`
  - 能力：RNA feature cache
  - 用途：RNA HMM 特征缓存/中间文件
  - 复用状态：blocked；类型：unknown
- `multi-feature/RNA/PSSM.pkl`
  - 能力：RNA feature cache
  - 用途：RNA PSSM 特征缓存/中间文件
  - 复用状态：blocked；类型：unknown

### inference

- `generate_multi_feature.py`
  - 能力：feature_generation
  - 用途：生成 DNA/RNA 多特征输入，属于推理前处理入口
  - 复用状态：blocked；类型：code_entry
- `predict.py`
  - 能力：prediction_entrypoint
  - 用途：推理入口，加载模型权重并输出结合位点预测
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `ensemble_DL_sequence_net.py`
  - 能力：model_architecture
  - 用途：集成深度网络结构定义，供预测脚本装配与加载权重
  - 复用状态：blocked；类型：code_entry
- `PKx.py`
  - 能力：feature_extraction
  - 用途：PKx 特征构造/编码辅助模块
  - 复用状态：blocked；类型：code_entry
- `RAA.py`
  - 能力：feature_extraction
  - 用途：RAA 特征构造/编码辅助模块
  - 复用状态：blocked；类型：code_entry
- `pychar.py`
  - 能力：utility
  - 用途：字符级序列特征辅助与编码工具
  - 复用状态：blocked；类型：code_entry
- `utils.py`
  - 能力：utility
  - 用途：通用辅助函数，支撑推理前后处理与IO
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态清单审计，未执行代码、未安装依赖、未运行测试。
- 仓库未见 LICENSE，代码/数据/权重的直接复用边界不明确。
- 部分 `.pkl` 与 `.h5` 只能确认存在，无法仅凭文件名验证生成过程或训练配置。

## 仍未知

- `multi-feature/*/HMM.pkl` 与 `PSSM.pkl` 的具体生成脚本、上游来源和许可未确认。
- 未见独立 evaluation 脚本、指标记录或阈值说明。
- `save_model/RNA/RNA_0.h5` 与其余 RNA 权重的组织关系未能从静态清单确认。
- `Datasets/*` 文本文件的原始来源、清洗步骤与许可未确认。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
