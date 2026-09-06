# jiaqingxie/DeepProtein

- **仓库：** [https://github.com/jiaqingxie/DeepProtein](https://github.com/jiaqingxie/DeepProtein)
- **固定 commit：** `6324783383cda5b46d635e3d9ac2dfdbf629ee0a`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 24

## 仓库摘要

该仓库是 DeepProtein 论文对应的主代码库，静态清单显示其包含蛋白序列学习的模型/编码器/Tokenizer/解码器、任务训练脚本、LMDB 与 pkl/tab 形式的基准数据，以及测试与结果产物；LICENSE 为 MIT，但数据与结果资产未见独立许可或来源证明，且未发现可识别的 checkpoint。

## 可复用模块与资源

### datasets

- `DeepProtein/data/beta_lactamase/beta_lactamase_train.lmdb/data.mdb`
  - 能力：LMDB benchmark bundle
  - 用途：代表 DeepProtein/data 下多组 LMDB 切分（beta_lactamase、fluorescence、human_ppi、ppi_affinity、solubility、stability、subcellular_localization、yeast_ppi、remote_homology、secondary_structure）。
  - 复用状态：blocked；类型：unknown
- `DeepProtein/data/remote_homology.zip`
  - 能力：远程同源性数据包
  - 用途：remote_homology 基准压缩包。
  - 复用状态：blocked；类型：unknown
- `data/iedb_jespersen.pkl`
  - 能力：IEDB 预处理数据
  - 用途：IEDB/epitope 任务的 pickle 数据。
  - 复用状态：blocked；类型：unknown
- `data/tap.tab`
  - 能力：TAP 表格数据
  - 用途：TAP 任务表格数据。
  - 复用状态：blocked；类型：unknown
- `data/sabdab_chen.tab`
  - 能力：SAbDab 数据
  - 用途：SAbDab_Chen 任务数据。
  - 复用状态：blocked；类型：unknown
- `train/data/sabdab_liberis.pkl`
  - 能力：SAbDab 数据
  - 用途：SAbDab_Liberis 任务数据。
  - 复用状态：blocked；类型：unknown
- `train/data/pdb_jespersen.pkl`
  - 能力：PDB 预处理数据
  - 用途：PDB/Jespersen 相关预处理数据。
  - 复用状态：blocked；类型：unknown

### evaluation

- `result/test_markdowntable.txt`
  - 能力：测试集结果表
  - 用途：记录测试集指标汇总。
  - 复用状态：partial；类型：unknown
- `result/valid_markdowntable.txt`
  - 能力：验证集结果表
  - 用途：记录验证集指标汇总。
  - 复用状态：partial；类型：unknown
- `result/roc-auc.jpg`
  - 能力：曲线与图表
  - 用途：ROC-AUC 图像；同目录还有 PR-AUC、confusion matrix、logits 等结果产物。
  - 复用状态：partial；类型：unknown
- `plot/result.ipynb`
  - 能力：结果分析 notebook
  - 用途：汇总绘图与实验分析。
  - 复用状态：partial；类型：unknown

### inference

- `DeepProtein/ProteinPred.py`
  - 能力：性质预测推理
  - 用途：提供 protein property prediction 的推理封装。
  - 复用状态：partial；类型：code_entry
- `DeepProtein/PPI.py`
  - 能力：PPI 推理
  - 用途：提供 protein-protein interaction 相关推理/预测封装。
  - 复用状态：partial；类型：code_entry
- `DeepProtein/TokenPred.py`
  - 能力：token-level 推理
  - 用途：提供 token-level prediction 推理封装。
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `DeepProtein/model_helper.py`
  - 能力：模型构建
  - 用途：定义任务模型的组装与工厂逻辑，支撑多任务蛋白表示学习。
  - 复用状态：ready_for_review；类型：code_entry
- `DeepProtein/encoders.py`
  - 能力：序列编码器
  - 用途：提供蛋白序列编码、特征抽取与 backbone 封装。
  - 复用状态：ready_for_review；类型：code_entry
- `DeepProtein/Tokenizer.py`
  - 能力：Tokenizer/词表
  - 用途：处理 ESPF/token 映射与序列分词。
  - 复用状态：ready_for_review；类型：tokenizer
- `DeepProtein/pybiomed_helper.py`
  - 能力：生物信息学辅助函数
  - 用途：提供特征计算与辅助生物信息学工具。
  - 复用状态：ready_for_review；类型：code_entry
- `DeepProtein/LLM_decoders.py`
  - 能力：LLM 解码
  - 用途：支持 LLM 相关输出解码与任务头。
  - 复用状态：ready_for_review；类型：code_entry

### training

- `DeepProtein/finetune.py`
  - 能力：统一微调入口
  - 用途：主训练入口，汇总不同任务的 fine-tune 流程。
  - 复用状态：ready_for_review；类型：code_entry
- `train/cli_common.py`
  - 能力：训练 CLI 辅助
  - 用途：共享参数解析、配置拼装和命令行公共逻辑。
  - 复用状态：ready_for_review；类型：code_entry
- `train/beta.py`
  - 能力：任务训练脚本
  - 用途：beta_lactamase 任务训练脚本，代表单任务训练模板。
  - 复用状态：ready_for_review；类型：code_entry
- `train/human_ppi.py`
  - 能力：任务训练脚本
  - 用途：human_ppi 任务训练脚本，代表 PPI 训练流程。
  - 复用状态：ready_for_review；类型：code_entry
- `train/llm/llm_beta.py`
  - 能力：LLM 训练脚本
  - 用途：beta 任务的 LLM 训练变体。
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态清单审查，未执行代码、未安装依赖、未运行测试。
- 未发现 tracked checkpoint 文件；result/ 与 train/result/ 下的 logits、曲线和表格不应误判为权重。
- 数据文件虽被仓库收录，但其来源与许可未在冻结证据中得到确认。
- clone_depth=1 且大文件可能为 promisor-only，个别数据 blob 的完整性与可用性无法从静态证据证明。

## 仍未知

- DeepProtein/data 与 data/、train/data/ 中的预处理数据究竟是项目自制、第三方打包副本还是下载缓存，无法仅凭路径确认。
- Readme.md 可能包含更多下载/许可说明，但未在当前冻结证据中展开审阅。
- 没有看到可独立复用的 checkpoint，因此无法评估预训练权重的可得性或模型初始化边界。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
