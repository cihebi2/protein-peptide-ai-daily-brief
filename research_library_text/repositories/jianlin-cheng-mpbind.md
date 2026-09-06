# jianlin-cheng/mpbind

- **仓库：** [https://github.com/jianlin-cheng/mpbind](https://github.com/jianlin-cheng/mpbind)
- **固定 commit：** `741a5e4461700d41bfc341edfaf5807e9ee30861`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0
- **资产记录数：** 16

## 仓库摘要

该仓库是 MPBind 的静态可复用实现，包含模型架构、特征/数据处理、训练与推理入口，以及若干示例结构和 5 个权重文件。代码许可证可按 GPL-3.0 处理，但数据与模型权重的再分发边界未被静态证据明确。

## 可复用模块与资源

### checkpoints

- `weight/model_v0.pt`
  - 能力：model checkpoint bundle
  - 用途：五个训练后权重文件（model_v0 到 model_vn）
  - 复用状态：blocked；类型：model_weight
- `weight/train_model_5.log`
  - 能力：training log / checkpoint trace
  - 用途：训练日志，可能包含 loss/metric 轨迹
  - 复用状态：unknown；类型：unknown

### datasets

- `datasets/construct/nonredundant_thre-2022-01-01_seq-id-0.3.fasta`
  - 能力：training corpus
  - 用途：非冗余序列集合，用于构造训练数据
  - 复用状态：partial；类型：unknown
- `datasets/subunits_train_set.txt`
  - 能力：train/validation/test split lists
  - 用途：训练、验证、测试拆分清单
  - 复用状态：partial；类型：unknown
- `example/AF-Q14D04-F1-model_v4.pdb`
  - 能力：demo structure and feature bundle
  - 用途：示例输入结构及其派生特征/预测文件
  - 复用状态：partial；类型：unknown
- `AlphaFold3/folder0/7R1M_1_A_0.pdb`
  - 能力：bulk AlphaFold3 example structures
  - 用途：大量 bundled PDB 示例，覆盖多个 AlphaFold3/folder* 目录
  - 复用状态：unknown；类型：unknown

### inference

- `experiment/inference.py`
  - 能力：inference entrypoint
  - 用途：推理脚本，生成预测输出
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `models/clof_seq.py`
  - 能力：binding-site model architecture
  - 用途：主模型架构与相关图/序列算子，支撑 binding-site 预测
  - 复用状态：ready_for_review；类型：code_entry
- `src/data_encoding.py`
  - 能力：feature encoding and tensorization
  - 用途：把结构/序列信息编码成训练与推理所需特征张量
  - 复用状态：ready_for_review；类型：code_entry
- `src/feature_extraction/ProtTrans.py`
  - 能力：ProtTrans and structure feature extraction
  - 用途：生成 ProtTrans 相关表征并驱动结构前处理
  - 复用状态：ready_for_review；类型：code_entry
- `src/feature_extraction/mkdssp`
  - 能力：bundled DSSP executable
  - 用途：二级结构特征计算所需的随仓库二进制依赖
  - 复用状态：unknown；类型：unknown
- `src/feature_extraction/Max_ProtTrans_repr.npy`
  - 能力：feature normalization constants
  - 用途：ProtTrans 表征归一化常量
  - 复用状态：partial；类型：unknown
- `experiment/build_dataset.py`
  - 能力：dataset construction
  - 用途：构造训练/验证/测试数据并组织样本
  - 复用状态：ready_for_review；类型：code_entry
- `datasets/download_data.sh`
  - 能力：data acquisition helper
  - 用途：下载和准备外部数据的 shell 脚本
  - 复用状态：ready_for_review；类型：code_entry

### training

- `experiment/train.py`
  - 能力：training entrypoint
  - 用途：训练主入口；按路径名推断其调用数据加载、配置与模型定义
  - 复用状态：ready_for_review；类型：code_entry
- `experiment/config.py`
  - 能力：training configuration
  - 用途：超参数和实验配置
  - 复用状态：ready_for_review；类型：config

## 使用限制

- 仅做静态审查，未运行仓库代码。
- 依赖未安装，无法验证导入、训练或推理是否可执行。
- 未运行测试，且未见 tests/CI 入口。
- 未见独立 evaluation 目录或评测脚本，无法核实报告指标。
- 子模块未初始化，部分外部内容可能不可见。
- 大于 5MiB 的 blob 可能只是 promisor 占位，不能当作可复现证据。
- 路径存在不等于实际可复现或可再分发。

## 仍未知

- `weight/*.pt` 是否对应论文最终模型、以及其单独许可状态不明。
- `datasets/construct/*.fasta` 和 `datasets/subunits_*.txt` 的生成规则与上游来源未被静态证据证明。
- `example/` 与 `AlphaFold3/folder*/` 中的 PDB/feature 文件是否为作者自生成、以及能否再分发不明。
- `weight/train_model_5.log` 是否记录了论文报告的指标不明。
- `src/feature_extraction/mkdssp` 的第三方来源与许可边界不明。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
