# aaronhuang-778/billm

- **仓库：** [https://github.com/aaronhuang-778/billm](https://github.com/aaronhuang-778/billm)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** high —— 单条命令即可对 HF 开源 LLM 完成 1-bit 量化与 ppl 评测（模型与校准数据均自动拉取），依赖极简（4 个包）
- **能力：** inference、benchmark、data_loader

## 仓库摘要

BiLLM（HKU/北航/ETH）：面向预训练 LLM 的 1-bit 后训练量化方案，通过显著权重结构选择 + 二值残差近似 + 最优分裂搜索，在 1.08-bit 下保持高精度推理（LLaMA2-70B ppl 8.41）。

## 入口脚本

- run.py
- run.sh

## 数据加载

- datautils.py（c4/WikiText2/PTB 校准与评测数据，经 HF datasets 自动加载）

## 模型权重

- 无自带权重；直接量化 HF 模型（facebook/opt-6.7b、meta-llama/Llama-2-7b-hf、lmsys/vicuna-7b-v1.5 等）

## 评测基准

- eval_ppl_utils.py（perplexity 评测）
- utils/autosearch.py（最优分裂搜索）

## 文档

- README.md
- requirements.txt

## 课题关联

- （无）

## 与论文/课题的组合方式

- 与
- 当
- 前
- 蛋
- 白
- /
- 分
- 子
- 课
- 题
- 族
- 无
- 直
- 接
- 关
- 联
- ；
- 若
- 后
- 续
- 课
- 题
- 需
- 在
- 单
- 张
- 消
- 费
- 级
-  
- G
- P
- U
-  
- 上
- 部
- 署
- 本
- 地
-  
- L
- L
- M
-  
- 辅
- 助
- 标
- 注
- 或
- 生
- 成
- ，
- 可
- 作
- 为
- 模
- 型
- 压
- 缩
- 部
- 署
- 的
- 现
- 成
- 工
- 具
- 。
