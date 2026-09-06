# aaai-2025-submission/anomymous_submission_aaai2025

- **仓库：** [https://github.com/aaai-2025-submission/anomymous_submission_aaai2025](https://github.com/aaai-2025-submission/anomymous_submission_aaai2025)
- **固定 commit：** `ee6e69c65fd251dc15b49f167cebd62a9ad02631`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0
- **资产记录数：** 20

## 仓库摘要

该仓库是 OmicsFUSION 的静态代码清单：含 DNA/omics 预处理、Hyena/模型定义、训练/推理/测试脚本；未见 tracked 数据集或 checkpoint，许可为 GPL-3.0。

## 可复用模块与资源

### evaluation

- `OmicsFUSION/train_model/embedding_test.py`
  - 能力：embedding评估
  - 用途：评估 embedding 相关训练结果
  - 复用状态：partial；类型：code_entry
- `OmicsFUSION/train_model/full_model_test.py`
  - 能力：full模型评估
  - 用途：评估完整模型流程
  - 复用状态：partial；类型：code_entry
- `OmicsFUSION/tests/run_lit_encoder_tests.py`
  - 能力：encoder测试套件
  - 用途：运行编码器相关测试
  - 复用状态：partial；类型：code_entry
- `OmicsFUSION/commands/768_hg38_65536_embedding_test.sh`
  - 能力：评估脚本封装
  - 用途：封装特定配置下的 embedding 测试命令
  - 复用状态：partial；类型：code_entry

### inference

- `OmicsFUSION/train_model/model_predict_omics.py`
  - 能力：omics推理
  - 用途：对 omics 输入执行预测/推断
  - 复用状态：partial；类型：code_entry
- `OmicsFUSION/commands/768_hg38_65536_model_predict.sh`
  - 能力：推理脚本封装
  - 用途：封装特定配置下的模型预测命令
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `OmicsFUSION/data_preparation/dna_generator.py`
  - 能力：DNA预处理
  - 用途：生成或整理 DNA 输入样本
  - 复用状态：ready_for_review；类型：code_entry
- `OmicsFUSION/data_preparation/interval_preparator.py`
  - 能力：区间预处理
  - 用途：构造基因组区间与训练样本切片
  - 复用状态：ready_for_review；类型：code_entry
- `OmicsFUSION/data_preparation/omics_generator.py`
  - 能力：omics特征生成
  - 用途：生成或整理 omics 输入特征
  - 复用状态：ready_for_review；类型：code_entry
- `OmicsFUSION/data_utils/base_dataset.py`
  - 能力：数据集抽象
  - 用途：提供通用 Dataset 基类
  - 复用状态：ready_for_review；类型：code_entry
- `OmicsFUSION/data_utils/base_datamodule.py`
  - 能力：数据模块抽象
  - 用途：提供通用 DataModule 基类
  - 复用状态：ready_for_review；类型：code_entry
- `OmicsFUSION/data_utils/embedding_dataset.py`
  - 能力：embedding数据集
  - 用途：承载 embedding 训练/测试样本
  - 复用状态：partial；类型：code_entry
- `OmicsFUSION/dl_utils/hyena_model.py`
  - 能力：Hyena模型定义
  - 用途：实现 Hyena 相关网络结构
  - 复用状态：ready_for_review；类型：code_entry
- `OmicsFUSION/dl_utils/models.py`
  - 能力：模型组合与封装
  - 用途：组织主要模型组件与前向逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `OmicsFUSION/dl_utils/lightning_modules.py`
  - 能力：训练封装
  - 用途：封装 PyTorch Lightning 训练模块
  - 复用状态：partial；类型：code_entry

### training

- `OmicsFUSION/commands/model_train.sh`
  - 能力：主训练启动
  - 用途：启动主训练流程
  - 复用状态：partial；类型：code_entry
- `OmicsFUSION/commands/model_train_sm.sh`
  - 能力：小规模训练启动
  - 用途：启动小规模/快速训练流程
  - 复用状态：partial；类型：code_entry
- `OmicsFUSION/train_model/model_train.py`
  - 能力：训练调度
  - 用途：组织训练入口与参数流转
  - 复用状态：partial；类型：code_entry
- `OmicsFUSION/train_model/embedding_train.py`
  - 能力：embedding训练
  - 用途：训练 embedding 相关模型
  - 复用状态：partial；类型：code_entry
- `OmicsFUSION/train_model/full_model_train.py`
  - 能力：full模型训练
  - 用途：训练完整模型流程
  - 复用状态：partial；类型：code_entry

## 使用限制

- 仅做静态清单审查，未执行代码、未安装依赖、未运行测试。
- 未见 tracked datasets 或 checkpoints，数据来源与权重可复用性无法从冻结清单确认。
- 仓库中命令脚本按 hg38/mm10 与不同窗口长度命名，说明存在多配置实验封装，但不能据此确认实际实验已复现。
- 单靠路径存在不能证明文件是项目原创、vendored 还是已改写。

## 仍未知

- README 未出现在冻结清单中，实验协议与参数说明不完整。
- 训练/推理脚本依赖的外部输入、环境变量和数据目录未冻结。
- 是否存在未列出的大文件、外部下载器或隐藏权重，当前无法确认。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
