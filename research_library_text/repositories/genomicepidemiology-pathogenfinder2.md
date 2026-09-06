# genomicepidemiology/pathogenfinder2

- **仓库：** [https://github.com/genomicepidemiology/pathogenfinder2](https://github.com/genomicepidemiology/pathogenfinder2)
- **固定 commit：** `3837caf6710da5da3038f5d1246dd82ab26e003a`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **资产记录数：** 34

## 仓库摘要

这是 PathogenFinder2 的静态仓库审查。仓库包含多种神经网络结构、预处理/后处理模块、CLI 推理入口、训练配置、测试夹具、2 个 TSV 元数据、1 个 embedding 缓存和 5 个 `.pt` 权重；代码许可可按 Apache-2.0 复用，但数据与模型资产的独立来源/许可未在冻结证据中完成边界证明。

## 可复用模块与资源

### checkpoints

- `src/pathogenfinder2/data/models_weights/model.pt`
  - 能力：model_weight
  - 用途：主模型权重
  - 复用状态：partial；类型：model_weight
- `src/pathogenfinder2/data/models_weights/weights_model1.pt`
  - 能力：model_weight
  - 用途：模型权重变体 1
  - 复用状态：partial；类型：model_weight
- `src/pathogenfinder2/data/models_weights/weights_model2.pt`
  - 能力：model_weight
  - 用途：模型权重变体 2
  - 复用状态：partial；类型：model_weight
- `src/pathogenfinder2/data/models_weights/weights_model3.pt`
  - 能力：model_weight
  - 用途：模型权重变体 3
  - 复用状态：partial；类型：model_weight
- `src/pathogenfinder2/data/models_weights/weights_model4.pt`
  - 能力：model_weight
  - 用途：模型权重变体 4
  - 复用状态：partial；类型：model_weight

### datasets

- `data/PathogenFinder2_dataset/METADATA_2024strain.tsv`
  - 能力：dataset_metadata
  - 用途：菌株元数据/训练或回归索引
  - 复用状态：partial；类型：unknown
- `data/PathogenFinder2_dataset/METADATA_PF2DB.tsv`
  - 能力：dataset_metadata
  - 用途：PF2DB 元数据/参考库索引
  - 复用状态：partial；类型：unknown
- `src/pathogenfinder2/data/bpl/embeddings.npz`
  - 能力：embedding_cache
  - 用途：预计算 protein embedding 缓存
  - 复用状态：partial；类型：unknown
- `test/data/GCF_000014385.1_ASM1438v1_genomic.fna`
  - 能力：test_fixture_sequence
  - 用途：回归/烟测输入基因组序列
  - 复用状态：partial；类型：unknown
- `test/data/GCF_006493955.1_ASM649395v1_genomic.fna`
  - 能力：test_fixture_sequence
  - 用途：回归/烟测输入基因组序列
  - 复用状态：partial；类型：unknown

### evaluation

- `test/test_network.py`
  - 能力：test_suite
  - 用途：网络结构与前向逻辑的静态测试
  - 复用状态：partial；类型：code_entry
- `test/test_gpu_inference.py`
  - 能力：test_suite
  - 用途：GPU 推理路径的回归测试
  - 复用状态：partial；类型：code_entry
- `test/test_smoke.py`
  - 能力：test_suite
  - 用途：烟测，检查最小可运行路径
  - 复用状态：partial；类型：code_entry
- `test/test_reporting.py`
  - 能力：test_suite
  - 用途：结果报告/导出逻辑测试
  - 复用状态：partial；类型：code_entry
- `test/configs/config_test.json`
  - 能力：config_recipe
  - 用途：测试与回归的配置样例
  - 复用状态：partial；类型：config

### inference

- `src/pathogenfinder2/__main__.py`
  - 能力：code_entry
  - 用途：package 级命令行入口
  - 复用状态：ready_for_review；类型：code_entry
- `src/pathogenfinder2/main.py`
  - 能力：code_entry
  - 用途：推理流程主入口与参数调度
  - 复用状态：ready_for_review；类型：code_entry
- `src/pathogenfinder2/cli.py`
  - 能力：code_entry
  - 用途：命令行参数解析与执行分发
  - 复用状态：ready_for_review；类型：code_entry
- `test/configs/config_inference.json`
  - 能力：config_recipe
  - 用途：推理流程的配置样例
  - 复用状态：ready_for_review；类型：config

### reusable_assets

- `src/pathogenfinder2/dl/model.py`
  - 能力：model_architecture
  - 用途：统一组装并切换不同神经网络骨架与分类头
  - 复用状态：ready_for_review；类型：code_entry
- `src/pathogenfinder2/dl/models/convnext.py`
  - 能力：model_architecture
  - 用途：提供 ConvNeXt backbone
  - 复用状态：ready_for_review；类型：code_entry
- `src/pathogenfinder2/dl/models/densenet.py`
  - 能力：model_architecture
  - 用途：提供 DenseNet backbone
  - 复用状态：ready_for_review；类型：code_entry
- `src/pathogenfinder2/dl/models/fnn.py`
  - 能力：model_architecture
  - 用途：提供 FNN baseline 架构
  - 复用状态：ready_for_review；类型：code_entry
- `src/pathogenfinder2/preprocessing/embedder.py`
  - 能力：preprocessing
  - 用途：把序列转换为 protein language model embedding
  - 复用状态：ready_for_review；类型：code_entry
- `src/pathogenfinder2/preprocessing/prodigal.py`
  - 能力：preprocessing
  - 用途：进行 gene calling / ORF 提取相关预处理
  - 复用状态：ready_for_review；类型：code_entry
- `src/pathogenfinder2/postprocessing/alignment.py`
  - 能力：postprocessing
  - 用途：执行 alignment 或结果映射类后处理
  - 复用状态：ready_for_review；类型：code_entry
- `src/pathogenfinder2/postprocessing/landscape.py`
  - 能力：postprocessing
  - 用途：生成 landscape / 可视化输出
  - 复用状态：ready_for_review；类型：code_entry
- `src/pathogenfinder2/dl/utils/data.py`
  - 能力：data_loading
  - 用途：加载数据集并组织批处理
  - 复用状态：ready_for_review；类型：code_entry
- `src/pathogenfinder2/setup_prot_db.py`
  - 能力：data_setup
  - 用途：准备或构建 protein database 的辅助流程
  - 复用状态：ready_for_review；类型：code_entry

### training

- `src/pathogenfinder2/dl/engine.py`
  - 能力：training_loop
  - 用途：训练循环、epoch 管理与模型拟合编排
  - 复用状态：ready_for_review；类型：code_entry
- `src/pathogenfinder2/dl/utils/optimizer.py`
  - 能力：optimizer
  - 用途：优化器与参数更新策略
  - 复用状态：ready_for_review；类型：code_entry
- `data/configs/config_train.json`
  - 能力：config_recipe
  - 用途：训练超参与路径配置
  - 复用状态：ready_for_review；类型：config
- `src/pathogenfinder2/data/configs/config_base.json`
  - 能力：config_recipe
  - 用途：基础配置模板，可供训练与推理复用
  - 复用状态：ready_for_review；类型：config
- `test/configs/config_trainfinal3_v4.json`
  - 能力：config_recipe
  - 用途：训练/回归用的配置样例
  - 复用状态：ready_for_review；类型：config

## 使用限制

- 仅做静态审查，仓库代码未执行。
- 依赖未安装，测试未运行。
- 子模块未初始化，且部分大文件可能只是 promisor blob。
- 路径存在不等于可复现、可训练或可推理。

## 仍未知

- 未见可验证的训练入口、训练日志或已完成的实验结果。
- 数据集、embedding 与 checkpoint 的来源及独立许可未在冻结证据中确认。
- 外部下载、数据库构建或权重生成流程是否完整可用，静态证据不足。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
