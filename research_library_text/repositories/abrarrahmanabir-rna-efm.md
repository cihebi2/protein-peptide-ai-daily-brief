# abrarrahmanabir/RNA-EFM

- **仓库：** [https://github.com/abrarrahmanabir/RNA-EFM](https://github.com/abrarrahmanabir/RNA-EFM)
- **固定 commit：** `975b407d5ef9b56a4af4b2d70fdd567ce79e7eeb`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 20

## 仓库摘要

静态盘点显示仓库由 `rnaefm/`、`geometric_rna_design/` 和 `RoseTTAFold2NA/` 三部分组成；可见训练、推理、评测与数据切分入口，但未见可核验的 checkpoint 或 bundled data，且根目录未发现统一 LICENSE。

## 可复用模块与资源

### datasets

- `geometric_rna_design/notebooks/data_splitting_random.ipynb`
  - 能力：数据切分协议
  - 用途：随机切分逻辑与实验划分说明
  - 复用状态：blocked；类型：unknown
- `geometric_rna_design/notebooks/data_splitting_seqid.ipynb`
  - 能力：数据切分协议
  - 用途：按 sequence identity 切分逻辑
  - 复用状态：blocked；类型：unknown
- `RoseTTAFold2NA/network/data_loader.py`
  - 能力：数据加载/预处理
  - 用途：结构或样本加载逻辑；不是原始数据本身
  - 复用状态：blocked；类型：code_entry
- `geometric_rna_design/src/data_utils.py`
  - 能力：数据统计与清洗辅助
  - 用途：数据统计、过滤或预处理工具
  - 复用状态：blocked；类型：code_entry

### evaluation

- `RoseTTAFold2NA/SE3Transformer/se3_transformer/runtime/metrics.py`
  - 能力：指标实现
  - 用途：训练/推理指标计算
  - 复用状态：blocked；类型：code_entry
- `RoseTTAFold2NA/SE3Transformer/scripts/benchmark_inference.sh`
  - 能力：推理基准脚本
  - 用途：推理性能基准
  - 复用状态：blocked；类型：code_entry
- `RoseTTAFold2NA/SE3Transformer/scripts/benchmark_train.sh`
  - 能力：训练基准脚本
  - 用途：训练性能基准
  - 复用状态：blocked；类型：code_entry
- `RoseTTAFold2NA/SE3Transformer/tests/test_equivariance.py`
  - 能力：equivariance 测试
  - 用途：SE(3) 等变性验证测试
  - 复用状态：blocked；类型：code_entry

### inference

- `scripts/inference.py`
  - 能力：推理入口
  - 用途：顶层推理启动脚本
  - 复用状态：blocked；类型：code_entry
- `RoseTTAFold2NA/network/predict.py`
  - 能力：推理脚本
  - 用途：预测/推断流程
  - 复用状态：blocked；类型：code_entry
- `RoseTTAFold2NA/SE3Transformer/se3_transformer/runtime/inference.py`
  - 能力：推理 runtime
  - 用途：推理循环与批处理输出
  - 复用状态：blocked；类型：code_entry
- `RoseTTAFold2NA/SE3Transformer/scripts/predict.sh`
  - 能力：推理 shell 包装
  - 用途：命令行推理封装
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `rnaefm/models/rnaflow.py`
  - 能力：energy-based flow matching RNA 设计主干
  - 用途：核心生成/优化模块
  - 复用状态：blocked；类型：code_entry
- `rnaefm/models/inverse_folding.py`
  - 能力：RNA inverse folding / 条件序列设计
  - 用途：逆折叠或条件生成组件
  - 复用状态：blocked；类型：code_entry
- `geometric_rna_design/src/model.py`
  - 能力：几何 RNA design 模型
  - 用途：几何约束下的 RNA 设计
  - 复用状态：blocked；类型：code_entry
- `RoseTTAFold2NA/network/RoseTTAFoldModel.py`
  - 能力：RoseTTAFold2NA 联合建模骨干
  - 用途：蛋白-RNA 联合建模主干
  - 复用状态：blocked；类型：code_entry

### training

- `scripts/train.py`
  - 能力：训练入口
  - 用途：顶层训练启动脚本
  - 复用状态：blocked；类型：code_entry
- `geometric_rna_design/src/train.py`
  - 能力：训练入口
  - 用途：geometric_rna_design 的训练流程
  - 复用状态：blocked；类型：code_entry
- `RoseTTAFold2NA/SE3Transformer/scripts/train.sh`
  - 能力：训练脚本
  - 用途：SE3Transformer 单机训练启动
  - 复用状态：blocked；类型：code_entry
- `RoseTTAFold2NA/SE3Transformer/se3_transformer/runtime/training.py`
  - 能力：训练 runtime
  - 用途：训练循环、优化与日志相关 runtime
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅静态分析，未执行任何仓库代码
- 依赖未安装，测试未运行
- submodules 未初始化
- 未发现可核验 checkpoint / 权重文件
- build/lib 与 .egg 更像打包产物，不能当作独立源码或复现证据
- example/*/log 下 stdout/stderr 仅是日志，不代表成功复现

## 仍未知

- `RoseTTAFold2NA/LICENSE` 与 `RoseTTAFold2NA/SE3Transformer/LICENSE` 的具体条款未读取
- 原始数据集来源、规模、划分比例无法仅凭路径确认
- 是否存在外部下载器或隐藏权重未在库存中显式出现
- `build/lib/` 与 `dist/*.egg` 是否与源码完全一致不可从静态路径确认
- `geometric_rna_design` 与 `rnaefm` 是否全部原创或含更多复用成分无法仅凭目录名确认

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
