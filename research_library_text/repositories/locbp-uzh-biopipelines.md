# locbp-uzh/biopipelines

- **仓库：** [https://github.com/locbp-uzh/biopipelines](https://github.com/locbp-uzh/biopipelines)
- **固定 commit：** `bbc3152c3acb947d431f38aa9c45ac403867132c`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 12

## 仓库摘要

BioPipelines 是面向蛋白与配体设计的工作流框架，主要提供工具封装、环境配置和示例流水线；未见本地训练数据或模型权重。

## 可复用模块与资源

### evaluation

- `pipe_scripts/pipe_posebusters.py`
  - 能力：构象/姿势几何评估
  - 用途：调用 Posebusters 做配体姿势合理性检查
  - 复用状态：partial；类型：code_entry
- `biopipelines/extract_metrics.py`
  - 能力：指标汇总
  - 用途：从管线输出中提取并汇总评估指标
  - 复用状态：ready_for_review；类型：code_entry
- `biopipelines/rtmscore.py`
  - 能力：结构/界面打分
  - 用途：提供 rtmscore 相关评价封装
  - 复用状态：partial；类型：code_entry

### inference

- `biopipelines/rfdiffusion.py`
  - 能力：结构生成/蛋白设计编排
  - 用途：封装 RFdiffusion 相关设计流程与参数适配
  - 复用状态：partial；类型：code_entry
- `pipe_scripts/pipe_dna_encoder.py`
  - 能力：DNA 编码管线入口
  - 用途：把 DNA 编码模块接入可运行流水线
  - 复用状态：partial；类型：code_entry
- `pipe_scripts/pipe_esmfold_inference.py`
  - 能力：结构预测推理
  - 用途：执行 ESMFold 推理与结构生成
  - 复用状态：partial；类型：code_entry
- `pipe_scripts/pipe_gnina.py`
  - 能力：分子对接与打分
  - 用途：驱动 gnina 对接/打分流程
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `biopipelines/dna_encoder.py`
  - 能力：DNA 编码与序列预处理
  - 用途：封装 DNA 编码逻辑，供上层管线复用
  - 复用状态：ready_for_review；类型：code_entry
- `biopipelines/_weights_cache.py`
  - 能力：权重缓存/下载定位
  - 用途：管理外部模型权重的缓存与定位，不是权重本体
  - 复用状态：partial；类型：code_entry
- `Dockerfile.container`
  - 能力：容器构建配置
  - 用途：构建可复现运行环境
  - 复用状态：ready_for_review；类型：unknown
- `pyproject.toml`
  - 能力：Python 依赖与打包配置
  - 用途：定义项目依赖、打包与工具链配置
  - 复用状态：ready_for_review；类型：config
- `environments/biopipelines.yaml`
  - 能力：环境/部署配方
  - 用途：描述整仓库的环境约束与安装配方
  - 复用状态：ready_for_review；类型：config

## 使用限制

- 仅做冻结清单静态审阅，未执行仓库代码。
- 未安装依赖，无法验证外部工具、环境配方或参数是否可运行。
- 静态清单未显示 bundled dataset、训练入口或 checkpoint 文件；实际权重可能由外部下载器按需获取。
- 测试目录与示例 notebook 只能说明存在演示/校验资产，不能证明论文结果可复现。

## 仍未知

- biopipelines/_weights_cache.py 实际指向哪些外部权重源，静态清单无法确认。
- 各 example_pipelines 是否与论文正式实验完全一致，无法仅凭路径判断。
- 部分 wrapper 是否只是调用上游工具、是否包含任何 vendored 代码，未读文件内容无法完全区分。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
