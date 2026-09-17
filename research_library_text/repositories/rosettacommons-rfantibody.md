# rosettacommons/rfantibody

- **仓库：** [https://github.com/rosettacommons/rfantibody](https://github.com/rosettacommons/rfantibody)
- **审计批次：** mass-review 论文声明仓库（repos2，浅克隆静态审计）
- **关联论文：** 10.1038/s41586-025-09721-5
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** high —— 工业级端到端管线：CLI + 全流程示例脚本 + 权重自动下载 + Docker/Apptainer 环境固化，MIT 许可且含详尽实战文档（热点选择、过滤策略），可直接部署到 GPU 服务器复现论文抗体设计。
- **能力：** inference、benchmark、protocol

## 仓库摘要

RFantibody：基于结构的 de novo 抗体与纳米抗体设计完整管线，由三部分组成——抗体微调版 RFdiffusion 做 backbone 设计、ProteinMPNN 做序列设计、抗体微调版 RoseTTAFold2 做 in silico 过滤打分。提供 CLI、Docker/Apptainer 镜像与模型权重下载脚本。

## 入口脚本

- src/rfantibody/cli/inference.py
- src/rfantibody/cli/quiver.py
- scripts/rfdiffusion_inference.py
- scripts/proteinmpnn_interface_design.py
- scripts/rf2_predict.py
- scripts/examples/nanobody_full_pipeline.sh

## 数据加载

- scripts/examples/example_inputs（示例输入：HLT 格式靶点/PDB）
- scripts/config/inference（推理配置）

## 模型权重

- include/download_weights.sh（自动下载抗体微调 RFdiffusion、RoseTTAFold2 及 TCR 专用 .pt 权重，如 RFab_noframework-nosidechains-5-10-23_trainingparamsadded.pt）

## 评测基准

- scripts/scoring（设计打分过滤）
- test/

## 文档

- README.md（管线、输入准备、热点选择、CDR 长度等实战指南极详尽）
- CLAUDE.md
- scripts/README
- Dockerfile
- rfantibody.def（Apptainer）

## 课题关联

- C004 binder/PPI（抗体-抗原 binder 设计核心引擎）
- L1蛋白设计（de novo backbone+序列+过滤全链路）
- C007条件生成（基于靶点结构/热点条件的条件生成范式）
- C011评估协议（RF2 结构预测过滤的设计评估协议）

## 与论文/课题的组合方式

- 与 DOI 10.1038/s41586-025-09721-5（RFantibody 论文）组合：用 nanobody_full_pipeline.sh + example_inputs 端到端复现纳米抗体设计；课题组合中作为 C004 binder 课题的生成引擎，与蛋白序列设计/评估模块（如 Chemprop 类打分、ESM 类过滤）拼接成条件生成-评估闭环。
