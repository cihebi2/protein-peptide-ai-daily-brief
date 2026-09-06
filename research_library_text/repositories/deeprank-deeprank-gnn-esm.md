# deeprank/deeprank-gnn-esm

- **仓库：** [https://github.com/deeprank/deeprank-gnn-esm](https://github.com/deeprank/deeprank-gnn-esm)
- **固定 commit：** `5470eaa253efb823c86013aba0fd9a869c90afde`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **资产记录数：** 23

## 仓库摘要

仓库提供 DeepRank-GNN-esm 的图构建、ESM/PSSM 特征、GNN 打分/预测、评估与多套预训练权重；当前仅能静态确认，代码许可清楚但数据/权重许可边界不完整。

## 可复用模块与资源

### checkpoints

- `paper_pretrained_models/DeepRank-GNN_models/scoring_of_docking_models/all_models/fold1_treg_yfnat_b128_e20_lr0.001_3.pt`
  - 能力：对接模型打分权重
  - 用途：10 折集合中的一个 scoring 权重文件。
  - 复用状态：partial；类型：model_weight
- `paper_pretrained_models/DeepRank-GNN_models/scoring_of_docking_models/all_models/fold10_treg_yfnat_b128_e20_lr0.001_5.pt`
  - 能力：对接模型打分权重
  - 用途：10 折集合中的一个 scoring 权重文件。
  - 复用状态：partial；类型：model_weight
- `paper_pretrained_models/scoring_of_docking_models/gnn_esm/treg_yfnat_b64_e20_lr0.001_foldall_esm.pth.tar`
  - 能力：端到端 scoring 权重
  - 用途：ESM 版本的 fold-all scoring checkpoint。
  - 复用状态：partial；类型：unknown
- `paper_pretrained_models/scoring_of_docking_models/gnn_esm_pssm/treg_yfnat_b50_e20_lr0.001_foldall_esm_pssm.pth.tar`
  - 能力：ESM+PSSM scoring 权重
  - 用途：ESM+PSSM 版本的 fold-all scoring checkpoint。
  - 复用状态：partial；类型：unknown
- `paper_pretrained_models/biological_vs_crystal_interfaces/gnn_esm/tclass_ybio_interface_b128_e50_lr0.001.pth.tar`
  - 能力：接口分类权重
  - 用途：biological_vs_crystal_interfaces 的分类 checkpoint。
  - 复用状态：partial；类型：unknown

### datasets

- `example/data/train_ref/train_data.csv`
  - 能力：训练参考表
  - 用途：示例训练/参考样本表，与测试夹具中的同名数据配套。
  - 复用状态：partial；类型：unknown
- `example/data/pdb/1ATN/1ATN_1w.pdb`
  - 能力：示例对接结构
  - 用途：提供 1ATN 的示例 PDB 输入；同目录还有 1ATN_2w 到 1ATN_10w。
  - 复用状态：partial；类型：unknown
- `example/data/pssm/1ATN/1ATN.A.pdb.pssm`
  - 能力：PSSM 示例特征
  - 用途：示例序列保守性特征输入，与测试夹具同类文件配套。
  - 复用状态：partial；类型：unknown
- `tests/data/hdf5/1ATN_residue.hdf5`
  - 能力：残基级 HDF5 夹具
  - 用途：用于测试数据集/图转换逻辑的 HDF5 固定夹具。
  - 复用状态：partial；类型：unknown
- `paper_pretrained_models/DeepRank-GNN_models/scoring_of_docking_models/BM5_CAPRI_datasets_details_csv/BM5_scores.csv`
  - 能力：基准集分数/目标元数据
  - 用途：BM5/CAPRI 相关的分数与数据集元数据。
  - 复用状态：partial；类型：unknown

### evaluation

- `src/deeprank_gnn/Metrics.py`
  - 能力：指标计算
  - 用途：实现评估指标与统计计算。
  - 复用状态：ready_for_review；类型：code_entry
- `paper_pretrained_models/DeepRank-GNN_models/scoring_of_docking_models/test.py`
  - 能力：预训练模型评估脚本
  - 用途：对 scoring_of_docking_models 预训练权重做静态测试/评估。
  - 复用状态：partial；类型：code_entry
- `tests/test_nn.py`
  - 能力：单元回归测试
  - 用途：检查网络相关逻辑的回归行为。
  - 复用状态：partial；类型：code_entry

### inference

- `src/deeprank_gnn/predict.py`
  - 能力：通用预测入口
  - 用途：对输入图或样本执行推理并输出打分结果。
  - 复用状态：ready_for_review；类型：code_entry
- `example/predict.py`
  - 能力：示例预测脚本
  - 用途：演示如何调用预测流程。
  - 复用状态：ready_for_review；类型：code_entry
- `paper_pretrained_models/DeepRank-GNN_models/biological_vs_crystal_interfaces/prediction_phy_non-phy.py`
  - 能力：接口分类推理
  - 用途：针对 biological_vs_crystal_interfaces 预训练模型的专用推理脚本。
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `src/deeprank_gnn/DataSet.py`
  - 能力：数据装载与样本组织
  - 用途：封装数据集读取、样本组织与图数据批处理入口。
  - 复用状态：ready_for_review；类型：code_entry
- `src/deeprank_gnn/GraphGenMP.py`
  - 能力：界面图生成
  - 用途：多进程生成蛋白-蛋白界面图，并配合残基图/自定义图/BSA/PSSM 工具做特征装配。
  - 复用状态：ready_for_review；类型：code_entry
- `src/deeprank_gnn/ginet.py`
  - 能力：GNN 结构与池化
  - 用途：定义用于界面打分的图神经网络主体，并与 community pooling / 通用训练封装协同。
  - 复用状态：ready_for_review；类型：code_entry
- `src/deeprank_gnn/tools/embedding.py`
  - 能力：ESM/PSSM 特征处理
  - 用途：读取或转换蛋白语言模型嵌入，并与 PSSM/序列保守性工具链衔接。
  - 复用状态：ready_for_review；类型：code_entry
- `example/data/embedding/1ATN/1ATN_1w.A.pt`
  - 能力：预计算 ESM 嵌入特征
  - 用途：作为示例/测试中可直接复用的输入表征文件，而非模型权重。
  - 复用状态：partial；类型：unknown

### training

- `src/deeprank_gnn/NeuralNet.py`
  - 能力：训练封装
  - 用途：提供通用训练/优化封装，但冻结清单没有单独训练入口。
  - 复用状态：partial；类型：code_entry
- `docs/tutorial.train_model.rst`
  - 能力：训练教程
  - 用途：描述训练流程和参数组织方式。
  - 复用状态：partial；类型：unknown

## 使用限制

- 仅做静态审查，未安装依赖、未执行代码、未跑测试。
- 冻结清单中没有单独的 training entrypoint，训练链路只能从模块与教程推断。
- 示例/测试数据与 checkpoint 的生成来源和独立许可未被静态证实。
- `.pt` 文件既包含模型权重也包含预计算嵌入，不能把它们都当作同一类 checkpoint。

## 仍未知

- `paper_pretrained_models` 下各权重是否全部为项目自训练、是否对应同一训练数据分割，清单未证实。
- `example/data/embedding/*.pt` 的生成流程、依赖模型和许可来源未证实。
- BM5/CAPRI 相关 CSV 与 1ATN 示例数据的原始出处和再分发边界未证实。
- 仓库虽有训练教程，但缺少可直接确认的独立训练入口与运行结果。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
