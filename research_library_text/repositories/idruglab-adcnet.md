# idruglab/adcnet

- **仓库：** [https://github.com/idruglab/adcnet](https://github.com/idruglab/adcnet)
- **固定 commit：** `40ea7ec87cc820893f400d90710f70e6bafc1209`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 16

## 仓库摘要

该仓库是一个面向 antibody-drug conjugates 活性预测的静态推理型项目，包含模型定义、数据加载、推理脚本、若干表格/特征数据和两份 h5 权重；未发现训练与评测入口，且未找到 LICENSE，因此复用边界不清。

## 可复用模块与资源

### checkpoints

- `classification_weights/ADC_9.h5`
  - 能力：分类模型权重
  - 用途：ADCNet 分类/预测 checkpoint。
  - 复用状态：blocked；类型：model_weight
- `medium3_weights/bert_weightsMedium_20.h5`
  - 能力：BERT 权重
  - 用途：medium3_weights 目录下的预训练或微调权重。
  - 复用状态：blocked；类型：model_weight

### datasets

- `data.xlsx`
  - 能力：ADC 活性表格数据
  - 用途：表格型样本/标签数据；来源与划分语义无法仅凭静态清单确认。
  - 复用状态：blocked；类型：unknown
- `t_data.xlsx`
  - 能力：目标/测试表格数据
  - 用途：可能用于测试或目标集的表格数据；仅由文件名推断。
  - 复用状态：blocked；类型：unknown
- `files/data.xlsx`
  - 能力：嵌套数据表
  - 用途：重复或派生的表格数据副本，具体角色不明。
  - 复用状态：blocked；类型：unknown
- `files/Antigen_1280.pkl`
  - 能力：抗原特征缓存
  - 用途：Antigen 相关预计算特征或缓存对象。
  - 复用状态：blocked；类型：unknown
- `files/Heavy_1280.pkl`
  - 能力：重链特征缓存
  - 用途：Heavy chain 相关预计算特征或缓存对象。
  - 复用状态：blocked；类型：unknown
- `files/Light_1280.pkl`
  - 能力：轻链特征缓存
  - 用途：Light chain 相关预计算特征或缓存对象。
  - 复用状态：blocked；类型：unknown

### inference

- `inference.py`
  - 能力：推理入口
  - 用途：根据冻结权重与输入特征生成预测。
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `model.py`
  - 能力：模型架构
  - 用途：定义 ADC 活性预测的主模型结构。
  - 复用状态：blocked；类型：code_entry
- `dataset.py`
  - 能力：数据加载
  - 用途：样本读取、组装与预处理入口。
  - 复用状态：blocked；类型：code_entry
- `inference.py`
  - 能力：推理入口
  - 用途：加载模型/权重并输出预测结果。
  - 复用状态：blocked；类型：code_entry
- `ESM-2.py`
  - 能力：特征抽取脚本
  - 用途：疑似用于 ESM-2 序列/蛋白特征生成或调用；需读源码确认。
  - 复用状态：blocked；类型：code_entry
- `utils.py`
  - 能力：辅助工具
  - 用途：通用辅助函数。
  - 复用状态：blocked；类型：code_entry
- `class.py`
  - 能力：类别/分类辅助
  - 用途：疑似分类相关辅助模块；用途需结合源码确认。
  - 复用状态：blocked；类型：code_entry
- `py37.yaml`
  - 能力：环境配置
  - 用途：Python 3.7 运行环境/依赖说明。
  - 复用状态：blocked；类型：config

## 使用限制

- 仅做静态审查，未执行任何代码、训练或测试。
- 未见独立训练入口或训练日志，无法核验训练流程、超参与数据划分。
- 大文件可能为 promisor-only 或不完整拉取内容，静态存在不等于可完整使用。
- 依赖未安装，环境与运行时行为不可验证。
- 未发现 LICENSE，代码/数据/权重的复用边界不明确。

## 仍未知

- data.xlsx / t_data.xlsx / files/data.xlsx 的切分语义和来源未知。
- files/Antigen_1280.pkl / Heavy_1280.pkl / Light_1280.pkl 的生成方式和内容结构未知。
- ESM-2.py 是否为主特征提取入口，无法仅凭清单确认。
- class.py 与 utils.py 的具体职责及其在训练/推理中的调用关系未知。
- classification_weights/Explanation 与 medium3_weights/Explanation 的内容与用途未知。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
