# zchwang/IGModel

- **仓库：** [https://github.com/zchwang/IGModel](https://github.com/zchwang/IGModel)
- **固定 commit：** `2703fc3a1a2cf45357d990a93141ddeda7f38587`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 6

## 仓库摘要

该仓库是一个面向 protein–ligand interaction prediction 的静态代码/权重仓库：可见模型结构、特征生成脚本、两个 checkpoint 和 1bcu 示例输入，但未见训练入口、评估流水线或可验证的数据/模型独立许可。

## 可复用模块与资源

### checkpoints

- `models/saved_model.pth`
  - 能力：saved_model
  - 用途：已保存模型权重，适合加载进行推理/复现检查
  - 复用状态：partial；类型：model_weight
- `models/self-ref_model.pth`
  - 能力：self_ref_model
  - 用途：已保存模型权重，可能对应自引用/变体模型
  - 复用状态：partial；类型：model_weight

### datasets

- `samples/1bcu/1bcu_protein_atom_noHETATM.pdb`
  - 能力：demo_input_sample
  - 用途：1bcu 示例蛋白/配体输入，用于演示评分流程，不应视为训练基准集
  - 复用状态：partial；类型：unknown

### inference

- `scripts/generate_features.py`
  - 能力：feature_generation_inference
  - 用途：推理阶段特征生成；静态可见，但未证明端到端运行
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `scripts/model.py`
  - 能力：model_architecture
  - 用途：定义模型结构与前向计算骨架，可作为方法实现的核心代码资产
  - 复用状态：partial；类型：code_entry
- `scripts/generate_features.py`
  - 能力：inference_preprocess
  - 用途：生成推理所需特征/输入，是推理链路的一部分
  - 复用状态：partial；类型：code_entry

## 使用限制

- 仅做静态审查，未执行代码、未安装依赖、未运行测试
- 仓库中存在 checkpoint，但训练来源、训练数据和版本兼容性无法从静态清单确认
- 未见明确 evaluation 入口或 CI/test 证据
- 样例输入可见，但其原创性/外部来源/许可状态未知

## 仍未知

- scripts/scoring.py 是否构成完整端到端推理入口无法仅凭路径确认
- 模型权重与样例文件是否与代码同许可证边界未知
- samples/1bcu/ 更像 demo 输入而非正式数据集，是否可复用仍需人工核验
- 未见 training entrypoint 或 training module，是否存在外部训练脚本未纳入冻结清单未知

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
