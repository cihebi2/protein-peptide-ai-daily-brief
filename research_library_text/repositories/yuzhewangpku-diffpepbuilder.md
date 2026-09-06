# yuzhewangpku/diffpepbuilder

- **仓库：** [https://github.com/yuzhewangpku/diffpepbuilder](https://github.com/yuzhewangpku/diffpepbuilder)
- **固定 commit：** `c19eb4f0cd2419d3bcc116184c0868243b6c4169`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 18

## 仓库摘要

仓库提供蛋白-肽对接与 binder screening 的核心代码、数据和评估脚本；冻结清单未见 checkpoint，数据与示例结构的独立许可边界仍需单独核查。

## 可复用模块与资源

### datasets

- `datasets/PepPC_dataset.csv`
  - 能力：主数据表
  - 用途：PepPC 主数据表，推测用于训练/筛选
  - 复用状态：partial；类型：unknown
- `datasets/PepPC_before_202201.csv`
  - 能力：时间切分子集
  - 用途：按时间切分的历史样本子集，可能用于训练/验证划分
  - 复用状态：partial；类型：unknown
- `datasets/docking/docking_benchmark.csv`
  - 能力：基准集合
  - 用途：对接基准集合，用于比较/筛选任务
  - 复用状态：partial；类型：unknown
- `datasets/docking/AF2_predicted_domains/O75554.pdb`
  - 能力：AF2 预测受体结构
  - 用途：bundled receptor structure input for docking
  - 复用状态：partial；类型：unknown
- `examples/docking_data/7Z6F.pdb`
  - 能力：示例对接输入
  - 用途：示例受体/复现实验输入
  - 复用状态：partial；类型：unknown

### evaluation

- `analysis/metrics.py`
  - 能力：评估指标计算
  - 用途：计算 screening / ranking 评估指标
  - 复用状态：ready_for_review；类型：code_entry
- `datasets/docking/PBD_screening_metrics.csv`
  - 能力：评估结果表
  - 用途：保存或复用 screening metrics 汇总表
  - 复用状态：partial；类型：unknown
- `config/eval.yaml`
  - 能力：评估配置
  - 用途：评估任务与输出参数配置
  - 复用状态：ready_for_review；类型：config

### inference

- `experiments/run_docking.py`
  - 能力：对接推理入口
  - 用途：批量 docking 推理与筛选入口
  - 复用状态：ready_for_review；类型：code_entry
- `experiments/run_postprocess.py`
  - 能力：后处理流程
  - 用途：对接输出后处理、排序与整理
  - 复用状态：ready_for_review；类型：code_entry
- `config/inference.yaml`
  - 能力：推理配置
  - 用途：推理运行参数与批处理设置
  - 复用状态：ready_for_review；类型：config

### reusable_assets

- `model/score_network.py`
  - 能力：核心打分/扩散网络
  - 用途：用于 peptide pose 生成、打分与排序的核心模型逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `model/ipa_module.py`
  - 能力：几何与结构模块
  - 用途：承载 SE(3) 相关几何更新与结构建模组件
  - 复用状态：ready_for_review；类型：code_entry
- `openfold/model/model.py`
  - 能力：vendored backbone
  - 用途：结构预测/折叠骨干模块，疑似 vendored OpenFold 代码
  - 复用状态：partial；类型：code_entry
- `experiments/preprocess_utils.py`
  - 能力：预处理辅助
  - 用途：数据与受体预处理、样本整理
  - 复用状态：ready_for_review；类型：code_entry

### training

- `experiments/train.py`
  - 能力：训练入口
  - 用途：训练/微调主入口
  - 复用状态：ready_for_review；类型：code_entry
- `config/finetune.yaml`
  - 能力：训练配置
  - 用途：训练超参数与任务配置
  - 复用状态：ready_for_review；类型：config
- `config/base.yaml`
  - 能力：基础配置
  - 用途：共享默认参数与训练/推理公共设置
  - 复用状态：ready_for_review；类型：config

## 使用限制

- 仅做静态审查，未执行代码或测试。
- 依赖未安装，无法验证训练/推理/评估路径是否可运行。
- 冻结清单未见 checkpoint 或模型权重，无法确认可直接复现的推理状态。
- 仓库内 bundled 数据与示例结构的上游来源/许可边界未能仅凭静态清单完全建立。

## 仍未知

- openfold/ 是否为完整 vendored 第三方副本，以及其与仓库顶层 MIT 许可的实际边界。
- CSV/PDB 示例与 AF2_predicted_domains 数据是否存在上游数据使用限制或额外许可。
- `experiments/run_inference.py` 存在于清单中，但静态 inventory 未单列 inference 子系统，完整推理边界仍有不确定性。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
