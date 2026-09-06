# Bhattacharya-Lab/EquiPPIS

- **仓库：** [https://github.com/Bhattacharya-Lab/EquiPPIS](https://github.com/Bhattacharya-Lab/EquiPPIS)
- **固定 commit：** `15fdccc532517dfaadbeea12759be59ef3f3f5de`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0
- **资产记录数：** 9

## 仓库摘要

仓库是 EquiPPIS 的静态发布版，围绕 E(3) equivariant GNN 做蛋白质-蛋白质相互作用位点预测。可见内容包含模型/预处理代码、数据加载器、60 组样本的输入与派生特征、以及 1 个 checkpoint；但未见可明确识别的训练入口、独立推理入口或评估脚本，因此只能确认静态可用性，不能证明可复现执行。

## 可复用模块与资源

### checkpoints

- `Trained_model/EquiPPIS_model/E-l10-256.pt`
  - 能力：ppi_site_prediction_checkpoint
  - 用途：已训练权重，供加载模型做推理或续训候选
  - 复用状态：partial；类型：model_weight

### datasets

- `Preprocessing/input/1ay7A.pdb`
  - 能力：raw_ppi_site_inputs
  - 用途：60 组样本的原始输入集合（每组含 .pdb/.fasta/.pssm/.dssp/.esm2_33.npy）
  - 复用状态：partial；类型：unknown
- `Preprocessing/distmaps/1ay7A.dist`
  - 能力：distance_map_bundle
  - 用途：60 组样本的距离图/派生结构关系文件
  - 复用状态：partial；类型：unknown
- `Preprocessing/processed_features/1ay7A.118feat.npy`
  - 能力：preprocessed_node_feature_bundle
  - 用途：60 组样本的 118 维预处理节点特征张量
  - 复用状态：partial；类型：unknown

### reusable_assets

- `EquiPPIS.py`
  - 能力：model_architecture
  - 用途：仓库核心模型实现/主程序候选，承载 EquiPPIS 的网络逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `egnn_clean.py`
  - 能力：equivariant_gnn_components
  - 用途：EGNN 相关层与消息传递组件
  - 复用状态：ready_for_review；类型：code_entry
- `Dataloader.py`
  - 能力：data_loader
  - 用途：读取预处理样本并组织模型输入
  - 复用状态：ready_for_review；类型：code_entry
- `Preprocessing/gen_preprocessed_node_features.py`
  - 能力：feature_preprocessing_suite
  - 用途：生成/汇总节点特征；同目录还包含 DSSP、PSSM、几何与 ESM2 特征脚本
  - 复用状态：ready_for_review；类型：code_entry
- `EquiPPIS_environment.yml`
  - 能力：runtime_environment_recipe
  - 用途：记录 Python 依赖环境，供训练/复现时建环境
  - 复用状态：partial；类型：config

## 使用限制

- 仅做静态清点，未运行代码或测试
- 依赖未安装，无法验证可执行性
- 未见明确 training entrypoint、独立 inference 脚本或 evaluation 脚本
- 大文件可能是 promisor/blob 载荷，内容未进一步核实
- 路径存在不等于可复现执行或可直接再分发

## 仍未知

- Preprocessing/input/ 中 60 组样本的真实来源与许可未从静态清单中确认
- checkpoint E-l10-256.pt 是否与当前代码版本完全匹配未知
- README / Preprocessing/readme.md 是否给出可运行命令或评估协议未知
- 仓库是否还依赖外部数据、脚本或未初始化子模块未知

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
