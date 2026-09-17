# grosenberger/easypqp

- **仓库：** [https://github.com/grosenberger/easypqp](https://github.com/grosenberger/easypqp)
- **审计批次：** peptide-core 论文声明仓库
- **关联论文：** 10.1038/s41467-023-40129-9
- **分析边界：** 仅静态审计
- **许可证：** BSD-3-Clause
- **复用度：** high —— PyPI 正式发布、CLI+Docker 双分发、pytest 回归测试与 CI 齐全、文档完整，可直接安装复用；唯一外部依赖 easypqp_rs 为可选 extras

## 仓库摘要

EasyPQP 是面向 OpenSWATH/DIA 定量蛋白质组学的 Python 命令行工具与包，用于从数据库搜索引擎（MSFragger/Sage 等 pepXML/idXML/TSV）结果生成肽查询参数（PQP）谱图库；支持保留时间（RT）与离子淌度（CCS）的内/外标校准、累积库与 run-specific 库生成、基于 UniMod 的 PTM 特异库过滤与 decoy 生成，并通过 easypqp_rs 扩展提供 in-silico 库生成（自动下载 AlphaPeptDeep 式 RT/CCS/MS2 预训练深度模型）。

## 入口脚本

- easypqp CLI（pyproject console script；实现在 easypqp/main.py）
- 子命令：convert / convertpsm / convertsage / library / insilico-library / reduce / filter-unimod / openswath-assay-generator / openswath-decoy-generator / targeted-file-converter
- Dockerfile（DockerHub: grosenberger/easypqp）

## 数据加载

- easypqp/convert.py（pepXML/idXML/TSV，MSFragger 等搜索引擎输出）
- easypqp/sage.py + convertsage（Sage 结果 TSV）
- easypqp/library.py（.peakpkl/.psmpkl、PQP 库读写）
- easypqp/unimoddb.py + easypqp/data/unimod.xml（UniMod PTM 数据库）
- easypqp/openswathassaygenerator.py / openswathdecoygenerator.py / targetedfileconverter.py（PQP↔TSV 转换、assay/decoy 生成）
- tests/data/（示例 FASTA、PQP、Sage TSV 等小型样本数据）

## 模型权重

- 仓库内无权重；in-silico 库功能运行时自动下载预训练模型（easypqp_rs）：RT 模型 rt_cnn_tf、CCS 模型 ccs_cnn_tf（基于 ProteomicsML RT/CCS 数据集训练的 CNN-Transformer）、MS2 模型 ms2_bert（AlphaPeptDeep 预训练）

## 评测基准

- tests/（pytest 单元与回归测试，8 个测试模块 + _regtest_outputs 期望输出）
- 无独立学术基准脚本；质量保障以回归测试 + GitHub Actions CI 为主

## 文档

- README.md
- CHANGELOG.md
- CONTRIBUTING.md
- Dockerfile
- .github/workflows/（ci、dockerpublish、pythonpublish、changelog）

## 课题关联

- L3 肽性质：弱相关——提供肽 RT/离子淌度/MS2 谱预测与校准管线（AlphaPeptDeep/ProteomicsML 生态），属肽理化/谱学性质预测的邻近领域，但面向质谱分析而非设计导向
- C008 基准校准：边缘相关——其『校准』为分析化学的内/外标 RT 校准，非 ML 概率校准，仅概念可借鉴
- C011 评估协议：边缘相关——回归测试与 QC 流程实践可参考，非模型评估协议

## 与论文/课题的组合方式

- 对应论文 10.1038/s41467-023-40129-9 为 EasyPQP 方法学论文：可用作 L3 肽性质预测的外部基线对照（ProteomicsML RT/CCS 数据 + AlphaPeptDeep 系预训练模型），检验自研 RT/IM 预测器
- 对 C001/C007/L4/L5 生成式肽设计课题：可作为湿实验侧 DIA 靶向验证数据管线（生成的候选肽→assay 库→靶向质谱验证），属间接组合
- 对 C002/C003/C004/C010/C013：无明显直接组合点
