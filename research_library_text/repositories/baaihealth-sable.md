# baaihealth/Sable

- **仓库：** [https://github.com/baaihealth/Sable](https://github.com/baaihealth/Sable)
- **固定 commit：** `7b2e46be059dbec0f1eca2fd3c378c70b3a1305d`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **资产记录数：** 10

## 仓库摘要

这是一个与论文直接关联的代码仓库，主体由蛋白结构/表示模型、任务头、数据流水线、配置配方以及多任务模块组成；冻结清单中未见可确认 checkpoint 或独立推理入口，示例数据与 TSV 资产的许可与来源也未被静态证实。

## 可复用模块与资源

### datasets

- `example_data.tar.gz`
  - 能力：示例数据包
  - 用途：快速上手/示例输入包，非已验证训练集
  - 复用状态：unknown；类型：unknown
- `script/model_quality_assessment.tsv`
  - 能力：模型质量评估表
  - 用途：任务准备与评估输入表
  - 复用状态：partial；类型：unknown

### evaluation

- `sable/module/binding_affinity_module.py`
  - 能力：下游任务验证与指标计算
  - 用途：下游任务的验证集/测试集评测与指标记录
  - 复用状态：ready_for_review；类型：code_entry

### inference

- `sable/model/model.py`
  - 能力：前向推理与任务打分
  - 用途：生成表示并输出任务分数/预测
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `opencomplex/model/embedders.py`
  - 能力：模型结构与任务头
  - 用途：蛋白表示、结构模块与下游任务输出
  - 复用状态：ready_for_review；类型：code_entry
- `opencomplex/data/data_pipeline.py`
  - 能力：数据流水线与预处理
  - 用途：样本构建、特征提取与任务数据准备
  - 复用状态：ready_for_review；类型：code_entry
- `sable/config/data/protein_design.yaml`
  - 能力：配置与运行配方
  - 用途：多任务训练、验证、日志与路径配置
  - 复用状态：ready_for_review；类型：config
- `opencomplex/loss/loss.py`
  - 能力：损失函数与训练辅助
  - 用途：训练目标、损失聚合与梯度辅助
  - 复用状态：partial；类型：code_entry

### training

- `go_sable.py`
  - 能力：训练/实验入口
  - 用途：疑似启动训练或实验流程
  - 复用状态：partial；类型：code_entry
- `sable/module/protein_design_module.py`
  - 能力：多任务训练模块
  - 用途：蛋白设计、抗体设计、结合亲和力、fold 分类、酶反应分类与模型质量评估的训练配方
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态清单审查，未执行代码、未安装依赖、未运行测试。
- tracked_paths 不等于实际可复现结果；文件存在不能证明训练、推理或评测已成功完成。
- 冻结清单中未见可确认 checkpoint/weights，因此无法判断模型资产的再利用与发布边界。
- 未发现独立的 inference 或 evaluation CLI 入口；只能依据模块与配置文件推断用途。
- example_data.tar.gz 与 script/model_quality_assessment.tsv 的内容、来源与许可未被展开验证。

## 仍未知

- go_sable.py 是否为正式训练入口、还是仅为辅助启动脚本，静态清单不足以确认。
- opencomplex 子树是否为 vendored third-party 代码，还是仓库自有实现，未见足够元数据。
- example_data.tar.gz 内部具体包含哪些样本/标签、是否可直接复用，尚不明确。
- 是否存在外部下载的 checkpoint 或额外数据源，冻结清单无法证明。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
