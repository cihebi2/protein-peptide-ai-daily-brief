# Dulab2020/NeoaPred

- **仓库：** [https://github.com/Dulab2020/NeoaPred](https://github.com/Dulab2020/NeoaPred)
- **固定 commit：** `af66a88c31f28648c3cc5df243ffa94358d153e5`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **资产记录数：** 21

## 仓库摘要

仓库以 PepConf、PepFore 和 Surface/masif_tools 组成的结构预测与属性评分流程为主，附带 HLA 模板、示例 PDB、测试 CSV 和 3 个 `.pth` 权重；主代码许可证为 Apache-2.0，但 APBS-3.0.0.Linux 是独立第三方边界，静态审查未验证可复现。

## 可复用模块与资源

### checkpoints

- `NeoaPred/PepConf/trained_model/model_1.pth`
  - 能力：PepConf 训练权重
  - 用途：PepConf 推理时的预训练/已训练参数
  - 复用状态：partial；类型：model_weight
- `NeoaPred/PepFore/trained_model/best_model.pth`
  - 能力：PepFore best 权重
  - 用途：PepFore 推理时的最佳模型参数
  - 复用状态：partial；类型：model_weight
- `NeoaPred/PepFore/trained_model/model_2.pth`
  - 能力：PepFore 备用权重
  - 用途：PepFore 的另一个训练检查点
  - 复用状态：partial；类型：model_weight

### datasets

- `NeoaPred/PepConf/data/MHC_template_PDB/HLA_A0101.pdb`
  - 能力：HLA template PDB library
  - 用途：peptide-HLA complex 的模板结构
  - 复用状态：partial；类型：unknown
- `NeoaPred/PepConf/data/HLA.list`
  - 能力：HLA/peptide 映射表
  - 用途：allele 列表与 peptide 序列/位置映射
  - 复用状态：ready_for_review；类型：unknown
- `peptides_pdb/HERC1_P3278S_mut_pep.pdb`
  - 能力：示例 mutant/wild-type peptide PDB
  - 用途：demo 输入与人工检查
  - 复用状态：partial；类型：unknown
- `test_1.csv`
  - 能力：测试/评估 CSV
  - 用途：静态 benchmark / demo split
  - 复用状态：partial；类型：unknown
- `NeoaPred/PepConf/embedder/BLOSUM50.dict.npy`
  - 能力：序列嵌入字典
  - 用途：氨基酸表征
  - 复用状态：partial；类型：unknown

### evaluation

- `NeoaPred/PepConf/utils/precision_utils.py`
  - 能力：评分与精度度量
  - 用途：precision / ranking / foreignness 评估
  - 复用状态：ready_for_review；类型：code_entry
- `test_1.csv`
  - 能力：静态评估输入
  - 用途：测试集/示例评估输入
  - 复用状态：partial；类型：unknown
- `APBS-3.0.0.Linux/share/apbs/tests/apbs_tester.py`
  - 能力：APBS upstream validation harness
  - 用途：第三方 APBS 自检，不是 NeoaPred 专用评测
  - 复用状态：partial；类型：code_entry

### inference

- `run_NeoaPred.py`
  - 能力：预测 CLI
  - 用途：加载输入、调用模型、写出预测结果
  - 复用状态：ready_for_review；类型：code_entry
- `NeoaPred/PepConf/utils/seq2pdb.py`
  - 能力：结构导出/松弛
  - 用途：将预测序列/结构转为 PDB 并做 relax
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `NeoaPred/PepConf/model/model.py`
  - 能力：PepConf 结构预测主干
  - 用途：编码 peptide-HLA complex 并输出结构/几何相关预测
  - 复用状态：ready_for_review；类型：code_entry
- `NeoaPred/PepConf/data/input_pipeline.py`
  - 能力：PepConf 数据与特征流水线
  - 用途：读取结构输入、组装 feature、处理 mmCIF/PDB
  - 复用状态：ready_for_review；类型：code_entry
- `NeoaPred/Surface/surface.py`
  - 能力：Surface/mesh 特征生成
  - 用途：生成 surface patch、charge 与几何特征
  - 复用状态：partial；类型：code_entry
- `NeoaPred/PepFore/model.py`
  - 能力：PepFore 评分模型
  - 用途：对候选 neoantigen 做 foreignness/分类打分
  - 复用状态：ready_for_review；类型：code_entry
- `run_NeoaPred.py`
  - 能力：端到端推理驱动
  - 用途：批量加载输入并串联 PepConf/PepFore 输出结果
  - 复用状态：ready_for_review；类型：code_entry
- `APBS-3.0.0.Linux/bin/apbs`
  - 能力：APBS vendored runtime
  - 用途：第三方电势/网格处理与验证工具链
  - 复用状态：partial；类型：unknown

### training

- `NeoaPred/PepConf/utils/loss.py`
  - 能力：PepConf fitting objective
  - 用途：训练/微调时的 loss 计算
  - 复用状态：ready_for_review；类型：code_entry
- `NeoaPred/PepFore/model.py`
  - 能力：PepFore 可训练分类器
  - 用途：训练 foreignness 分类头
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态审查，未执行代码、未安装依赖、未运行测试。
- 未发现可验证的独立 training_entrypoint；训练超参、数据切分与数据来源未公开。
- checkpoints 只能从路径推断为已训练权重，不能证明与当前源码/数据完全可复现。
- APBS/masif 相关 vendored 目录的上游许可与修改范围尚未完全解耦。

## 仍未知

- `NeoaPred/PepConf/trained_model/model_1.pth`、`NeoaPred/PepFore/trained_model/best_model.pth`、`NeoaPred/PepFore/trained_model/model_2.pth` 是否为论文最终权重及其训练集来源未知。
- `NeoaPred/PepConf/data/MHC_template_PDB/` 与 `peptides_pdb/` 的原始来源、授权与清洗规则未知。
- `test_1.csv`、`test_2.csv` 是否为官方评测集、内部拆分或仅示例输入未知。
- `BLOSUM50.dict.npy`、`PhyChem.dict.npy` 的生成流程与外部来源是否被重建未知。
- `APBS-3.0.0.Linux` 中是否完整保留 upstream license notices、以及是否存在本地修改未在清单中显式标注未知。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
