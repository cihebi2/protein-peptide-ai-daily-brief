# a-evo-lab/a-evolve

- **仓库：** [https://github.com/a-evo-lab/a-evolve](https://github.com/a-evo-lab/a-evolve)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT（README 徽章声明；仓库根未见 LICENSE 文件）
- **语言：** Python
- **复用度：** medium —— 代码、文档、示例、种子工作区与评测 artifacts 齐全，但实际运行需自配 LLM API key 与各 benchmark 环境（OSWorld/SWE-bench 等重依赖），非开箱即用
- **能力：** benchmark、protocol

## 仓库摘要

A-Evolve（arXiv 2602.00359）是自改进 LLM Agent 的通用进化基础设施：任意 agent + 任意 benchmark + 任意进化算法，3 行 API（ae.Evolver）零人工干预进化，在 MCP-Atlas、SWE-bench Verified、Terminal-Bench 2.0、OSWorld、ARC-AGI、SkillsBench 上验证（如 Claude Opus-4.6 基线 +2.6~+15.2pp）。

## 入口脚本

- agent_evolve/api.py（ae.Evolver 入口）
- examples/*/run_*.sh（MCP/SWE/OSWorld/ARC/Skillbench/Terminal-Bench 复现脚本）
- Makefile

## 数据加载

- agent_evolve/benchmarks（内置基准适配层）
- seed_workspaces/（arc/mcp/swe/osworld 等 种子工作区）

## 模型权重

- 无内置权重；依赖外部 LLM API（如 Claude Opus-4.6）；artifacts/ 附 baseline_eval 与 final_eval 5 试次 JSON 结果

## 评测基准

- agent_evolve/benchmarks
- artifacts/mcp_mh_opus46/baseline_eval_5trials.json
- artifacts/mcp_mh_opus46/final_eval_5trials.json
- examples/harness-disentangling/

## 文档

- README.md
- QUICKSTART.md
- DESIGN.md
- CLAUDE.md
- docs/

## 课题关联

- （无）

## 与论文/课题的组合方式

- 与
- 生
- 物
- 课
- 题
- 族
- 无
- 直
- 接
- 关
- 联
- ；
- 其
-  
- b
- a
- s
- e
- l
- i
- n
- e
-  
- v
- s
-  
- f
- i
- n
- a
- l
-  
- 多
- 试
- 次
- 评
- 测
-  
- a
- r
- t
- i
- f
- a
- c
- t
- s
-  
- 与
- 统
- 一
- 评
- 测
-  
- h
- a
- r
- n
- e
- s
- s
-  
- 设
- 计
- ，
- 可
- 作
- 为
-  
- C
- 0
- 1
- 1
-  
- 评
- 估
- 协
- 议
- 课
- 题
- 的
- 方
- 法
- 论
- 参
- 照
- （
- 如
- 何
- 隔
- 离
-  
- h
- a
- r
- n
- e
- s
- s
-  
- 差
- 异
- 、
- 固
- 定
- 多
- 试
- 次
- 评
- 测
- ）
- 。
