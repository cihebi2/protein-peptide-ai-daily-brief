# bowenwang77/OmniMol

- **仓库：** [https://github.com/bowenwang77/OmniMol](https://github.com/bowenwang77/OmniMol)
- **固定 commit：** `342506a224fb29e26e956f24d227178fdc92a987`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **资产记录数：** 23

## 仓库摘要

该仓库是一个基于 fairseq/Graphormer 的分子表示学习与 ADMET 微调代码库；静态清单可见训练、推理、验证、数据预处理、示例数据与模型归档，但未能证明实际运行或权重内容。

## 可复用模块与资源

### checkpoints

- `fairseq_mods/fairseq/checkpoint_utils.py`
  - 能力：checkpoint 读写工具
  - 用途：模型 checkpoint 加载/保存辅助
  - 复用状态：partial；类型：code_entry
- `fairseq_mods/fairseq/modules/checkpoint_activations.py`
  - 能力：activation checkpoint
  - 用途：激活检查点以降低显存占用
  - 复用状态：partial；类型：code_entry
- `applicability_domain_models.zip`
  - 能力：候选模型归档
  - 用途：可能包含模型权重或模型集合；静态清单未解包确认
  - 复用状态：unknown；类型：unknown

### datasets

- `example/CYP2C19-inh.csv`
  - 能力：CYP2C19 抑制示例数据
  - 用途：示例分类/抑制活性数据
  - 复用状态：ready_for_review；类型：unknown
- `example/prop1.csv`
  - 能力：性质回归示例数据 1
  - 用途：示例回归任务数据
  - 复用状态：ready_for_review；类型：unknown
- `example/prop2.csv`
  - 能力：性质回归示例数据 2
  - 用途：示例回归任务数据
  - 复用状态：ready_for_review；类型：unknown
- `Applicability_Domain.csv`
  - 能力：应用域表
  - 用途：应用域筛查所需的表格数据
  - 复用状态：ready_for_review；类型：unknown
- `application_domains.csv`
  - 能力：应用域映射表
  - 用途：应用域类别/映射参考
  - 复用状态：ready_for_review；类型：unknown

### evaluation

- `fairseq_mods/fairseq_cli/validate.py`
  - 能力：验证集评估
  - 用途：模型验证与评估入口
  - 复用状态：partial；类型：code_entry
- `fairseq_mods/fairseq_cli/eval_lm.py`
  - 能力：LM 评估
  - 用途：语言模型/序列模型评估
  - 复用状态：partial；类型：code_entry
- `fairseq_mods/fairseq/logging/metrics.py`
  - 能力：指标汇总
  - 用途：训练/验证指标记录与聚合
  - 复用状态：partial；类型：code_entry
- `check_applicability_domain.py`
  - 能力：应用域评估
  - 用途：对候选样本做 applicability domain 检查
  - 复用状态：ready_for_review；类型：code_entry

### inference

- `fairseq_mods/fairseq_cli/generate.py`
  - 能力：生成式推理
  - 用途：候选输出生成与推理
  - 复用状态：partial；类型：code_entry
- `fairseq_mods/fairseq_cli/interactive.py`
  - 能力：交互式推理
  - 用途：交互式输入输出推理
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `graphormer/models/graphormer.py`
  - 能力：分子图模型核心实现
  - 用途：Graphormer 分子表示学习主模型代码
  - 复用状态：partial；类型：code_entry
- `graphormer/modules/graphormer_graph_encoder.py`
  - 能力：图编码器层
  - 用途：Graphormer 图编码器堆叠与消息传递实现
  - 复用状态：partial；类型：code_entry
- `scripts/data_proc_SMILES2lmdb.py`
  - 能力：SMILES→LMDB 预处理
  - 用途：把 SMILES 转成训练/索引所需的 LMDB 结构
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/umap_vis.py`
  - 能力：结果可视化
  - 用途：对嵌入或实验结果做 UMAP 降维展示
  - 复用状态：ready_for_review；类型：code_entry

### training

- `ADMET_FT_cls.sh`
  - 能力：分类微调入口
  - 用途：启动 ADMET 分类微调流程
  - 复用状态：ready_for_review；类型：code_entry
- `ADMET_FT_reg.sh`
  - 能力：回归微调入口
  - 用途：启动 ADMET 回归微调流程
  - 复用状态：ready_for_review；类型：code_entry
- `fairseq_mods/fairseq_cli/train.py`
  - 能力：通用训练入口
  - 用途：fairseq 风格的通用训练主入口
  - 复用状态：partial；类型：code_entry
- `fairseq_mods/fairseq/trainer.py`
  - 能力：训练循环
  - 用途：训练循环、优化与日志聚合
  - 复用状态：partial；类型：code_entry
- `graphormer/criterions/mae_dft_md.py`
  - 能力：图任务与损失
  - 用途：图预训练/微调相关损失定义
  - 复用状态：partial；类型：code_entry

## 使用限制

- 仅做静态清单审查，未执行代码、未运行测试、未安装依赖。
- `applicability_domain_models.zip` 未解包，无法确认内部是否为权重、脚本或数据，也无法确认许可。
- `fairseq_mods/` 与 `graphormer/` 大量文件更像 vendored/衍生第三方代码，路径存在不等于原创贡献。
- 示例 CSV、应用域表与模型归档未见单独数据/模型许可边界，外部复用需额外核对。

## 仍未知

- 冻结清单里是否存在可直接复用的真实 checkpoint 文件（如 .pt/.pth/.ckpt）未被显式列出。
- `applicability_domain_models.zip` 的内容是否真为模型权重、以及其来源是否与仓库代码一致。
- `ADMET_FT_cls.sh` 与 `ADMET_FT_reg.sh` 的真实输入数据、超参和调用链未从静态路径中确认。
- `graphormer/` 目录是否相对上游 Graphormer 有项目级修改，静态路径不足以判断。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
