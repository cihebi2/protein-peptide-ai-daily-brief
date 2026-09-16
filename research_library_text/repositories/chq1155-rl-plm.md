# chq1155/rl-plm

- **仓库：** [https://github.com/chq1155/rl-plm](https://github.com/chq1155/rl-plm)
- **固定 commit：** `c901a00040258d9fe7fd27cb3b82680574f0d638`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 0

## 仓库摘要

仓库主要实现面向蛋白序列优化的 RL 研究代码，覆盖 AMP、antibody 与 kinase 三条任务线；静态清单未见 bundled data 或 checkpoints，顶层为 MIT，但 `stable_baselines3` 目录属于 vendored third-party。

## 可复用模块与资源

- 未发现可公开描述的结构化资产。
## 使用限制

- 仅做静态清单分析，未安装依赖、未运行训练/评估、未验证结果。
- 未发现 bundled data 或 checkpoint 路径，因此无法确认是否存在仓库外数据或训练产物。
- `kinase_mutation/stable_baselines3/` 为 vendored third-party，许可证边界需要单独核查。
- `amp_design/generation.py` 存在，但静态证据不足以确认它是独立 inference entrypoint。

## 仍未知

- 外部数据集名称、下载方式与预处理协议未在冻结清单中明确。
- 仓库中未列出 checkpoint 文件，无法判断是否存在未冻结的大权重文件。
- vendored `stable_baselines3` 的上游许可证未被单独解析。
- `amp_design/generation.py` 的实际运行角色仍不确定。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。

## 2026-09-16 复审补充（mass-review 批次）

- **复用度（复审）：** high —— 三条任务管线代码完整（训练/生成/评测/分析），数据与 checkpoint 有官方 Google Drive 发布且带 SHA256 校验清单，任务级 README 齐全
- **许可证（复审）：** MIT
- **能力（复审）：** training_pipeline、inference、benchmark、data_loader

**课题关联：**

- C001 AMP条件活性
- C007 条件生成
- C004 binder/PPI
- C013 基线新颖性

**与论文/课题的组合方式：**

- 结
- 合
- 论
- 文
- 用
-  
- A
- M
- P
-  
- 生
- 成
- 管
- 线
- 复
- 现
-  
- R
- L
-  
- 对
-  
- P
- L
- M
-  
- 的
- 能
- 力
- 扩
- 展
- /
- 收
- 缩
- 诊
- 断
- （
- E
- S
- R
- 、
- D
- u
- a
- l
- -
- R
- e
- w
- a
- r
- d
-  
- E
- S
- R
- ）
- ；
- 其
-  
- r
- e
- w
- a
- r
- d
-  
- h
- a
- c
- k
- i
- n
- g
-  
- 检
- 测
- 协
- 议
- 可
- 直
- 接
- 移
- 植
- 到
-  
- C
- 0
- 0
- 1
- /
- C
- 0
- 0
- 7
-  
- 的
- 条
- 件
- 活
- 性
- 生
- 成
- 评
- 测
- ，
- 作
- 为
- 奖
- 励
- 模
- 型
- 可
- 靠
- 性
- 的
- 校
- 准
- 基
- 线
