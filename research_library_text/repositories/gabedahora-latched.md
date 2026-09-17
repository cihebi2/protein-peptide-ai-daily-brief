# gabedahora/latched

- **仓库：** [https://github.com/gabedahora/latched](https://github.com/gabedahora/latched)
- **审计批次：** peptide-core 论文声明仓库
- **关联论文：** 10.1021/jacs.3c10126
- **分析边界：** 仅静态审计
- **许可证：** none
- **复用度：** low —— 单文件 Tcl 脚本、强依赖 VMD 环境、无 LICENSE 文件（默认版权保留，法律复用风险）、无打包/无测试/无参数化 CLI，仅适用于 lasso 肽结构这一狭窄场景；逻辑简单可按几何算法重实现

## 仓库摘要

LATCHED（Lasso Threading Classification and Handedness Evaluation Descriptor）：单文件 VMD/Tcl 脚本，用于检验 lasso 肽（套索肽）的环是否被尾部穿线——区分 lasso 与 tadpole 构型；若为 lasso 进一步判定穿线为左手或右手。运行方式为 vmd -dispdev text -e latched_v1.tcl，输出 3 个文本文件（相交/穿线计算、lasso 或 pre-tadpole 判定、左右手性判定）。仓库极简，仅 README 与脚本两个文件，另有 Zenodo 存档（records/14618067）。

## 入口脚本

- latched_v1.tcl（唯一入口：vmd -dispdev text -e latched_v1.tcl，对 VMD 当前加载的分子结构执行）

## 数据加载

- 经 VMD 加载的分子结构（PDB/PSF 等由 VMD 自身解析，脚本不自带独立加载器）

## 模型权重

- 无（纯几何/拓扑判定脚本，不含模型与权重）

## 评测基准

- 无（无测试、无基准数据集）

## 文档

- README.md（简短说明：用途、运行命令、输出内容）
- Zenodo 存档记录（records/14618067）

## 课题关联

- C011 评估协议：中等相关——可作为生成式 lasso 肽设计的输出结构有效性评估器（判定生成/折叠结构是否保持穿线拓扑及手性）
- L3 肽性质：弱相关——提供 lasso 肽拓扑/手性这一结构性质端点，但非序列-性质预测模型
- L4/L5 肽生成与优化：间接相关——作为 lasso 肽生成-评估闭环中的结构过滤器
- C001/C002/C003/C004/C007/C008/C010/C013：基本不相关（无活性/毒性/结合/生成/校准内容）

## 与论文/课题的组合方式

- 对应论文 10.1021/jacs.3c10126（lasso 肽拓扑分类/手性评估相关工作）：建议在 L4 lasso 肽生成课题中把 LATCHED 纳入 C011 式评估协议，对生成结构做拓扑与手性约束检验
- 与 jertubiana/pgm 类生成模型组合：生成→结构预测→LATCHED 拓扑过滤，可构成 lasso 肽的条件生成/筛选管线（需自行粘合，无现成接口）
- L3 课题可将手性/穿线作为离散结构性质标签，但需自行批量调用并解析输出文本
