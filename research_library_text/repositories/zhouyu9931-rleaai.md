# zhouyu9931/rleaai

- **仓库：** [https://github.com/zhouyu9931/rleaai](https://github.com/zhouyu9931/rleaai)
- **固定 commit：** `8f59bd111347d38eb22cbb49543731e57a1a6aee`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 15

## 仓库摘要

该仓库冻结了RLEAAI的模型实现、数据加载、推理/评估脚本、HIV与SARS-CoV-2权重及示例数据；未发现许可证文件，代码直接复用受限。

## 可复用模块与资源

### checkpoints

- `ckp/HIV.pth`
  - 能力：HIV 模型权重
  - 用途：HIV 任务的已保存模型参数
  - 复用状态：unknown；类型：model_weight
- `ckp/SARS-CoV-2.pth`
  - 能力：SARS-CoV-2 模型权重
  - 用途：SARS-CoV-2 任务的已保存模型参数
  - 复用状态：unknown；类型：model_weight

### datasets

- `data/dataset_hiv.xlsx`
  - 能力：HIV 数据表
  - 用途：HIV 抗体-抗原交互数据
  - 复用状态：unknown；类型：unknown
- `data/dataset_SARS-CoV-2.xlsx`
  - 能力：SARS-CoV-2 数据表
  - 用途：SARS-CoV-2 抗体-抗原交互数据
  - 复用状态：unknown；类型：unknown
- `data/example/ab.fasta`
  - 能力：示例抗体 FASTA
  - 用途：示例抗体序列输入
  - 复用状态：unknown；类型：unknown
- `data/example/ag.fasta`
  - 能力：示例抗原 FASTA
  - 用途：示例抗原序列输入
  - 复用状态：unknown；类型：unknown

### evaluation

- `utils/evaluate.py`
  - 能力：评估脚本
  - 用途：汇总或计算评估指标
  - 复用状态：blocked；类型：code_entry

### inference

- `predict.py`
  - 能力：推理入口
  - 用途：加载权重并对输入序列进行预测
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `model/RLEAAI.py`
  - 能力：RLEAAI 主模型定义
  - 用途：组合主网络结构并调度子模块
  - 复用状态：blocked；类型：code_entry
- `model/lcnn.py`
  - 能力：LCNN 子模块
  - 用途：提供局部卷积特征提取组件
  - 复用状态：blocked；类型：code_entry
- `model/rcca.py`
  - 能力：RCCA 子模块
  - 用途：提供上下文/注意力类子模块
  - 复用状态：blocked；类型：code_entry
- `dataset/rle_dataset.py`
  - 能力：数据集读取与样本构造
  - 用途：加载并组织交互数据样本
  - 复用状态：blocked；类型：code_entry
- `dataset/tensor.py`
  - 能力：张量/特征转换辅助
  - 用途：辅助数据到张量的转换
  - 复用状态：blocked；类型：code_entry
- `utils/cksaap.py`
  - 能力：CKSAAP 序列特征提取
  - 用途：生成序列顺序特征
  - 复用状态：blocked；类型：code_entry
- `utils/embedding.py`
  - 能力：embedding 辅助工具
  - 用途：处理或生成序列嵌入相关特征
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态清点，未运行任何脚本、测试或训练。
- 未发现 training_entrypoint 或 training_module，训练流程无法从冻结清单确认。
- 仅见 requirements.txt，未安装依赖，环境兼容性与版本锁定未知。
- `.pth` 权重与 `data/*.xlsx` 的来源、切分和许可未能从清单中确认。

## 仍未知

- README.md 内容未读取，无法确认作者自述的数据来源、实验协议和许可声明。
- ckp/HIV.pth 与 ckp/SARS-CoV-2.pth 是否为论文最终可复用权重、是否带优化器状态未知。
- data/dataset_hiv.xlsx 与 data/dataset_SARS-CoV-2.xlsx 的标注、切分与采样策略未知。
- results/HIV、results/SARS-CoV-2、results/SAbDab 下的文本结果未解析，无法验证具体指标。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
