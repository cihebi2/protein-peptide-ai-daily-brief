# Graylab/GeoDock

- **仓库：** [https://github.com/Graylab/GeoDock](https://github.com/Graylab/GeoDock)
- **固定 commit：** `df8d1f4c24ae2946655f27e7411ba2ffabf3d350`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 16

## 仓库摘要

静态审查显示 GeoDock 是一套面向 flexible protein-protein docking 的 MIT 许可代码仓库，包含核心模型、训练编排、评估工具、少量测试样例和一个 checkpoint；但未执行代码，也无法仅凭静态文件确认权重与数据的独立许可和端到端可复现性。

## 可复用模块与资源

### checkpoints

- `geodock/weights/dips_0.3.ckpt`
  - 能力：预训练权重
  - 用途：已打包的模型参数文件，可直接用于加载推理/微调。
  - 复用状态：partial；类型：model_weight

### datasets

- `geodock/data/test/a9_1a95.pdb1_3.dill_l_b_COMPLEX.pdb`
  - 能力：测试样例复合体（左链/受体侧）
  - 用途：本地测试输入样例之一。
  - 复用状态：partial；类型：unknown
- `geodock/data/test/a9_1a95.pdb1_3.dill_r_b_COMPLEX.pdb`
  - 能力：测试样例复合体（右链/配体侧）
  - 用途：与上一个样例配对的本地测试输入。
  - 复用状态：partial；类型：unknown

### evaluation

- `geodock/utils/metrics.py`
  - 能力：评估指标集合
  - 用途：汇总评估指标与打分逻辑。
  - 复用状态：ready_for_review；类型：code_entry
- `geodock/utils/compute_dockq.py`
  - 能力：DockQ 计算
  - 用途：计算 docking 质量指标。
  - 复用状态：ready_for_review；类型：code_entry

### inference

- `geodock/GeoDockRunner.py`
  - 能力：推理/运行封装
  - 用途：面向用户的预测运行入口。
  - 复用状态：partial；类型：code_entry
- `geodock/model/interface.py`
  - 能力：模型接口
  - 用途：为模型前向调用提供统一接口。
  - 复用状态：ready_for_review；类型：code_entry
- `geodock/utils/docking.py`
  - 能力：docking 工具链
  - 用途：执行 docking 相关的结构生成与整理。
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `geodock/model/GeoDock.py`
  - 能力：核心模型封装
  - 用途：主模型入口，连接图编码、迭代更新与结构输出。
  - 复用状态：ready_for_review；类型：code_entry
- `geodock/model/modules/graph_module.py`
  - 能力：图特征编码模块
  - 用途：构建图表示并进行消息传递/特征聚合。
  - 复用状态：ready_for_review；类型：code_entry
- `geodock/model/modules/iterative_transformer.py`
  - 能力：迭代式 Transformer 模块
  - 用途：迭代更新交互表征，是主模型的关键结构模块。
  - 复用状态：ready_for_review；类型：code_entry
- `geodock/model/modules/structure_module.py`
  - 能力：结构输出模块
  - 用途：把网络隐表示映射到结构/坐标层面的输出。
  - 复用状态：ready_for_review；类型：code_entry
- `geodock/utils/embed.py`
  - 能力：输入嵌入与特征构造
  - 用途：将原子/残基等输入映射为网络可用的特征表示。
  - 复用状态：ready_for_review；类型：code_entry

### training

- `geodock/trainer/train.py`
  - 能力：训练入口
  - 用途：训练命令入口与主训练流程启动。
  - 复用状态：ready_for_review；类型：code_entry
- `geodock/trainer/run.py`
  - 能力：训练编排
  - 用途：训练运行时封装与任务编排。
  - 复用状态：ready_for_review；类型：code_entry
- `geodock/trainer/config/config.yaml`
  - 能力：训练配置总入口
  - 用途：汇总 model、datamodule、trainer 等配置树。
  - 复用状态：ready_for_review；类型：config

## 使用限制

- 仅静态审查，未执行代码或测试。
- 依赖未安装，无法验证训练/推理链路。
- checkpoint 来源与训练数据未从静态文件中闭合确认。
- bundled data 与权重未见独立许可证声明。
- 仓库中存在推理与精修包装，但未确认端到端实际调用顺序。

## 仍未知

- GeoDockRunner.py 实际运行时是否默认加载 dips_0.3.ckpt。
- checkpoint 是否完全对应当前 commit 的代码与配置。
- 测试样例与 DB5 清单文件是否只是示例还是正式评测集切片。
- openmm_ref.py 与 pyrosetta_ref.py 在默认流程中的启用条件。
- 训练数据规模、来源与预处理细节未在静态清单中闭合。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
