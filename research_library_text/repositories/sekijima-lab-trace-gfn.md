# sekijima-lab/trace-gfn

- **仓库：** [https://github.com/sekijima-lab/trace-gfn](https://github.com/sekijima-lab/trace-gfn)
- **固定 commit：** `ca5cf1a8707e5a45f71afcb156dab295d975d7bc`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 20

## 仓库摘要

仓库实现了面向 QSAR 导向分子设计的 GFlowNet/Transformer/GCN 代码，并附带目标数据与若干序列化模型；代码许可清晰，但数据与权重的独立许可边界未被静态证实。

## 可复用模块与资源

### checkpoints

- `src/gflownet/models/ckpts/GCN/GCN.pth`
  - 能力：GCN checkpoint
  - 用途：打包的 GCN 权重，用于性质预测。
  - 复用状态：partial；类型：model_weight
- `src/gflownet/models/qsar_AKT1_optimized.pkl`
  - 能力：AKT1 optimized QSAR model
  - 用途：序列化的 AKT1 性质预测模型。
  - 复用状态：partial；类型：unknown
- `src/gflownet/models/qsar_CXCR4_optimized.pkl`
  - 能力：CXCR4 optimized QSAR model
  - 用途：序列化的 CXCR4 性质预测模型。
  - 复用状态：partial；类型：unknown
- `src/gflownet/models/qsar_DRD2_optimized.pkl`
  - 能力：DRD2 optimized QSAR model
  - 用途：序列化的 DRD2 性质预测模型。
  - 复用状态：partial；类型：unknown

### datasets

- `src/gflownet/data/AKT1/akt1_train.csv`
  - 能力：AKT1 QSAR 数据集
  - 用途：AKT1 任务的训练/测试划分与起始化合物，用于靶点导向分子设计。
  - 复用状态：partial；类型：unknown
- `src/gflownet/data/CXCR4/cxcr4_train.csv`
  - 能力：CXCR4 QSAR 数据集
  - 用途：CXCR4 任务的训练/测试划分与起始化合物。
  - 复用状态：partial；类型：unknown
- `src/gflownet/data/DRD2/drd2_train.csv`
  - 能力：DRD2 QSAR 数据集
  - 用途：DRD2 任务的训练/测试划分与起始化合物。
  - 复用状态：partial；类型：unknown
- `src/gflownet/data/USPTO/src_train.txt`
  - 能力：USPTO 反应语料
  - 用途：reaction-aware Transformer 的训练/验证/测试反应文本。
  - 复用状态：partial；类型：unknown

### evaluation

- `src/gflownet/utils/metrics.py`
  - 能力：评估指标
  - 用途：评估生成结果、性质命中或多目标分数。
  - 复用状态：ready_for_review；类型：code_entry
- `src/gflownet/evals/evals.py`
  - 能力：评估入口
  - 用途：封装实验评估流程。
  - 复用状态：ready_for_review；类型：code_entry

### inference

- `src/gflownet/models/Transformer/beam_search.py`
  - 能力：Transformer 束搜索解码
  - 用途：为序列生成提供候选解码。
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `src/gflownet/algo/trajectory_balance_synthesis.py`
  - 能力：GFlowNet 候选分子生成与轨迹平衡
  - 用途：核心 trajectory balance 生成/优化逻辑，支撑候选分子探索。
  - 复用状态：ready_for_review；类型：code_entry
- `src/gflownet/algo/reaction_sampling.py`
  - 能力：反应感知采样
  - 用途：按反应状态抽样轨迹/动作，供生成循环使用。
  - 复用状态：ready_for_review；类型：code_entry
- `src/gflownet/models/Transformer/model.py`
  - 能力：Transformer 序列生成模型
  - 用途：实现 reaction-aware Transformer 主体。
  - 复用状态：ready_for_review；类型：code_entry
- `src/gflownet/models/GCN/network.py`
  - 能力：图表示与 QSAR 预测网络
  - 用途：实现 GCN 结构，用于目标性质/亲和力预测。
  - 复用状态：ready_for_review；类型：code_entry
- `src/gflownet/data/replay_buffer.py`
  - 能力：回放缓冲与采样迭代器
  - 用途：保存与重放轨迹/样本，支持在线训练。
  - 复用状态：ready_for_review；类型：code_entry
- `src/gflownet/utils/conditioning.py`
  - 能力：条件控制与多目标约束
  - 用途：处理条件变量与目标约束。
  - 复用状态：ready_for_review；类型：code_entry

### training

- `src/gflownet/models/GCN/train.py`
  - 能力：GCN 训练入口
  - 用途：训练 AKT1/CXCR4/DRD2 的 QSAR 预测器。
  - 复用状态：ready_for_review；类型：code_entry
- `src/gflownet/models/Transformer/train.py`
  - 能力：Transformer 训练入口
  - 用途：训练 reaction-aware Transformer。
  - 复用状态：ready_for_review；类型：code_entry
- `src/gflownet/trainer.py`
  - 能力：训练编排器
  - 用途：协调在线/离线训练与 GFlowNet 更新。
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅基于冻结清单做静态审查，未执行代码、未跑测试、未验证训练/推理效果。
- 依赖未安装，submodule 未初始化，且大文件可能只是 promisor blob。
- 路径存在不等于可复现，也不等于模型/数据已成功训练或可直接推理。

## 仍未知

- AKT1/CXCR4/DRD2 CSV 与 USPTO 文本数据的原始来源和独立许可未能从清单中确认。
- `GCN.pth` 与 `qsar_*.pkl` 是否为项目自训练产物、外部导入或再打包资产，无法仅凭静态清单判定。
- 未见独立配置 recipe；`beam_search.py` 等推理辅助代码是否对应公开 CLI 入口未能确认。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
