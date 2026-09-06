# atomicarchitects/equivariant-SBS

- **仓库：** [https://github.com/atomicarchitects/equivariant-SBS](https://github.com/atomicarchitects/equivariant-SBS)
- **固定 commit：** `c1287118f56a3e62ab75cc5237fc37dcb6298932`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 5

## 仓库摘要

从冻结清单看，仓库主要是对称性破缺相关的示例材料：一个 GAP 反例脚本、三组 Jupyter notebooks（BaTiO3、Chiral Octagon、Triangular Prism）及其 PNG 输出；未发现独立数据集、训练入口、推理模块、评测脚本或 checkpoint 文件。

## 可复用模块与资源

### reusable_assets

- `GAP script/counterexample.g`
  - 能力：methods
  - 用途：GAP 反例/对称性破缺构造脚本，可作为方法实现参考
  - 复用状态：ready_for_review；类型：unknown
- `Notebooks/BaTiO3/BaTiO3.ipynb`
  - 能力：methods
  - 用途：BaTiO3 示例 notebook；配套生成/展示目标与模型变体图
  - 复用状态：partial；类型：unknown
- `Notebooks/Chiral Octagon/Chiral octagon.ipynb`
  - 能力：methods
  - 用途：Chiral Octagon 示例 notebook；演示单例与对照图
  - 复用状态：partial；类型：unknown
- `Notebooks/Triangular Prism/Triangular prism.ipynb`
  - 能力：methods
  - 用途：Triangular Prism 示例 notebook；演示多种构型图
  - 复用状态：partial；类型：unknown
- `requirements.txt`
  - 能力：dependencies
  - 用途：Python 依赖清单；用于重建 notebook 运行环境
  - 复用状态：partial；类型：unknown

## 使用限制

- 仅做静态清单分析，未执行仓库代码或 notebook。
- 未发现独立数据集目录、训练入口、推理模块、评测脚本或 checkpoint 文件。
- `requirements.txt` 存在，但依赖能否成功安装、版本是否兼容都未验证。
- PNG 多为 notebook 输出图，不能当作可复现数据集或模型产物证据。

## 仍未知

- notebook 单元格内部逻辑与外部数据来源未逐一核验。
- GAP 脚本与 notebooks 的实际运行结果未验证。
- PNG/Notebook 产物是否有独立授权说明未见。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
