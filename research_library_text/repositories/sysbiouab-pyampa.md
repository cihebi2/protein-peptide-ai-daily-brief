# SysBioUAB/PyAMPA

- **仓库：** [https://github.com/SysBioUAB/PyAMPA](https://github.com/SysBioUAB/PyAMPA)
- **固定 commit：** `47e65b4b04be366a14fbc02431fb81c22f5d3cbe`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 16

## 仓库摘要

仓库包含 PyAMPA 的推断入口、核心脚本、验证工件、多个序列分类模型/向量器以及一个 FASTA 数据文件；代码许可可确认是 MIT，但模型与数据的独立许可和训练来源仍未被静态证据证明。

## 可复用模块与资源

### checkpoints

- `activities_model.pkl`
  - 能力：activity 分类模型 checkpoint
  - 用途：活动相关预测模型的序列化状态
  - 复用状态：partial；类型：unknown
- `activities_vectorizer.pkl`
  - 能力：activity 特征向量器 checkpoint
  - 用途：活动相关模型配套的特征向量化状态
  - 复用状态：partial；类型：unknown
- `cpp_model.pkl`
  - 能力：CPP 分类模型 checkpoint
  - 用途：cell-penetrating peptide 相关预测模型的序列化状态
  - 复用状态：partial；类型：unknown
- `cpp_vectorizer.pkl`
  - 能力：CPP 特征向量器 checkpoint
  - 用途：CPP 模型配套的特征向量化状态
  - 复用状态：partial；类型：unknown
- `hemolysis_model.pkl`
  - 能力：hemolysis 分类模型 checkpoint
  - 用途：溶血相关预测模型的序列化状态
  - 复用状态：partial；类型：unknown
- `hemolysis_vectorizer.pkl`
  - 能力：hemolysis 特征向量器 checkpoint
  - 用途：溶血模型配套的特征向量化状态
  - 复用状态：partial；类型：unknown
- `tox_model.pkl`
  - 能力：toxicity 分类模型 checkpoint
  - 用途：毒性相关预测模型的序列化状态
  - 复用状态：partial；类型：unknown
- `tox_vectorizer.pkl`
  - 能力：toxicity 特征向量器 checkpoint
  - 用途：毒性模型配套的特征向量化状态
  - 复用状态：partial；类型：unknown
- `label_encoder.pkl`
  - 能力：标签编码器 checkpoint
  - 用途：输出标签或类别编码的持久化对象
  - 复用状态：partial；类型：unknown

### datasets

- `proteome.fasta`
  - 能力：蛋白序列输入集
  - 用途：FASTA 格式蛋白序列背景/输入资源，可能用于扫描或筛选
  - 复用状态：partial；类型：unknown

### evaluation

- `AMPValidate.pkl`
  - 能力：验证模型工件
  - 用途：验证/评估用序列分类器或判别器
  - 复用状态：partial；类型：unknown
- `amp_validate_vectorizer.pkl`
  - 能力：验证特征向量器
  - 用途：与验证模型配套的特征提取/向量化对象
  - 复用状态：partial；类型：unknown
- `validate.png`
  - 能力：验证结果图
  - 用途：验证/评估相关图像资源或结果展示
  - 复用状态：partial；类型：unknown

### inference

- `main.py`
  - 能力：命令入口/推断入口
  - 用途：程序主入口，按命名推断负责加载模型并执行预测/优化流程
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `pyampa.py`
  - 能力：核心方法模块
  - 用途：PyAMPA 的核心流程与工具函数，供入口脚本调用
  - 复用状态：ready_for_review；类型：code_entry
- `comprovacio.py`
  - 能力：验证/检查辅助脚本
  - 用途：按文件名看是检查或验证流程辅助逻辑
  - 复用状态：partial；类型：code_entry

## 使用限制

- 仅做静态清点，未执行代码、未安装依赖、未跑测试。
- 仓库中存在多个 `.pkl` 序列化工件，但其训练数据、训练环境与可反序列化兼容性未被证明。
- 没有发现明确的训练入口或可复现的再训练流水线。

## 仍未知

- `proteome.fasta` 的来源、构造方式与许可未在静态库存中明确。
- `AMPValidate.pkl` 等验证工件是否对应论文中的正式评估流程，无法仅凭路径确认。
- README 的声明未被执行验证，无法据此证明运行结果或复现性。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
