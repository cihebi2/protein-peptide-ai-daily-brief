# yatoka233/lncpndeep

- **仓库：** [https://github.com/yatoka233/lncpndeep](https://github.com/yatoka233/lncpndeep)
- **固定 commit：** `0e20ea30f6f5d5e97f73823d8abbd5c056d8e574`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 14

## 仓库摘要

该仓库主要包含 lncRNA 分类/预训练/推理代码：有模型结构、数据加载与预训练入口，但未见仓库内数据集、checkpoint 或 LICENSE；因此只能做静态、受限的复用判断，不能证明可复现执行。

## 可复用模块与资源

### inference

- `predict_lncrna.py`
  - 能力：推理脚本
  - 用途：对输入序列执行 lncRNA 分类/预测
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `simulation_and_pretrain_code/model/attention.py`
  - 能力：注意力模块
  - 用途：实现序列注意力层
  - 复用状态：blocked；类型：code_entry
- `simulation_and_pretrain_code/model/bert.py`
  - 能力：Transformer/BERT 编码器
  - 用途：实现序列编码主干
  - 复用状态：blocked；类型：code_entry
- `simulation_and_pretrain_code/model/mybigbird.py`
  - 能力：BigBird 风格长序列主干
  - 用途：处理长序列建模
  - 复用状态：blocked；类型：code_entry
- `simulation_and_pretrain_code/feature.py`
  - 能力：特征工程
  - 用途：构造输入特征
  - 复用状态：blocked；类型：code_entry
- `simulation_and_pretrain_code/multi_feature.py`
  - 能力：多特征融合
  - 用途：融合多路 embedding / 特征
  - 复用状态：blocked；类型：code_entry
- `simulation_and_pretrain_code/dataset.py`
  - 能力：数据集加载器
  - 用途：构造训练/推理数据读取
  - 复用状态：blocked；类型：code_entry
- `simulation_and_pretrain_code/pre_dataset.py`
  - 能力：预训练数据构建
  - 用途：生成预训练样本
  - 复用状态：blocked；类型：code_entry
- `simulation_and_pretrain_code/split_sequence.py`
  - 能力：序列切分/预处理
  - 用途：切分输入序列并准备特征
  - 复用状态：blocked；类型：code_entry
- `extract_nucleotide_embeddings.py`
  - 能力：nucleotide embedding 提取
  - 用途：生成 nucleotide embedding 特征
  - 复用状态：blocked；类型：code_entry
- `download_weights.py`
  - 能力：checkpoint 下载辅助
  - 用途：获取外部预训练权重（未见仓库内 checkpoint）
  - 复用状态：blocked；类型：code_entry

### training

- `simulation_and_pretrain_code/pretrain.py`
  - 能力：预训练入口
  - 用途：组织预训练流程
  - 复用状态：blocked；类型：code_entry
- `simulation_and_pretrain_code/scripts/pretrain.py`
  - 能力：脚本化预训练入口
  - 用途：以脚本方式启动预训练
  - 复用状态：blocked；类型：code_entry
- `simulation_and_pretrain_code/trainer.py`
  - 能力：训练循环/优化模块
  - 用途：封装训练、优化与日志流程
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态清点，未执行代码、未安装依赖、未运行测试。
- 未发现仓库内 bundled 数据集或 checkpoint，无法核实训练/推理复现性。
- 未发现 LICENSE 文件，代码复用边界不明确。
- `simulation_and_pretrain_code/test.py` 仅凭路径名不能确认其是否为正式评估脚本。

## 仍未知

- 外部数据来源、下载地址及许可是否在 README 或脚本中声明，当前无法确认。
- `download_weights.py` 实际下载的权重来源与授权状态未知。
- 是否存在未跟踪的大文件权重或数据，静态快照无法排除。
- 独立 evaluation 指标与划分方案未从冻结清单中识别出来。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
