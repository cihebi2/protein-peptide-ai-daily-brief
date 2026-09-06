# pnumlb/aptatrans

- **仓库：** [https://github.com/pnumlb/aptatrans](https://github.com/pnumlb/aptatrans)
- **固定 commit：** `59a8a8f618edde57a72555950b7c61c9c64b54fe`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 18

## 仓库摘要

该冻结仓库是 AptaTrans 的实现型代码库，主要覆盖训练、预训练、推理管线、默认配置、若干 checkpoint 以及两个 pickle 数据文件；静态审查未见 LICENSE，且未执行代码或测试，因此复用边界只能保守判断。

## 可复用模块与资源

### checkpoints

- `models/default/conv_best_auc.pt`
  - 能力：model_weight
  - 用途：卷积分支最佳 AUC 权重
  - 复用状态：unknown；类型：model_weight
- `models/default/encoder_apta_best_auc.pt`
  - 能力：model_weight
  - 用途：Apta 编码器最佳 AUC 权重
  - 复用状态：unknown；类型：model_weight
- `models/default/encoder_prot_best_auc.pt`
  - 能力：model_weight
  - 用途：Protein 编码器最佳 AUC 权重
  - 复用状态：unknown；类型：model_weight
- `models/default/predictor_best_auc.pt`
  - 能力：model_weight
  - 用途：预测头/分类器最佳 AUC 权重
  - 复用状态：unknown；类型：model_weight
- `models/default/pretrained_encoder_protein.pt`
  - 能力：model_weight
  - 用途：Protein 预训练编码器权重
  - 复用状态：unknown；类型：model_weight
- `models/default/pretrained_encoder_rna.pt`
  - 能力：model_weight
  - 用途：RNA/aptamer 预训练编码器权重
  - 复用状态：unknown；类型：model_weight
- `models/default/to_im_best_auc.pt`
  - 能力：model_weight
  - 用途：to_im 变体最佳 AUC 权重；具体结构未核验
  - 复用状态：unknown；类型：model_weight

### datasets

- `data/dataset_li.pickle`
  - 能力：dataset
  - 用途：疑似主数据集或样本索引；仅能按文件名静态推断
  - 复用状态：unknown；类型：unknown
- `data/protein_word_freq_3.pickle`
  - 能力：dataset
  - 用途：蛋白词频统计/词表缓存；仅能按文件名静态推断
  - 复用状态：unknown；类型：unknown

### evaluation

- `example.ipynb`
  - 能力：example_notebook
  - 用途：示例 notebook；更像演示或手工复现，不足以证明正式评测脚本
  - 复用状态：blocked；类型：unknown

### inference

- `aptatrans_pipeline.py`
  - 能力：inference_pipeline
  - 用途：推理/预测管线；按文件名推断负责端到端打分流程
  - 复用状态：blocked；类型：code_entry
- `run.py`
  - 能力：inference_pipeline
  - 用途：运行入口候选；可能封装训练或推理调用
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `config/default.yaml`
  - 能力：config
  - 用途：默认实验配置；按文件名推断包含超参数、路径与运行开关
  - 复用状态：blocked；类型：config
- `encoders.py`
  - 能力：model_architecture
  - 用途：编码器实现；按文件名推断负责 aptamer/protein 表示学习
  - 复用状态：blocked；类型：code_entry
- `utils.py`
  - 能力：helper_module
  - 用途：公共工具函数；可能承载数据处理、度量或训练辅助
  - 复用状态：blocked；类型：code_entry
- `mcts.py`
  - 能力：search_helper
  - 用途：搜索/优化辅助模块；是否进入主流程未核验
  - 复用状态：blocked；类型：code_entry

### training

- `training.py`
  - 能力：training_module
  - 用途：主训练模块；静态清单未识别为独立入口
  - 复用状态：blocked；类型：code_entry
- `pretraining.py`
  - 能力：training_module
  - 用途：预训练模块；用于预训练编码器或相关权重生成
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态清点，未执行代码、未跑测试、未验证模型文件可加载性。
- 依赖未安装，submodules 未初始化，large blobs 可能是 promisor-only。
- `training.py`、`run.py`、`mcts.py` 的实际调用关系未核验。
- checkpoint 与 pickle 文件的训练来源、拆分方式、作者许可均未确认。

## 仍未知

- `data/dataset_li.pickle` 是否为最终训练集、验证集还是索引文件无法确认。
- `data/protein_word_freq_3.pickle` 是否为项目生成缓存或外部语料统计无法确认。
- `models/default/*.pt` 是否对应论文报告的最终最佳权重无法仅凭路径确认。
- `example.ipynb` 仅能视为示例性材料，不能证明正式评测流程。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
