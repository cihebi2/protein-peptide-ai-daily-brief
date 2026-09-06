# jiaoshihu/captp

- **仓库：** [https://github.com/jiaoshihu/captp](https://github.com/jiaoshihu/captp)
- **固定 commit：** `1de2e4e265f39c3c19408a16ad14080611403837`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 8

## 仓库摘要

该仓库是 CAPTP 的静态实现清单，明确包含模型结构与数据预处理代码，以及训练/测试文本、AAindex.pkl 和 model_saved.pkl，但未发现 LICENSE、训练入口、推理入口或评估脚本；仅能做静态盘点，不能证明可复现运行。

## 可复用模块与资源

### checkpoints

- `data/model_saved.pkl`
  - 能力：序列化模型产物
  - 用途：保存的模型对象/权重快照，疑似 checkpoint
  - 复用状态：blocked；类型：unknown

### datasets

- `data/train_data.txt`
  - 能力：训练集
  - 用途：peptide toxicity 训练样本
  - 复用状态：blocked；类型：unknown
- `data/test1.txt`
  - 能力：测试集分片
  - 用途：静态 test split，用于 toxicity 分类评估
  - 复用状态：blocked；类型：unknown
- `data/test2.txt`
  - 能力：测试集分片
  - 用途：静态 test split，用于 toxicity 分类评估
  - 复用状态：blocked；类型：unknown
- `test.fasta`
  - 能力：FASTA 形式输入/外部测试序列
  - 用途：序列级评估输入或外部测试序列
  - 复用状态：blocked；类型：unknown
- `data/AAindex.pkl`
  - 能力：AAindex 特征表
  - 用途：氨基酸性质查表资源，供预处理阶段生成特征
  - 复用状态：unknown；类型：unknown

### reusable_assets

- `model/CAPTP_model.py`
  - 能力：CAPTP 模型结构（卷积+自注意力）
  - 用途：定义 peptide toxicity prediction 的主模型结构，供后续训练/推理复用
  - 复用状态：blocked；类型：code_entry
- `preprocess/data_process.py`
  - 能力：数据预处理/特征构建
  - 用途：读取序列并组织 AAindex/编码特征，形成模型输入
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态盘点，未执行代码或测试。
- 未见 LICENSE，不能判定代码/数据/checkpoint 的许可边界。
- data/model_saved.pkl 与 data/AAindex.pkl 的真实内容和来源未验证。
- 未确认 main.py 是否承担训练、推理或评估入口职责。

## 仍未知

- main.py 的实际职责未从冻结清单确认。
- data/AAindex.pkl 是否为第三方 vendored 资源未确认。
- data/model_saved.pkl 的序列化格式及可加载性未确认。
- train_data.txt、test1.txt、test2.txt、test.fasta 的标注来源与划分策略未确认。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
