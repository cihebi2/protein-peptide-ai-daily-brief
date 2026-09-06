# seferlab/deepptm

- **仓库：** [https://github.com/seferlab/deepptm](https://github.com/seferlab/deepptm)
- **固定 commit：** `46ba955fd2efdb35de8adc3ddcbe3d6978c787de`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 17

## 仓库摘要

仓库以 4 个 Jupyter notebooks、1 个预处理脚本和 6 个 Excel 数据表为主，围绕 BERT/ProtBert 向量构建与 1D/2D CNN + ViT 的 PTM 预测流程；冻结清单中未见 LICENSE、checkpoint 或独立训练/推理脚本，且未执行任何代码。

## 可复用模块与资源

### datasets

- `data/Crot_Human_cdhit40_Equal.xlsx`
  - 能力：PTM 样本表
  - 用途：从文件名看是 Human Crot 任务的 Excel 数据表，可作为样本/标签输入
  - 复用状态：blocked；类型：unknown
- `data/Gly_Human_cdhit40_Equal.xlsx`
  - 能力：PTM 样本表
  - 用途：从文件名看是 Human Gly 任务的 Excel 数据表，可作为样本/标签输入
  - 复用状态：blocked；类型：unknown
- `data/Suc_Human_cdhit40_Equal.xlsx`
  - 能力：PTM 样本表
  - 用途：从文件名看是 Human Suc 任务的 Excel 数据表，可作为样本/标签输入
  - 复用状态：blocked；类型：unknown
- `data/Suc_Mouse_cdhit40_Equal.xlsx`
  - 能力：PTM 样本表
  - 用途：从文件名看是 Mouse Suc 任务的 Excel 数据表，可作为样本/标签输入
  - 复用状态：blocked；类型：unknown
- `data/Suc_yeast_cdhit40_Equal.xlsx`
  - 能力：PTM 样本表
  - 用途：从文件名看是 Yeast Suc 任务的 Excel 数据表，可作为样本/标签输入
  - 复用状态：blocked；类型：unknown
- `data/Ubi_Human_cdhit40_Equal.xlsx`
  - 能力：PTM 样本表
  - 用途：从文件名看是 Human Ubi 任务的 Excel 数据表，可作为样本/标签输入
  - 复用状态：blocked；类型：unknown

### evaluation

- `BERT_1D_2D_CNN_and_ViT.ipynb`
  - 能力：评估流程（推定）
  - 用途：从命名看可能包含指标计算/对比评估，但未展开确认
  - 复用状态：blocked；类型：unknown
- `Protbert_1D_2D_CNN_and_ViT.ipynb`
  - 能力：评估流程（推定）
  - 用途：从命名看可能包含指标计算/对比评估，但未展开确认
  - 复用状态：blocked；类型：unknown

### inference

- `BERT_1D_2D_CNN_and_ViT.ipynb`
  - 能力：推理/预测流程（推定）
  - 用途：从命名看可能包含预测/推理单元，但未展开确认
  - 复用状态：blocked；类型：unknown
- `Protbert_1D_2D_CNN_and_ViT.ipynb`
  - 能力：推理/预测流程（推定）
  - 用途：从命名看可能包含预测/推理单元，但未展开确认
  - 复用状态：blocked；类型：unknown

### reusable_assets

- `processdata.py`
  - 能力：预处理/数据整理
  - 用途：从命名看是辅助读取、清洗或拼接样本与特征的脚本；未展开代码确认
  - 复用状态：blocked；类型：code_entry
- `BERT_Vector_Creation.ipynb`
  - 能力：BERT 表征构建
  - 用途：从序列生成 BERT 向量/特征的 notebook；未展开单元格确认
  - 复用状态：blocked；类型：unknown
- `Protbert_Vector_Creation.ipynb`
  - 能力：ProtBert 表征构建
  - 用途：从序列生成 ProtBert 向量/特征的 notebook；未展开单元格确认
  - 复用状态：blocked；类型：unknown
- `BERT_1D_2D_CNN_and_ViT.ipynb`
  - 能力：BERT + CNN + ViT 模型流程
  - 用途：从命名看包含 BERT、1D/2D CNN 与 ViT 的主模型 notebook，可能同时承载训练/推理/评估
  - 复用状态：blocked；类型：unknown
- `Protbert_1D_2D_CNN_and_ViT.ipynb`
  - 能力：ProtBert + CNN + ViT 模型流程
  - 用途：从命名看包含 ProtBert、1D/2D CNN 与 ViT 的主模型 notebook，可能同时承载训练/推理/评估
  - 复用状态：blocked；类型：unknown

### training

- `BERT_1D_2D_CNN_and_ViT.ipynb`
  - 能力：训练入口（推定）
  - 用途：从命名看是 BERT + 1D/2D CNN + ViT 的训练 notebook；未展开单元格确认
  - 复用状态：blocked；类型：unknown
- `Protbert_1D_2D_CNN_and_ViT.ipynb`
  - 能力：训练入口（推定）
  - 用途：从命名看是 ProtBert + 1D/2D CNN + ViT 的训练 notebook；未展开单元格确认
  - 复用状态：blocked；类型：unknown

## 使用限制

- 仅做静态清单审计，未执行 notebook、脚本、测试或模型推理。
- 仓库未见 LICENSE，代码、笔记本和数据的直接复用受限。
- requirements.txt 存在，但依赖未安装，环境可复现性未知。
- 冻结快照可能遗漏未拉取的大文件或外部下载资源。

## 仍未知

- 未展开 notebook 内容，无法确认是否确实覆盖完整训练-推理-评估闭环。
- data/*.xlsx 的具体划分、标签定义和来源未确认。
- 是否存在外部下载的权重、缓存或运行时生成文件未确认。
- processdata.py 的具体接口、输入输出和副作用未检查。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
