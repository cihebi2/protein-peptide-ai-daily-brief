# CDDLeiden/PCMol

- **仓库：** [https://github.com/CDDLeiden/PCMol](https://github.com/CDDLeiden/PCMol)
- **固定 commit：** `6e2bd12bd7455e2a81c57032f2ef46fe2d30e8c5`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 17

## 仓库摘要

该仓库对应论文实现，包含分子生成模型、AlphaFold/Papyrus 相关预处理、训练/生成/评估脚本，以及少量 bundled data；静态清单未见已追踪 checkpoint，代码许可为 MIT，但数据与模型工件的独立许可未确认。

## 可复用模块与资源

### datasets

- `data/alphafold/emb_max.npy`
  - 能力：AlphaFold embedding 上界数组
  - 用途：存放预计算结构特征的上界参考
  - 复用状态：partial；类型：unknown
- `data/alphafold/emb_min.npy`
  - 能力：AlphaFold embedding 下界数组
  - 用途：存放预计算结构特征的下界参考
  - 复用状态：partial；类型：unknown
- `data/targets.txt`
  - 能力：target 清单
  - 用途：提供条件生成或筛选所需的 target 列表
  - 复用状态：partial；类型：unknown
- `data/training/final_dataset/voc_smiles.txt`
  - 能力：training 词表/SMILES 语料
  - 用途：提供训练阶段用的 SMILES vocabulary 或语料
  - 复用状态：partial；类型：unknown

### evaluation

- `pcmol/utils/evaluate.py`
  - 能力：评估流程
  - 用途：汇总生成结果并计算指标
  - 复用状态：ready_for_review；类型：code_entry
- `pcmol/utils/metrics.py`
  - 能力：指标定义
  - 用途：定义评估指标
  - 复用状态：ready_for_review；类型：code_entry

### inference

- `pcmol/generate.py`
  - 能力：生成入口脚本
  - 用途：执行分子生成与采样
  - 复用状态：ready_for_review；类型：code_entry
- `notebooks/generate.ipynb`
  - 能力：推理示例 notebook
  - 用途：展示生成流程
  - 复用状态：ready_for_review；类型：unknown

### reusable_assets

- `pcmol/models/transformer.py`
  - 能力：核心生成模型
  - 用途：实现条件分子生成的主体网络
  - 复用状态：ready_for_review；类型：code_entry
- `pcmol/models/components.py`
  - 能力：模型组件
  - 用途：提供网络层与子模块
  - 复用状态：ready_for_review；类型：code_entry
- `pcmol/models/runner.py`
  - 能力：模型运行封装
  - 用途：组织训练、采样与前向流程
  - 复用状态：ready_for_review；类型：code_entry
- `pcmol/alphafold/batch_process.py`
  - 能力：AlphaFold/Papyrus 数据预处理
  - 用途：批量整理结构或嵌入相关输入
  - 复用状态：ready_for_review；类型：code_entry
- `pcmol/alphafold/papyrus.py`
  - 能力：AlphaFold/Papyrus 数据适配
  - 用途：连接 Papyrus 侧化学数据与结构特征
  - 复用状态：ready_for_review；类型：code_entry
- `pcmol/utils/standardizers.py`
  - 能力：SMILES 标准化
  - 用途：统一分子输入格式
  - 复用状态：ready_for_review；类型：code_entry
- `pcmol/utils/smiles_enumerator.py`
  - 能力：SMILES 枚举
  - 用途：生成字符串变体与增强样本
  - 复用状态：ready_for_review；类型：code_entry
- `pcmol/utils/dataset.py`
  - 能力：蛋白/分子数据集加载
  - 用途：读取训练样本并喂给训练流程
  - 复用状态：ready_for_review；类型：code_entry

### training

- `pcmol/train.py`
  - 能力：训练入口
  - 用途：启动模型训练与参数组织
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态审查，未运行代码、训练或测试
- 依赖未安装，无法验证入口可执行性
- 未追踪到 checkpoint 文件，无法核实权重
- bundled data 与潜在模型工件未见独立许可声明

## 仍未知

- `data/alphafold/*.npy` 的生成来源和再分发条件未从静态清单确认
- `data/training/final_dataset/voc_smiles.txt` 是否为训练语料还是中间词表，当前仅能按路径推断
- `notebooks/generate.ipynb` 是示例还是正式推理流程，未执行验证
- 是否存在未追踪的大文件模型权重无法由当前清单排除

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
