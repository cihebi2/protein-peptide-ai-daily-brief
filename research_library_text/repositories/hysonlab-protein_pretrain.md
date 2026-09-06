# HySonLab/Protein_Pretrain

- **仓库：** [https://github.com/HySonLab/Protein_Pretrain](https://github.com/HySonLab/Protein_Pretrain)
- **固定 commit：** `88b7a1366377318b8ae359eb523dd583a5e39261`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 5

## 仓库摘要

该仓库静态上仅能确认多模态蛋白预训练相关的模型与数据加载代码，以及少量下游任务数据模块；未发现可执行训练入口、推理、评测或 checkpoint 文件，且冻结库存未提供许可证文件，直接复用受限。

## 可复用模块与资源

### reusable_assets

- `model/Auto_Fusion.py`
  - 能力：multimodal protein pretraining model modules
  - 用途：构成蛋白多模态预训练的模型骨架与特征融合模块
  - 复用状态：blocked；类型：code_entry
- `pretrain/data/Fusion.py`
  - 能力：pretraining data loaders
  - 用途：提供融合、图、点云和序列四类预训练输入管线
  - 复用状态：blocked；类型：code_entry
- `downstreamtasks/data/EI.py`
  - 能力：downstream task data loaders and augmentation helper
  - 用途：支撑四个下游任务的数据读取与随机变换
  - 复用状态：blocked；类型：code_entry
- `downstreamtasks/EI.py`
  - 能力：downstream task scripts
  - 用途：从文件名看像下游任务封装与公共工具脚本；仅能确认路径存在，具体职责未静态验证
  - 复用状态：blocked；类型：code_entry

### training

- `model/Auto_Fusion.py`
  - 能力：pretraining stack without confirmed entrypoint
  - 用途：支撑多模态蛋白预训练的模型与输入管线；冻结库存未见 `train`/`main` 类入口，不能据此确认完整训练流程
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态清单审查；未安装依赖、未运行代码、未执行测试。
- 冻结库存未见可验证的训练入口、推理入口、评测脚本或 checkpoint 文件。
- 路径存在不等于可运行或可复现。
- 无 LICENSE 文件，直接复用受限。
- `downstreamtasks/EI.py` 等脚本的真实职责仅凭文件名判断，未做静态语义验证。

## 仍未知

- `README.md` 的具体说明内容未在当前冻结输出中展开。
- `model/ESM.py` 是否封装或移植了第三方实现，静态库存无法确认。
- 下游数据是否依赖外部下载源、其许可和版本未显式列出。
- `downstreamtasks/EI.py`、`MSP.py`、`PFC.py`、`PLA.py` 是否承担训练、验证还是评测入口，未验证。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
