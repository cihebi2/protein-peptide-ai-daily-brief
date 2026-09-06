# baker-laboratory/RoseTTAFold-All-Atom

- **仓库：** [https://github.com/baker-laboratory/RoseTTAFold-All-Atom](https://github.com/baker-laboratory/RoseTTAFold-All-Atom)
- **固定 commit：** `d69ab3a73f8ede31a4cc005fbc076a341d848469`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** BSD-3-Clause
- **资产记录数：** 16

## 仓库摘要

该仓库静态呈现了 RoseTTAFold-All-Atom 的全原子结构预测流水线：包含主模型、SE(3) 等变子模块、输入解析/预处理、推理与训练脚本、benchmark/test，以及若干示例 FASTA/SDF 和 .pt 资源；但未执行代码，运行性与可复现性未验证。

## 可复用模块与资源

### checkpoints

- `examples/docker/3fap_aux.pt`
  - 能力：Docker demo 辅助权重/状态包
  - 用途：为 docker 示例推理提供辅助张量或权重状态
  - 复用状态：partial；类型：model_weight
- `rf2aa/atomized_protein_frames.pt`
  - 能力：atomized protein frame 资源
  - 用途：支持 all-atom protein frame 处理/推理的二进制资源
  - 复用状态：partial；类型：model_weight

### datasets

- `examples/protein/7qxr.fasta`
  - 能力：protein 示例输入
  - 用途：结构预测/回归的蛋白 demo 输入集
  - 复用状态：partial；类型：unknown
- `examples/nucleic_acid/7u7w_B.fasta`
  - 能力：nucleic acid 示例输入
  - 用途：核酸相关推理的 demo 输入
  - 复用状态：partial；类型：unknown
- `examples/small_molecule/XG4.sdf`
  - 能力：small molecule 示例输入
  - 用途：ligand / glycan / 小分子复合物 demo 输入
  - 复用状态：partial；类型：unknown
- `rf2aa/ligands.json.gz`
  - 能力：化学/配体参考表
  - 用途：配体字典、化学模板或原子/键参考的支撑数据
  - 复用状态：partial；类型：unknown

### evaluation

- `rf2aa/SE3Transformer/se3_transformer/runtime/metrics.py`
  - 能力：benchmark 与指标计算
  - 用途：计算 inference/train benchmark 指标并支持基准脚本
  - 复用状态：partial；类型：code_entry
- `rf2aa/SE3Transformer/tests/test_equivariance.py`
  - 能力：equivariance 回归测试
  - 用途：提供结构等变性的静态测试入口
  - 复用状态：partial；类型：code_entry

### inference

- `rf2aa/run_inference.py`
  - 能力：顶层推理入口
  - 用途：调度 all-atom 结构预测并写出结果
  - 复用状态：ready_for_review；类型：code_entry
- `rf2aa/SE3Transformer/scripts/predict.sh`
  - 能力：SE3Transformer 推理入口
  - 用途：启动 vendored runtime 的预测流程
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `rf2aa/model/RoseTTAFoldModel.py`
  - 能力：全原子结构预测主模型
  - 用途：组装主干网络与输出头，支撑蛋白/核酸/小分子复合体的结构推理
  - 复用状态：ready_for_review；类型：code_entry
- `rf2aa/data/data_loader.py`
  - 能力：输入解析与预处理
  - 用途：解析、合并和预处理 protein、nucleic acid、small molecule 与 covalent 输入
  - 复用状态：ready_for_review；类型：code_entry
- `rf2aa/config/inference/protein.yaml`
  - 能力：推理配置模板
  - 用途：切换 protein、nucleic_acid、protein_sm、protein_na_sm、protein_complex_sm 与 covalent 等推理模式
  - 复用状态：ready_for_review；类型：config
- `rf2aa/SE3Transformer/se3_transformer/model/transformer.py`
  - 能力：SE(3)-equivariant 训练/推理子树
  - 用途：提供等变注意力、卷积、归一化和 runtime 组件，支撑独立 backbone 或 vendored 依赖复用
  - 复用状态：partial；类型：code_entry

### training

- `rf2aa/training/checkpoint.py`
  - 能力：训练状态管理
  - 用途：checkpoint 保存/加载、EMA 和 recycling 等训练辅助逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `rf2aa/SE3Transformer/scripts/train.sh`
  - 能力：SE3Transformer 训练入口
  - 用途：启动单机/多机训练流水线
  - 复用状态：partial；类型：code_entry

## 使用限制

- 仅做静态清点，未执行仓库代码、未安装依赖、未运行测试。
- 大型 .pt / .gz 资源可能只是 promisor blob，路径存在不等于可用或可复现。
- 示例输入与 checkpoint 文件没有独立的冻结许可证与来源说明，复用边界不清。
- SE3Transformer 子树疑似 vendored 组件，不能默认视作项目原创代码。
- 未见数据库 schema 或数据下载管线的独立证据，训练/推理实际数据流未被验证。

## 仍未知

- .pt 资源是否为完整模型 checkpoint、仅辅助状态，还是推理缓存，无法从路径本身确认。
- 示例 FASTA/SDF 是否来自外部公共结构或项目自建数据，冻结清单不足以判断。
- root 训练流水线是否能在当前 commit 上无修改复现，未执行无法确认。
- README 与源码正文未逐文件复核，部分功能只能依据路径命名推断。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
