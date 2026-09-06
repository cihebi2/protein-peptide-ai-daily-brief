# gzBiomedical/EpiScan

- **仓库：** [https://github.com/gzBiomedical/EpiScan](https://github.com/gzBiomedical/EpiScan)
- **固定 commit：** `62661a82fbd5b52e8b94fb120c30cdeef4500247`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 18

## 仓库摘要

仓库主要是 EpiScan 的序列表位映射代码包，含模型结构、训练/推理脚本、公开数据切分、结果表和一个最终权重；仅做静态清点，MIT 仅覆盖代码，数据与模型许可边界仍需单独核验。

## 可复用模块与资源

### checkpoints

- `EpiScan/EpiScan/embLLM/pretrained.py`
  - 能力：pretrained_model_reference
  - 用途：预训练模型引用/加载逻辑；不是序列化权重文件本体
  - 复用状态：unknown；类型：code_entry
- `trained_model/Seq_final.pth`
  - 能力：trained_weights
  - 用途：最终训练权重文件
  - 复用状态：partial；类型：model_weight

### datasets

- `dataProcess/public/DB1.fasta`
  - 能力：sequence_dataset
  - 用途：FASTA 序列数据/输入样本
  - 复用状态：unknown；类型：unknown
- `dataProcess/public/public_sep_trainAg.tsv`
  - 能力：train_split_table
  - 用途：训练集拆分表
  - 复用状态：unknown；类型：unknown
- `dataProcess/public/public_sep_valAg.tsv`
  - 能力：validation_split_table
  - 用途：验证集拆分表
  - 复用状态：unknown；类型：unknown
- `dataProcess/public/public_sep_testAg.tsv`
  - 能力：test_split_table
  - 用途：测试集拆分表
  - 复用状态：unknown；类型：unknown
- `dataProcess/publicPairs/con_cdr_dict.pickle`
  - 能力：preprocessed_dict_cache
  - 用途：配对/预处理字典缓存
  - 复用状态：unknown；类型：unknown
- `dataProcess/publicPairs/con_pdb_dict_AgAb.pickle`
  - 能力：preprocessed_dict_cache
  - 用途：PDB/Ag-Ab 配对字典缓存
  - 复用状态：unknown；类型：unknown

### evaluation

- `EpiScan/EpiScan/commands/demo_test.py`
  - 能力：demo_test
  - 用途：demo/test 入口，可作为静态评估脚本候选
  - 复用状态：partial；类型：code_entry
- `EpiScan/EpiScan/experimental results/DB1-test.csv`
  - 能力：result_table
  - 用途：DB1 测试结果/基准输出表
  - 复用状态：unknown；类型：unknown
- `EpiScan/EpiScan/experimental results/DB2-test.csv`
  - 能力：result_table
  - 用途：DB2 测试结果/基准输出表
  - 复用状态：unknown；类型：unknown

### inference

- `EpiScan/EpiScan/commands/epimapping.py`
  - 能力：inference_entrypoint
  - 用途：表位映射/预测入口候选；仅凭路径名判断，未验证调用链
  - 复用状态：partial；类型：code_entry
- `EpiScan/EpiScan/commands/embed.py`
  - 能力：feature_export_or_embedding
  - 用途：embedding 导出/前处理入口候选；静态未验证其是否为正式推理链路
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `EpiScan/EpiScan/models/deep_ppi.py`
  - 能力：model_architecture
  - 用途：核心模型结构/交互建模；同目录 `contact_sep.py`, `interaction_sep.py`, `embedding.py`, `BasicModule.py` 为同一模型栈
  - 复用状态：ready_for_review；类型：code_entry
- `EpiScan/EpiScan/embLLM/language_model.py`
  - 能力：sequence_embedding_model
  - 用途：序列 embedding / language model 实现；配合 `alphabets.py`, `fasta.py`, `utils.py` 使用
  - 复用状态：ready_for_review；类型：code_entry
- `EpiScan/EpiScan/selfLoss/BdiceLoss.py`
  - 能力：loss_and_attention_blocks
  - 用途：训练期 loss 与 attention 组件；`Bfocalloss.py`, `attBlock.py`, `crossAtt.py` 为配套模块
  - 复用状态：ready_for_review；类型：code_entry
- `EpiScan/EpiScan/embLLM/pretrained.py`
  - 能力：pretrained_model_reference
  - 用途：预训练模型引用/加载逻辑；静态看更像引用器而非权重本体
  - 复用状态：unknown；类型：code_entry

### training

- `EpiScan/EpiScan/commands/train_sep-auc.py`
  - 能力：training_entrypoint
  - 用途：训练入口；从命名看用于以 AUC 为目标的训练
  - 复用状态：partial；类型：code_entry

## 使用限制

- 仅做静态清点，未执行任何脚本或测试。
- 未安装依赖，无法验证训练/推理/评估链路。
- `EpiScan/EpiScan/embLLM/pretrained.py` 是 Python 脚本，不应直接当作二进制 checkpoint。
- `trained_model/Seq_final.pth` 仅证明文件存在，不证明可加载或来源可追溯。
- 数据文件与结果 CSV 的来源、再分发许可和生成方式都未被验证。

## 仍未知

- `dataProcess/public/*` 是否为作者自建数据还是外部公开数据，静态清单无法确认。
- `commands/epimapping.py`、`commands/embed.py` 是否为正式推理入口，仍需阅读内容或运行验证。
- `DB1-test.csv` 和 `DB2-test.csv` 更像结果表而非原始数据，具体生成过程未知。
- `Seq_final.pth` 对应的训练配置、指标和最佳验证标准未在冻结清单中给出。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
