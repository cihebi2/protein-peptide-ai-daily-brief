# Graylab/FLAb

- **仓库：** [https://github.com/Graylab/FLAb](https://github.com/Graylab/FLAb)
- **固定 commit：** `e05e3f0135783ffb7de412df6a1467e7a0031911`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** found
- **资产记录数：** 19

## 仓库摘要

仓库主要提供抗体 fitness 预测基准数据、多个预训练模型的打分封装，以及大量静态评估结果；未见可执行的训练入口、推理流水线或 tracked checkpoint。

## 可复用模块与资源

### datasets

- `data/binding/AbRank_dataset.csv.zip`
  - 能力：binding 基准数据
  - 用途：Kd / IC50 / binary affinity 任务的汇总数据
  - 复用状态：partial；类型：unknown
- `data/expression/adams2017measuring_4420-fluorescein_exp_er.csv`
  - 能力：expression 基准数据
  - 用途：表达量/ER/HEK 相关标签
  - 复用状态：partial；类型：unknown
- `data/aggregation/jain2024assessment_HIC.csv`
  - 能力：aggregation / developability 数据
  - 用途：HIC、SEC、CSI、ACSINS、SAS、SGAC、SMAC 等聚集与理化性质任务
  - 复用状态：partial；类型：unknown
- `data/polyreactivity/jain2024assessment_PSR.csv`
  - 能力：polyreactivity 数据
  - 用途：ELISA、CICRT、PSR、heme 等多种多反应性任务
  - 复用状态：partial；类型：unknown
- `data/thermostability/jain2024assessment_Tm.csv`
  - 能力：thermostability 数据
  - 用途：Tm、DSF、DLS、NbThermo 等热稳定性任务
  - 复用状态：partial；类型：unknown
- `data/pharmacokinetics/jain2024assessment_tg32_halflife.csv`
  - 能力：pharmacokinetics 数据
  - 用途：FcRn、RT、clearance、halflife 与 pI 相关任务
  - 复用状态：partial；类型：unknown
- `data/immunogenicity/marks2021humanization_immunogenicity.csv`
  - 能力：immunogenicity 数据
  - 用途：抗体免疫原性任务
  - 复用状态：partial；类型：unknown

### evaluation

- `score/antiberty/binding/Hie2022_C143_Kd/Hie2022_C143_Kd_corr.csv`
  - 能力：AntiBerty 评估产物
  - 用途：多任务相关系数、plot 与 ppl 静态结果
  - 复用状态：partial；类型：unknown
- `score/esmif/binding/Rosace2023_Adalimumab_Kd/Rosace2023_Adalimumab_Kd_corr.csv`
  - 能力：ESM-IF 评估产物
  - 用途：多任务相关系数、plot 与 ppl 静态结果
  - 复用状态：partial；类型：unknown
- `score/iglm/binding/Warszawski2019_d44_Kd/Warszawski2019_d44_Kd_corr.csv`
  - 能力：IGLM 评估产物
  - 用途：多任务相关系数、plot 与 ppl 静态结果
  - 复用状态：partial；类型：unknown
- `score/mpnn/binding/gsk2023_D25_Kd/gsk2023_D25_Kd_corr.csv`
  - 能力：ProteinMPNN 评估产物
  - 用途：多任务相关系数、plot 与 ppl 静态结果
  - 复用状态：partial；类型：unknown
- `score/progen/base/binding/Hie2022_C143_Kd/Hie2022_C143_Kd_corr.csv`
  - 能力：PROGEN 评估产物
  - 用途：多版本 PROGEN 基线的静态评估结果
  - 复用状态：partial；类型：unknown
- `score/pyrosetta/binding/Hie2022_MEDI8852_Kd/Hie2022_MEDI8852_Kd_corr.csv`
  - 能力：PyRosetta 评估产物
  - 用途：结构能量打分的静态评估结果
  - 复用状态：partial；类型：unknown

### inference

- `models/scoring_esm2_8M.py`
  - 能力：语言模型打分推断
  - 用途：对抗体序列做 zero-shot 或似然打分推断
  - 复用状态：partial；类型：code_entry
- `models/scoring_esmif.py`
  - 能力：结构相关打分推断
  - 用途：对序列/结构做结构感知评分
  - 复用状态：partial；类型：code_entry
- `models/ft_scoring_esm2_150M.py`
  - 能力：微调版打分接口
  - 用途：封装微调后模型的评分接口，如 ESM2、IgFold、ISM、AntiBerty 等
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `README.md`
  - 能力：项目说明与入口文档
  - 用途：总体仓库说明、任务入口与目录导航
  - 复用状态：partial；类型：unknown
- `examples/FLAb_ZeroShotExample_IgLM_Expression.ipynb`
  - 能力：示例 notebook
  - 用途：演示零样本表达分数的使用方式
  - 复用状态：partial；类型：unknown
- `models/scoring_bp_gravy.py`
  - 能力：生化特征辅助代码
  - 用途：计算 GRAVY 等序列理化特征，可作为轻量基线或特征提取模块
  - 复用状态：partial；类型：code_entry

## 使用限制

- 仅做静态清单审查，未执行代码、未安装依赖、未运行测试。
- tracked 路径存在不等于可复现或可执行，尤其是 score/ 下的结果文件。
- 未发现训练入口、配置 recipe、数据加载器或 checkpoint 文件。
- 部分数据集可能是外部文献汇编而来，但冻结清单未给出完整来源许可链。

## 仍未知

- `models/*.py` 是否依赖未跟踪的外部 checkpoint 或私有权重，静态清单无法确认。
- `score/` 目录中的结果是否由本仓库当前版本生成，还是导入的历史产物，无法仅凭路径判断。
- `LICENSE` 的具体许可证文本类别未解析为 SPDX，代码再利用边界需人工复核。
- 各 CSV/zip 数据的原始采集协议、清洗规则与二次分发条件未从清单中完全确定。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
