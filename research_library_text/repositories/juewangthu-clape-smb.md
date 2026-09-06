# juewangthu/clape-smb

- **仓库：** [https://github.com/juewangthu/clape-smb](https://github.com/juewangthu/clape-smb)
- **固定 commit：** `998b378a7d30515d325ae66277e8ffbfd2733d6f`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 36

## 仓库摘要

静态清单显示该仓库包含核心模型实现、数据读取/预处理、损失与 triplet 逻辑、推理入口，以及 17 个 checkpoint；Raw_data 下还有 SJC、UniProtSMB、Standard datasets 和 IDP/IDP_IDR 文本。未见 LICENSE、独立训练入口或独立评测流水线，因此只能按静态可复用性分层。

## 可复用模块与资源

### checkpoints

- `Models/SJC/random_seed/17.ckpt`
  - 能力：SJC checkpoint
  - 用途：SJC 随机种子训练权重，可用于复现实验或加载推理。
  - 复用状态：blocked；类型：model_weight
- `Models/SJC/random_seed/35.ckpt`
  - 能力：SJC checkpoint
  - 用途：SJC 随机种子训练权重，可用于复现实验或加载推理。
  - 复用状态：blocked；类型：model_weight
- `Models/SJC/random_seed/42.ckpt`
  - 能力：SJC checkpoint
  - 用途：SJC 随机种子训练权重，可用于复现实验或加载推理。
  - 复用状态：blocked；类型：model_weight
- `Models/SJC/random_seed/6.ckpt`
  - 能力：SJC checkpoint
  - 用途：SJC 随机种子训练权重，可用于复现实验或加载推理。
  - 复用状态：blocked；类型：model_weight
- `Models/UniProtSMB/k_folds/fold1.ckpt`
  - 能力：UniProtSMB k-fold checkpoint
  - 用途：UniProtSMB 交叉验证权重，fold1。
  - 复用状态：blocked；类型：model_weight
- `Models/UniProtSMB/k_folds/fold2.ckpt`
  - 能力：UniProtSMB k-fold checkpoint
  - 用途：UniProtSMB 交叉验证权重，fold2。
  - 复用状态：blocked；类型：model_weight
- `Models/UniProtSMB/k_folds/fold3.ckpt`
  - 能力：UniProtSMB k-fold checkpoint
  - 用途：UniProtSMB 交叉验证权重，fold3。
  - 复用状态：blocked；类型：model_weight
- `Models/UniProtSMB/k_folds/fold4.ckpt`
  - 能力：UniProtSMB k-fold checkpoint
  - 用途：UniProtSMB 交叉验证权重，fold4。
  - 复用状态：blocked；类型：model_weight
- `Models/UniProtSMB/k_folds/fold5.ckpt`
  - 能力：UniProtSMB k-fold checkpoint
  - 用途：UniProtSMB 交叉验证权重，fold5。
  - 复用状态：blocked；类型：model_weight
- `Models/UniProtSMB/k_folds/fold6.ckpt`
  - 能力：UniProtSMB k-fold checkpoint
  - 用途：UniProtSMB 交叉验证权重，fold6。
  - 复用状态：blocked；类型：model_weight
- `Models/UniProtSMB/k_folds/fold7.ckpt`
  - 能力：UniProtSMB k-fold checkpoint
  - 用途：UniProtSMB 交叉验证权重，fold7。
  - 复用状态：blocked；类型：model_weight
- `Models/UniProtSMB/k_folds/fold8.ckpt`
  - 能力：UniProtSMB k-fold checkpoint
  - 用途：UniProtSMB 交叉验证权重，fold8。
  - 复用状态：blocked；类型：model_weight
- `Models/UniProtSMB/k_folds/fold9.ckpt`
  - 能力：UniProtSMB k-fold checkpoint
  - 用途：UniProtSMB 交叉验证权重，fold9。
  - 复用状态：blocked；类型：model_weight
- `Models/UniProtSMB/random_seed/17.ckpt`
  - 能力：UniProtSMB checkpoint
  - 用途：UniProtSMB 随机种子训练权重，可用于复现实验或加载推理。
  - 复用状态：blocked；类型：model_weight
- `Models/UniProtSMB/random_seed/35.ckpt`
  - 能力：UniProtSMB checkpoint
  - 用途：UniProtSMB 随机种子训练权重，可用于复现实验或加载推理。
  - 复用状态：blocked；类型：model_weight
- `Models/UniProtSMB/random_seed/42.ckpt`
  - 能力：UniProtSMB checkpoint
  - 用途：UniProtSMB 随机种子训练权重，可用于复现实验或加载推理。
  - 复用状态：blocked；类型：model_weight
- `Models/UniProtSMB/random_seed/6.ckpt`
  - 能力：UniProtSMB checkpoint
  - 用途：UniProtSMB 随机种子训练权重，可用于复现实验或加载推理。
  - 复用状态：blocked；类型：model_weight

### datasets

- `Raw_data/IDP.txt`
  - 能力：auxiliary dataset
  - 用途：IDP 相关原始数据，仓库内未见更细说明。
  - 复用状态：blocked；类型：unknown
- `Raw_data/IDP_IDR.txt`
  - 能力：auxiliary dataset
  - 用途：IDP/IDR 相关原始数据，仓库内未见更细说明。
  - 复用状态：blocked；类型：unknown
- `Raw_data/SJC/train_SJC.txt`
  - 能力：training split
  - 用途：SJC 任务训练集划分。
  - 复用状态：blocked；类型：unknown
- `Raw_data/SJC/valid_SJC.txt`
  - 能力：validation split
  - 用途：SJC 任务验证集划分。
  - 复用状态：blocked；类型：unknown
- `Raw_data/SJC/test_SJC.txt`
  - 能力：test split
  - 用途：SJC 任务测试集划分。
  - 复用状态：blocked；类型：unknown
- `Raw_data/Standard datasets/chen11.txt`
  - 能力：standard benchmark dataset
  - 用途：标准 benchmark 数据文件，可能用于外部评测或复现。
  - 复用状态：blocked；类型：unknown
- `Raw_data/Standard datasets/coach420.txt`
  - 能力：standard benchmark dataset
  - 用途：标准 benchmark 数据文件，可能用于外部评测或复现。
  - 复用状态：blocked；类型：unknown
- `Raw_data/Standard datasets/joined.txt`
  - 能力：standard benchmark dataset
  - 用途：标准 benchmark 的合并数据文件，具体协议未能从静态清单确认。
  - 复用状态：blocked；类型：unknown
- `Raw_data/Standard datasets/scpdb.txt`
  - 能力：standard benchmark dataset
  - 用途：标准 benchmark 数据文件，可能用于外部评测或复现。
  - 复用状态：blocked；类型：unknown
- `Raw_data/UniProtSMB/train_UniProtSMB.txt`
  - 能力：training split
  - 用途：UniProtSMB 任务训练集划分。
  - 复用状态：blocked；类型：unknown
- `Raw_data/UniProtSMB/valid_UniProtSMB.txt`
  - 能力：validation split
  - 用途：UniProtSMB 任务验证集划分。
  - 复用状态：blocked；类型：unknown
- `Raw_data/UniProtSMB/test_UniProtSMB.txt`
  - 能力：test split
  - 用途：UniProtSMB 任务测试集划分。
  - 复用状态：blocked；类型：unknown

### evaluation

- `count.py`
  - 能力：evaluation / statistics helper
  - 用途：统计或检查辅助脚本；静态清单未见完整 metrics pipeline。
  - 复用状态：blocked；类型：code_entry

### inference

- `inference.py`
  - 能力：inference entrypoint
  - 用途：推理入口，加载权重并输出 binding site 预测。
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `model.py`
  - 能力：model architecture
  - 用途：核心模型结构与前向计算实现，支撑训练和推理。
  - 复用状态：blocked；类型：code_entry

### training

- `data.py`
  - 能力：data loading
  - 用途：训练/验证/测试样本读取与批次构造。
  - 复用状态：blocked；类型：code_entry
- `losses.py`
  - 能力：loss function
  - 用途：训练损失函数实现。
  - 复用状态：blocked；类型：code_entry
- `triplet.py`
  - 能力：contrastive / triplet logic
  - 用途：triplet 或对比学习相关样本组织与约束逻辑。
  - 复用状态：blocked；类型：code_entry
- `pre.py`
  - 能力：preprocessing
  - 用途：预处理与训练前特征准备。
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅能做静态清单审查，未执行代码、未安装依赖、未跑测试。
- submodules 未初始化，且存在 large blobs/ promisor 文件的不确定性。
- 路径存在不等于可复现；checkpoint 的训练配置、超参数与指标不可由静态清单验证。
- 仓库未见独立 training entrypoint，因此训练流程只能从 data.py、losses.py、triplet.py、pre.py 等模块侧面推断。
- 仓库未见明确独立 evaluation 流水线，count.py 仅可视为辅助统计脚本。

## 仍未知

- Raw_data/Standard datasets/*.txt 与 IDP*.txt 的外部来源、授权范围和是否为 vendored_third_party 未明。
- count.py 的实际职责只能由文件名推断，是否承担正式评测未知。
- 是否存在外部 pretrained protein language model 依赖、下载脚本或隐藏权重未能从冻结清单确认。
- 17 个 checkpoint 分别对应的划分协议、最佳轮次和性能结果未在静态清单中体现。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
