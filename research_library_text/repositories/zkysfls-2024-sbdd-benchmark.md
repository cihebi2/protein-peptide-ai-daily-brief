# zkysfls/2024-sbdd-benchmark

- **仓库：** [https://github.com/zkysfls/2024-sbdd-benchmark](https://github.com/zkysfls/2024-sbdd-benchmark)
- **固定 commit：** `fbe82b4369b0166a44dbfa35c8948b0429fcf35f`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 4

## 仓库摘要

该仓库是 SBDD benchmark 的静态评测/分析辅助项目，主要资产是评测脚本与两个 conda 环境文件；未见训练入口、推理模块、数据集或 checkpoint。

## 可复用模块与资源

### evaluation

- `evaluation.py`
  - 能力：artifact_kind=code_entry; evaluation script
  - 用途：结构基准的评测入口与指标计算
  - 复用状态：partial；类型：code_entry
- `results_compare.py`
  - 能力：artifact_kind=code_entry; result comparison helper
  - 用途：结果汇总、对比与分析辅助
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `environment_TDCEnv.yml`
  - 能力：artifact_kind=config; conda environment definition
  - 用途：评测/运行所需依赖环境之一
  - 复用状态：partial；类型：config
- `environment_TestEnv.yml`
  - 能力：artifact_kind=config; conda environment definition
  - 用途：测试/对照环境定义
  - 复用状态：partial；类型：config

## 使用限制

- 仅基于静态清单，未执行代码、未安装依赖、未运行测试。
- 未见 bundled data、checkpoint、training entrypoint 或 inference module。
- 两个 notebook 存在但未逐格检查，内部是否引用外部数据源或下载流程未知。

## 仍未知

- README 与 notebook 的具体方法细节、指标定义和外部数据依赖未核验。
- evaluation.py 与 results_compare.py 的实际输入输出契约未从文件内容确认。
- 仓库是否依赖外部下载的数据集或第三方结果文件，当前静态证据不足。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。

## 2026-09-16 复审补充（mass-review 批次）

- **复用度（复审）：** medium —— 统一评测与结果比较代码完整（MIT），但 16 个方法的实现分布在两套 conda 环境与外部依赖中，预处理数据/模型未在克隆工作区内，复现工作量大
- **许可证（复审）：** MIT
- **能力（复审）：** benchmark、protocol、visualization

**课题关联：**

- C008 基准校准
- C011 评估协议
- C013 基线新颖性
- C016 docking

**与论文/课题的组合方式：**

- 作
- 为
-  
- C
- 0
- 0
- 8
- /
- C
- 0
- 1
- 3
-  
- 的
- 基
- 线
- 池
- ：
- 1
- 6
-  
- 个
-  
- 2
- D
- /
- 3
- D
-  
- 方
- 法
- 的
- 配
- 置
- 与
- 评
- 测
- 口
- 径
- 可
- 直
- 接
- 借
- 用
- 来
- 检
- 验
- 新
- 方
- 法
- 相
- 对
- 基
- 线
- 的
- 新
- 颖
- 性
- ；
- 其
-  
- e
- v
- a
- l
- u
- a
- t
- i
- o
- n
- .
- p
- y
-  
- 的
- 统
- 一
- 指
- 标
- 栈
- 可
- 并
- 入
- 自
- 建
- 评
- 估
- 协
- 议
- （
- C
- 0
- 1
- 1
- ）
- 。
