# ABILiLab/LncTracker

- **仓库：** [https://github.com/ABILiLab/LncTracker](https://github.com/ABILiLab/LncTracker)
- **固定 commit：** `ed0f00d04d30188944156cc0f4bab0df059d4fd8`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 15

## 仓库摘要

该仓库是 LncTracker 论文的配套代码与资源包，静态清单显示包含模型、数据加载、评估脚本、训练/预测入口、示例数据、预计算特征和两个 checkpoint；但未发现 LICENSE，且未执行任何代码，因此只能做静态可复用性盘点，不能据此认定可直接复现或可合法复用。

## 可复用模块与资源

### checkpoints

- `checkpoints/model_final.pth`
  - 能力：model weights checkpoint
  - 用途：训练完成后的模型权重
  - 复用状态：blocked；类型：model_weight
- `checkpoints/tokenizer.pkl`
  - 能力：tokenizer checkpoint
  - 用途：与模型配套的 tokenizer / 词表序列化文件
  - 复用状态：blocked；类型：tokenizer

### datasets

- `data/example.fasta`
  - 能力：example sequence input
  - 用途：仓库示例 FASTA 输入
  - 复用状态：blocked；类型：unknown
- `data/lncRNA`
  - 能力：bundled lncRNA data directory
  - 用途：项目内 lncRNA 数据目录，可能用于训练/评估
  - 复用状态：blocked；类型：unknown
- `data/lncRNA_6000`
  - 能力：bundled lncRNA data directory
  - 用途：项目内 lncRNA 数据目录，可能为另一份样本集或规模版本
  - 复用状态：blocked；类型：unknown
- `features/lnctracker_5mer.pkl`
  - 能力：precomputed feature blob
  - 用途：5-mer 特征的预计算数据
  - 复用状态：blocked；类型：unknown
- `features/lnctracker_cksnap.pkl`
  - 能力：precomputed feature blob
  - 用途：CKSNAP 特征的预计算数据
  - 复用状态：blocked；类型：unknown
- `features/lnctracker_foldings.pkl`
  - 能力：precomputed feature blob
  - 用途：folding 相关特征的预计算数据
  - 复用状态：blocked；类型：unknown

### evaluation

- `metrics.py`
  - 能力：evaluation metrics
  - 用途：评估指标与结果统计
  - 复用状态：blocked；类型：code_entry

### inference

- `run_predict.py`
  - 能力：inference entrypoint
  - 用途：预测/推理入口脚本（仅按静态路径识别，未执行验证）
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `model.py`
  - 能力：model architecture
  - 用途：定义 LncTracker 的模型结构与前向计算
  - 复用状态：blocked；类型：code_entry
- `data.py`
  - 能力：data loading pipeline
  - 用途：数据读取、切分或批处理相关逻辑
  - 复用状态：blocked；类型：code_entry
- `environment.yml`
  - 能力：runtime environment recipe
  - 用途：记录依赖与环境构建方式
  - 复用状态：blocked；类型：config
- `linearfold_v`
  - 能力：RNA folding helper
  - 用途：折叠相关特征/外部工具调用的可执行文件，具体作用仅据文件名推断
  - 复用状态：unknown；类型：unknown

### training

- `run_train.py`
  - 能力：training entrypoint
  - 用途：训练入口脚本（仅按静态路径识别，未执行验证）
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态审查，未执行代码、未跑测试、未安装依赖
- 仓库内缺少显式 LICENSE，直接复用边界不清
- 路径存在不等于可运行或可复现
- 大型二进制/权重可能是未展开或不可完全核验的 blob
- 数据集、特征文件和 checkpoint 的来源与训练流程未被验证

## 仍未知

- run_train.py 与 run_predict.py 的实际参数、I/O 和可运行性未知
- data/lncRNA 与 data/lncRNA_6000 的真实来源、许可与划分方式未知
- features/*.pkl 的生成方式及是否来自外部工具未知
- linearfold_v 是否为 vendored third-party 二进制未知
- checkpoints/model_final.pth 的训练数据、训练轮次和性能未验证

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
