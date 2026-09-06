# ai4protein/ProtSSN

- **仓库：** [https://github.com/ai4protein/ProtSSN](https://github.com/ai4protein/ProtSSN)
- **固定 commit：** `d99091a979c9106bf7173d1bde5ef64125cd338e`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** found
- **资产记录数：** 12

## 仓库摘要

仓库以 ProtSSN 为核心，包含模型结构、数据读取/预处理、训练/微调脚本以及 embedding/fitness 辅助脚本；冻结清单中还包含 DDG、DTM、PDBSol 和 ProteinGym 相关数据与若干 .pt 缓存，但未见可验证的独立评测目录或典型模型权重。

## 可复用模块与资源

### checkpoints

- `norm/cath_k10_mean_attr.pt`
  - 能力：归一化统计/属性缓存
  - 用途：CATH 邻域/属性均值缓存，按路径更像统计张量，不是典型模型权重
  - 复用状态：partial；类型：model_weight
- `data/mutant_example/proteingym-benchmark/Proteingym-benchmark_k10/processed/pre_filter.pt`
  - 能力：ProteinGym 预处理图缓存
  - 用途：图/处理缓存，便于复用，但静态路径不足以证明为训练 checkpoint
  - 复用状态：partial；类型：model_weight

### datasets

- `data/DDG/README.md`
  - 能力：DDG benchmark bundle
  - 用途：蛋白突变稳定性/ΔΔG 相关样本与结构配对
  - 复用状态：unknown；类型：unknown
- `data/DTM/README.md`
  - 能力：DTM benchmark bundle
  - 用途：热稳定性/熔解温度相关样本
  - 复用状态：unknown；类型：unknown
- `data/finetune_example/README.md`
  - 能力：PDBSol fine-tuning example
  - 用途：溶解度任务示例划分
  - 复用状态：unknown；类型：unknown
- `data/mutant_example/proteingym-benchmark/DATASET/A0A1I9GEU1_NEIME_Kennouche_2019/A0A1I9GEU1_NEIME_Kennouche_2019.tsv`
  - 能力：ProteinGym mutant benchmark example
  - 用途：突变效应/无实验标注示例
  - 复用状态：unknown；类型：unknown

### evaluation

- `compute_fitness.py`
  - 能力：fitness 计算
  - 用途：对突变/样本进行 fitness 打分，作为评估辅助
  - 复用状态：partial；类型：code_entry

### inference

- `get_embedding.py`
  - 能力：embedding 导出
  - 用途：提取蛋白 embedding/表示
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `src/models.py`
  - 能力：ProtSSN 模型主干与图编码器
  - 用途：实现 ProtSSN 的几何/图网络骨干与下游表示层
  - 复用状态：partial；类型：code_entry
- `src/data.py`
  - 能力：数据读取与预处理
  - 用途：构建 CATH/突变体/监督任务数据管线
  - 复用状态：partial；类型：code_entry

### training

- `run_pt.py`
  - 能力：预训练入口与配置
  - 用途：启动预训练/主流程与模型配置
  - 复用状态：partial；类型：code_entry
- `run_ft.py`
  - 能力：微调入口与分布式配置
  - 用途：下游微调与 FSDP 配置
  - 复用状态：partial；类型：code_entry

## 使用限制

- 仅做静态盘点，未执行代码、训练、测试或下载流程。
- 未见独立 evaluation 目录或 tests/CI；评测主要只能从脚本路径推断。
- 大量 data/*.pt 更像预处理/统计缓存，未证实为可直接复用的模型 checkpoint。
- 冻结清单未拆分数据与模型许可，外部数据来源与再分发条件仍需单独确认。

## 仍未知

- LICENSE 的具体条款及对代码/数据/模型的许可边界。
- data/DDG、data/DTM、data/finetune_example、data/mutant_example 的原始来源与授权。
- get_embedding.py 与 compute_fitness.py 的实际运行参数和输出约定是否与 README 完全一致。
- 是否存在未入清单的额外模型权重或外部下载资产。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
