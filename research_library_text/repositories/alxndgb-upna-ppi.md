# alxndgb/UPNA-PPI

- **仓库：** [https://github.com/alxndgb/UPNA-PPI](https://github.com/alxndgb/UPNA-PPI)
- **固定 commit：** `20d1d8225e9d377434669973b7391697be6b4aa2`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **资产记录数：** 26

## 仓库摘要

该仓库主要是PPI预测论文的静态资源包：包含 ComPPlete/TPPNI 交互数据、ProtVec 特征、5 个 H5 检查点以及用于推理和解释的 Jupyter notebooks；未见独立训练入口或模型源码，数据与模型的单独许可边界也未完整披露。

## 可复用模块与资源

### checkpoints

- `models/compplete_02_12_2024_fold0.h5`
  - 能力：fold0 模型检查点
  - 用途：第0折权重，用于推理或集成
  - 复用状态：unknown；类型：model_weight
- `models/compplete_02_12_2024_fold1.h5`
  - 能力：fold1 模型检查点
  - 用途：第1折权重，用于推理或集成
  - 复用状态：unknown；类型：model_weight
- `models/compplete_02_12_2024_fold2.h5`
  - 能力：fold2 模型检查点
  - 用途：第2折权重，用于推理或集成
  - 复用状态：unknown；类型：model_weight
- `models/compplete_02_12_2024_fold3.h5`
  - 能力：fold3 模型检查点
  - 用途：第3折权重，用于推理或集成
  - 复用状态：unknown；类型：model_weight
- `models/compplete_02_12_2024_fold4.h5`
  - 能力：fold4 模型检查点
  - 用途：第4折权重，用于推理或集成
  - 复用状态：unknown；类型：model_weight

### datasets

- `data/ComPPlete_PPNI_PPI_Interactome/ComPPlete_PPI_021224_part_1.csv`
  - 能力：主PPI交互分片
  - 用途：ComPPlete PPI interactome 第1分片，作为主交互数据的一部分
  - 复用状态：unknown；类型：unknown
- `data/ComPPlete_PPNI_PPI_Interactome/ComPPlete_PPI_021224_part_2.csv`
  - 能力：主PPI交互分片
  - 用途：ComPPlete PPI interactome 第2分片，作为主交互数据的一部分
  - 复用状态：unknown；类型：unknown
- `data/ComPPlete_PPNI_PPI_Interactome/ComPPlete_PPI_021224_part_3.csv`
  - 能力：主PPI交互分片
  - 用途：ComPPlete PPI interactome 第3分片，作为主交互数据的一部分
  - 复用状态：unknown；类型：unknown
- `data/ComPPlete_PPNI_PPI_Interactome/ComPPlete_PPI_021224_part_4.csv`
  - 能力：主PPI交互分片
  - 用途：ComPPlete PPI interactome 第4分片，作为主交互数据的一部分
  - 复用状态：unknown；类型：unknown
- `data/ComPPlete_PPNI_PPI_Interactome/ComPPlete_PPI_021224_part_5.csv`
  - 能力：主PPI交互分片
  - 用途：ComPPlete PPI interactome 第5分片，作为主交互数据的一部分
  - 复用状态：unknown；类型：unknown
- `data/ComPPlete_PPNI_PPI_Interactome/ComPPlete_PPNI_021224_part_1.csv`
  - 能力：补充PPNI分片
  - 用途：ComPPlete PPNI 第1分片，补充交互数据
  - 复用状态：unknown；类型：unknown
- `data/ComPPlete_PPNI_PPI_Interactome/ComPPlete_PPNI_021224_part_2.csv`
  - 能力：补充PPNI分片
  - 用途：ComPPlete PPNI 第2分片，补充交互数据
  - 复用状态：unknown；类型：unknown
- `data/GPCRs_seq.csv`
  - 能力：GPCR序列集合
  - 用途：GPCR 预测输入序列集
  - 复用状态：unknown；类型：unknown
- `data/Topological_Negatives/Topological_Negatives_TPPNI_1.csv`
  - 能力：拓扑负样本分片
  - 用途：TPPNI 第1分片，作为拓扑驱动负样本
  - 复用状态：unknown；类型：unknown
- `data/Topological_Negatives/Topological_Negatives_TPPNI_2.csv`
  - 能力：拓扑负样本分片
  - 用途：TPPNI 第2分片，作为拓扑驱动负样本
  - 复用状态：unknown；类型：unknown
- `data/Topological_Negatives/Topological_Negatives_TPPNI_3.csv`
  - 能力：拓扑负样本分片
  - 用途：TPPNI 第3分片，作为拓扑驱动负样本
  - 复用状态：unknown；类型：unknown
- `data/Topological_Negatives/Topological_Negatives_TPPNI_4.csv`
  - 能力：拓扑负样本分片
  - 用途：TPPNI 第4分片，作为拓扑驱动负样本
  - 复用状态：unknown；类型：unknown
- `data/protVec_100d_3grams.csv`
  - 能力：ProtVec特征表
  - 用途：100d 3-gram ProtVec 向量表，用于蛋白序列表征
  - 复用状态：unknown；类型：unknown
- `data/gene_protein_mapping.pickle`
  - 能力：标识映射
  - 用途：gene/protein 标识对照映射，供数据对齐使用
  - 复用状态：unknown；类型：unknown

### evaluation

- `interpretability/5-fold-Interpretability-Heterodimers.ipynb`
  - 能力：异源二聚体解释性评估
  - 用途：5 折异源二聚体解释/评估
  - 复用状态：partial；类型：unknown
- `interpretability/5-fold-Interpretability-Homodimers.ipynb`
  - 能力：同源二聚体解释性评估
  - 用途：5 折同源二聚体解释/评估
  - 复用状态：partial；类型：unknown

### inference

- `frontend/Run_ComPPlete.ipynb`
  - 能力：推理运行笔记本
  - 用途：交互式/批量运行 ComPPlete 推理流程
  - 复用状态：partial；类型：unknown
- `frontend/output/GPCRS_all_preds.csv`
  - 能力：推理输出快照
  - 用途：GPCRS 预测结果快照，属于推理产物
  - 复用状态：partial；类型：unknown

### reusable_assets

- `environment.yml`
  - 能力：环境说明
  - 用途：Conda 依赖约束，辅助复现运行环境
  - 复用状态：ready_for_review；类型：config
- `images/pipeline.PNG`
  - 能力：方法流程图
  - 用途：静态流程图，说明 ComPPlete/TPPNI 管线
  - 复用状态：ready_for_review；类型：unknown
- `README.md`
  - 能力：仓库说明
  - 用途：仓库用途、目录与运行说明
  - 复用状态：ready_for_review；类型：unknown

## 使用限制

- 仅做静态清单审查，未执行任何 notebook、脚本或模型。
- 依赖未安装，`.h5` 仅确认存在，未验证可加载或可推理。
- 未见独立训练入口、模型架构源码、测试或 CI。
- 数据、模型、embedding 与输出文件缺少单独许可与来源说明。

## 仍未知

- ComPPlete、PPNI、Topological_Negatives、GPCRs_seq 与 gene_protein_mapping.pickle 的来源/授权边界未确认。
- `protVec_100d_3grams.csv` 是否为第三方 vendored 资源需进一步核实。
- 5 个 `.h5` 检查点是否对应论文最终设置、fold 划分与超参数无法静态证明。
- `frontend/output/GPCRS_all_preds.csv` 是否由当前 commit 生成、输入何种数据不可静态确认。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
