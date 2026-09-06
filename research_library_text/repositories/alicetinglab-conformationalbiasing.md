# alicetinglab/ConformationalBiasing

- **仓库：** [https://github.com/alicetinglab/ConformationalBiasing](https://github.com/alicetinglab/ConformationalBiasing)
- **固定 commit：** `e6328bc0b3b57ed095f61943732ee4df55376c48`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 10

## 仓库摘要

仓库更像论文伴随资源包：含通用辅助函数、SAXS/寡聚态分析脚本、LPLA 设计示例 notebook 和一组结构/PDB 资源；未见 checkpoint 或可验证的训练/推理入口。

## 可复用模块与资源

### datasets

- `pdbs/b2ar/2rh1_native.pdb`
  - 能力：bundled protein structure set
  - 用途：按蛋白家族组织的 native/AF2/binder PDB 集合
  - 复用状态：partial；类型：unknown
- `saxs/pdbs/1X2H_ChainA_Closed_Monomer.pdb`
  - 能力：SAXS structure set
  - 用途：SAXS/寡聚态分析的结构输入集合
  - 复用状态：partial；类型：unknown

### evaluation

- `saxs/denss.ipynb`
  - 能力：SAXS/寡聚态评估 notebook
  - 用途：SAXS 相关评估、重建与寡聚态分析
  - 复用状态：partial；类型：unknown
- `pdbs/b2ar/af2/active_af2_scores.json`
  - 能力：AF2 评分输出
  - 用途：active/inactive AF2 scores 结果工件
  - 复用状态：partial；类型：config

### inference

- `examples/example_lpla_esmif1.ipynb`
  - 能力：设计示例 notebooks
  - 用途：LPLA 场景下的 ESM-IF1、Frame2Seq、ProteinMPNN、ThermoMPNN 示例设计/打分流程
  - 复用状态：partial；类型：unknown

### reusable_assets

- `utilities/cbutils.py`
  - 能力：共享辅助函数
  - 用途：供 conformation-biasing 工作流复用的通用辅助函数
  - 复用状态：ready_for_review；类型：code_entry
- `colab/CB.ipynb`
  - 能力：演示 notebook
  - 用途：Colab 演示/交互式复现入口
  - 复用状态：partial；类型：unknown
- `saxs/analysis/combined_oligomer_analysis_kratky_addition.py`
  - 能力：SAXS 分析脚本
  - 用途：SAXS/寡聚态后处理与汇总分析
  - 复用状态：ready_for_review；类型：code_entry
- `saxs/analysis/create_complete_enhanced_weighted_averages.py`
  - 能力：SAXS 加权平均脚本
  - 用途：SAXS 信号的增强加权平均计算
  - 复用状态：ready_for_review；类型：code_entry

### training

- `modeling/single_state_kconf_model.ipynb`
  - 能力：单态 kconf 建模 notebook
  - 用途：单态 kconf 建模/参数探索；是否包含实际训练步骤未被静态证实
  - 复用状态：partial；类型：unknown

## 使用限制

- 仅做静态审查，未执行任何代码、Notebook 或测试。
- `environment.yml` 只说明依赖意图，依赖未安装，运行性未验证。
- 未见 checkpoint 文件；模型权重/训练产物未在冻结清单中出现。
- PDB、JSON 和 notebook 输出的上游来源与许可未逐项核验。
- 目录存在不等于流程可复现；外部下载、环境变量和交互式步骤均未验证。

## 仍未知

- `modeling/single_state_kconf_model.ipynb` 是否包含实际训练、拟合或仅分析。
- `examples/*.ipynb` 是否依赖外部权重或数据下载。
- `pdbs/` 与 `saxs/pdbs/` 的原始出处和再分发边界。
- `active_af2_scores.json` / `inactive_af2_scores.json` 是否由仓库脚本生成。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
