# bytedance/dplm

- **仓库：** [https://github.com/bytedance/dplm](https://github.com/bytedance/dplm)
- **固定 commit：** `8a2e15e53416b4536f03f79ad1f6f6a9cbd5e19d`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **资产记录数：** 18

## 仓库摘要

该仓库是 DPLM 论文对应的静态代码仓库：包含 DPLM/DPLM2/StructOK 三条方法线、训练与生成入口、数据下载与装载脚本、评测脚本，以及 vendored OpenFold；未见随仓库打包的真实数据集或可核验权重文件。

## 可复用模块与资源

### checkpoints

- `src/byprot/models/structok/modules/folding_utils/pretrained.py`
  - 能力：pretrained checkpoint wiring
  - 用途：预训练折叠/结构权重加载封装；未见实际权重文件
  - 复用状态：partial；类型：code_entry

### datasets

- `src/byprot/datamodules/dataset/uniref.py`
  - 能力：Uniref50 sequence corpus
  - 用途：LM 预训练/序列生成的数据加载与外部下载入口；仓库未打包原始数据
  - 复用状态：partial；类型：code_entry
- `src/byprot/datamodules/dataset/cath.py`
  - 能力：CATH 4.3 structure dataset
  - 用途：结构条件建模与折叠相关训练数据装载；仓库未包含数据本体
  - 复用状态：partial；类型：code_entry
- `src/byprot/datamodules/pdb_dataset/pdb_datamodule.py`
  - 能力：PDB / SwissProt structure-sequence dataset
  - 用途：PDB/SwissProt 下载、缓存与训练装载；实际样本不在仓库内
  - 复用状态：partial；类型：code_entry
- `src/byprot/datamodules/dataset/tokenized_protein.py`
  - 能力：tokenized protein corpus
  - 用途：离散 token 训练，支撑 StructOK / latent model 路线
  - 复用状态：partial；类型：code_entry

### evaluation

- `src/byprot/modules/metrics.py`
  - 能力：protein metrics
  - 用途：训练/验证/测试指标汇总
  - 复用状态：ready_for_review；类型：code_entry
- `analysis/cal_tmscore.py`
  - 能力：TMscore / pLDDT analysis helpers
  - 用途：结构结果后处理与评分
  - 复用状态：ready_for_review；类型：code_entry

### inference

- `generate_dplm.py`
  - 能力：sequence generation
  - 用途：DPLM 采样、生成与 scaffold 代码路径
  - 复用状态：ready_for_review；类型：code_entry
- `generate_dplm2.py`
  - 能力：DPLM2 generation
  - 用途：DPLM2 采样、生成与 scaffold 代码路径
  - 复用状态：ready_for_review；类型：code_entry
- `configs/experiment/structok/inference/unconditional.yaml`
  - 能力：structure-side inference recipes
  - 用途：StructOK 的 forward / inverse / reconstruction / unconditional / codesign 推理配置
  - 复用状态：ready_for_review；类型：config
- `vendor/openfold/scripts/generate_alphafold_feature_dict.py`
  - 能力：vendored OpenFold feature-generation utilities
  - 用途：AlphaFold/OpenFold 特征字典与缓存预处理
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `src/byprot/models/dplm/dplm.py`
  - 能力：DPLM / DPLM2 protein language-model core
  - 用途：序列级 diffusion language model 主体、inverse folding 变体与适配层
  - 复用状态：ready_for_review；类型：code_entry
- `src/byprot/models/structok/structok_lfq.py`
  - 能力：StructOK latent structure tokenizer and folding stack
  - 用途：结构 tokenization、LFQ/VQ-VAE 与 folding 生成路径
  - 复用状态：ready_for_review；类型：code_entry
- `vendor/openfold/openfold/model/model.py`
  - 能力：OpenFold vendored structural model/data utilities
  - 用途：第三方折叠模型、MSA/template/data pipeline 与测试辅助
  - 复用状态：ready_for_review；类型：code_entry
- `src/byprot/utils/protein/folding_model.py`
  - 能力：Protein utility and folding wrapper layer
  - 用途：折叠模型封装、残基/原子级工具与 PDB tokenization 辅助
  - 复用状态：ready_for_review；类型：code_entry

### training

- `train.py`
  - 能力：training entrypoint and pipeline
  - 用途：Hydra/Lightning 风格训练入口，连接各任务与 datamodule
  - 复用状态：ready_for_review；类型：code_entry
- `configs/experiment/dplm/dplm_650m.yaml`
  - 能力：training recipes
  - 用途：DPLM / DPLM2 / StructOK 的超参与 stage 配置集合
  - 复用状态：ready_for_review；类型：config
- `vendor/openfold/train_openfold.py`
  - 能力：vendored OpenFold training path
  - 用途：OpenFold 结构模型训练/微调入口
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态清单审查，未执行代码、未安装依赖、未运行测试。
- tracked 路径存在不代表训练/推理/评测可成功复现。
- 未见随仓库打包的数据集或二进制 checkpoint 权重。
- vendor/openfold 与项目自有代码、数据、模型许可需要分开核对。

## 仍未知

- 各下载脚本拉取到的外部数据集及其最终许可未核验。
- src/byprot/models/structok/modules/folding_utils/pretrained.py 对应的具体 checkpoint 来源与版本未知。
- 评测指标实现细节、实验协议和数值结果未通过执行确认。
- 仓库中 analysis 脚本是否为正式发表时使用的唯一评测流程无法仅凭静态路径确定。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
