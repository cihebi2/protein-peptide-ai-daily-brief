# abbey4799/cello

- **仓库：** [https://github.com/abbey4799/cello](https://github.com/abbey4799/cello)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** high —— 评测数据、打分器、模型结果全部内嵌仓库，eval/score 脚本一键运行（仅需自备被评模型 API）
- **能力：** benchmark、protocol、database、inference

## 仓库摘要

CELLO（AAAI 2024）：系统评估大模型复杂指令遵循能力的基准——8 类指令特征、4 项评估标准与配套度量实现，含中英文代表模型的完整评测结果。

## 入口脚本

- code/eval.py
- code/score.py
- eval.sh
- score.sh

## 数据加载

- data/（13 个任务类别 JSON 评测集随仓库内嵌，已匿名化）

## 模型权重

- 无（评测对象为外部 LLM：ChatGLM 等，经 code/evaluators/ 的 API 适配器调用）

## 评测基准

- code/scorers/（按约束分解的多准则打分器）
- scores/
- results/（各模型原始输出）

## 文档

- README.md
- framework.png

## 课题关联

- C008
- C011

## 与论文/课题的组合方式

- 其'特征分解×多准则打分器'的评估协议架构可直接迁移到 C011 评估协议课题（如 LLM 辅助科学评测的协议设计）
- 基准+逐约束打分+模型结果汇总的组织方式可作为 C008 基准校准课题的仓库模板
