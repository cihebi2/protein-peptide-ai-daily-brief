# luozhenjie1997/CPL-Diff

- **仓库：** [https://github.com/luozhenjie1997/CPL-Diff](https://github.com/luozhenjie1997/CPL-Diff)
- **固定 commit：** `35629aaa788295e23bad6a75843469df8ce00465`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 11

## 仓库摘要

仓库以固定长度功能肽的扩散生成器为核心，包含训练/采样脚本、若干已保存权重和多来源肽数据；代码许可清晰，但数据与模型权重边界仍需单独核验。

## 可复用模块与资源

### checkpoints

- `save_model/denoise_model.pkl`
  - 能力：project_trained_weights
  - 用途：已保存的 denoiser 权重
  - 复用状态：partial；类型：unknown
- `ESM2-8M/pytorch_model.bin`
  - 能力：vendor_pretrained_backbone
  - 用途：预训练 ESM-2-8M 编码器权重
  - 复用状态：unknown；类型：unknown

### datasets

- `data/AMP/apd3_Antibacterial.fasta`
  - 能力：raw_peptide_corpora
  - 用途：原始肽语料汇编，覆盖 AMP/AVP/AFP 与 CAMP 子集
  - 复用状态：unknown；类型：unknown
- `data/train/mulit_peptide_train.csv`
  - 能力：processed_training_data
  - 用途：训练/验证拆分后的生成任务语料
  - 复用状态：partial；类型：unknown
- `data/train/antimicrobial_esm_embedding_umap.npy`
  - 能力：analysis_embeddings
  - 用途：ESM embedding 的 t-SNE/UMAP 可视化与分布分析
  - 复用状态：partial；类型：unknown

### inference

- `scripts/sample_randomLen.ipynb`
  - 能力：sampling_generation
  - 用途：随机长度采样与序列生成
  - 复用状态：partial；类型：unknown

### reusable_assets

- `CPLDiff/models/Denoiser.py`
  - 能力：model_architecture
  - 用途：扩散 denoiser 主体与条件嵌入
  - 复用状态：ready_for_review；类型：code_entry
- `CPLDiff/utils/CPLDiffDataset.py`
  - 能力：data_pipeline
  - 用途：样本读取、数据集封装与训练输入组装
  - 复用状态：ready_for_review；类型：code_entry
- `environment.yml`
  - 能力：dependencies
  - 用途：环境与依赖声明
  - 复用状态：ready_for_review；类型：config

### training

- `scripts/train_decoder.py`
  - 能力：decoder_training
  - 用途：decoder 训练入口
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/train_denoiser.ipynb`
  - 能力：denoiser_training_notebook
  - 用途：denoiser 训练 notebook
  - 复用状态：partial；类型：unknown

## 使用限制

- 仅做静态清点，未执行仓库代码或 notebook
- dependencies 未安装，训练/推断流程未验证
- tests 未运行，未发现 CI 证据
- submodules 未初始化
- 大型 blob 可能只是 promisor 占位，不能当作可复现证明

## 仍未知

- 原始 `data/` 语料的下载来源、去重规则和许可证未在静态清单中确认
- `ESM2-8M/` 权重是否为第三方 vendored 资产及其具体许可未核验
- `save_model/*.pkl` 是否为最终论文模型、训练数据对应关系和超参未核验
- 未发现独立 evaluation 入口，性能指标只能从外部论文或进一步代码审计确认

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
