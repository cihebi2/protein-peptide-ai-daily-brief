# adrienmialland/ProtFitTrans

- **仓库：** [https://github.com/adrienmialland/ProtFitTrans](https://github.com/adrienmialland/ProtFitTrans)
- **固定 commit：** `ae4c731825a11463e8589b379d4d842ceec00c2d`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 8

## 仓库摘要

冻结清单只显示少量脚本、一个FASTA 数据集和一个 .pt 嵌入产物；未发现可验证的训练、推理或评估入口，且没有 LICENSE 文件。

## 可复用模块与资源

### checkpoints

- `data/IGPS_ss_tm_tt/embeddings_esm2_t33_650M_UR50D/IGPS_ss_tm_tt__esm2_t33_650M_UR50D__embs_0.pt`
  - 能力：embedding cache / tensor artifact
  - 用途：疑似 ESM2 生成的序列嵌入缓存或特征张量；仅从路径命名推断，不视为已验证模型权重。
  - 复用状态：blocked；类型：model_weight

### datasets

- `data/IGPS_ss_tm_tt.fasta`
  - 能力：sequence dataset
  - 用途：IGPS_ss_tm_tt 的 FASTA 序列集合，可能供特征提取或变体预测使用；标签与来源未核实。
  - 复用状态：blocked；类型：unknown

### reusable_assets

- `Scripts/Embeddings_Extract.py`
  - 能力：embedding extraction script
  - 用途：从文件名看，负责把序列转换为 embedding/特征；未执行验证。
  - 复用状态：blocked；类型：code_entry
- `Scripts/Variant_Predictor.py`
  - 能力：variant prediction script
  - 用途：从文件名看，承载变体效应/fitness 预测逻辑；未执行验证。
  - 复用状态：blocked；类型：code_entry
- `Scripts/manager.py`
  - 能力：pipeline helper
  - 用途：从文件名看，管理流程、参数或任务编排；具体职责未核实。
  - 复用状态：blocked；类型：code_entry
- `Scripts/runner.py`
  - 能力：run wrapper
  - 用途：从文件名看，封装运行入口或批处理；未执行验证。
  - 复用状态：blocked；类型：code_entry
- `launcher.py`
  - 能力：top-level launcher
  - 用途：从文件名看，提供项目顶层启动入口。
  - 复用状态：blocked；类型：code_entry
- `requirements.txt`
  - 能力：dependency manifest
  - 用途：静态依赖清单，可用于环境审阅；未安装依赖，也未验证可复现性。
  - 复用状态：blocked；类型：unknown

## 使用限制

- 仅做静态清单，不执行代码、不安装依赖。
- 训练、推理、评估入口在冻结 inventory 中未出现。
- .pt 资产可能是缓存嵌入而非模型 checkpoint。
- README 具体内容未展开，文件名推断存在不确定性。

## 仍未知

- data/IGPS_ss_tm_tt.fasta 的来源、标签与许可未确认。
- .pt 资产是模型权重、特征缓存还是推断产物未确认。
- Scripts/*.py 的具体实现与 CLI 参数仅能从文件名推断。
- 是否存在外部下载器或生成流程未确认。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
