# bytedance/decompdiff

- **仓库：** [https://github.com/bytedance/decompdiff](https://github.com/bytedance/decompdiff)
- **固定 commit：** `ed4e7d8202c077cc4bd1b9ca626e173c24007f2a`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** found
- **资产记录数：** 10

## 仓库摘要

静态盘点显示该仓库提供 DecompDiff 的模型、训练、采样、预处理和评估代码，但未发现 bundled data 或 checkpoints，许可仅能确认 LICENSE 存在。

## 可复用模块与资源

### datasets

- `configs/preprocessing/crossdocked.yml`
  - 能力：CrossDocked 数据预处理链
  - 用途：配置并驱动 CrossDocked 风格蛋白-配体数据的清洗、切分和装载
  - 复用状态：partial；类型：config
- `configs/preprocessing/pdbbind.yml`
  - 能力：PDBbind 数据预处理链
  - 用途：配置并驱动 PDBbind 子复合物构建与加载流程
  - 复用状态：partial；类型：config

### evaluation

- `scripts/evaluate_mol_from_meta_full.py`
  - 能力：分子性质与结构评估
  - 用途：评估原子数、原子类型、键长、相似性和综合得分
  - 复用状态：ready_for_review；类型：code_entry
- `utils/evaluation/docking.py`
  - 能力：对接与 SA 支持
  - 用途：提供 docking、Vina 封装、ARM 统计和 synthetic accessibility 支持
  - 复用状态：partial；类型：code_entry

### inference

- `scripts/sample_diffusion_decomp.py`
  - 能力：扩散采样入口
  - 用途：按漂移/引导配置生成候选分子
  - 复用状态：ready_for_review；类型：code_entry
- `utils/reconstruct.py`
  - 能力：采样后处理
  - 用途：将采样结果还原为分子并进行可视化
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `models/decompdiff.py`
  - 能力：DecompDiff 核心扩散模型
  - 用途：定义蛋白-配体结构生成主模型，并与编码器和转移模块协同工作
  - 复用状态：ready_for_review；类型：code_entry
- `utils/reconstruct.py`
  - 能力：几何与重建辅助模块
  - 用途：用于坐标变换、分子重建和化学辅助处理
  - 复用状态：ready_for_review；类型：code_entry

### training

- `scripts/train_diffusion_decomp.py`
  - 能力：扩散模型训练入口
  - 用途：启动并配置 DecompDiff 训练流程
  - 复用状态：ready_for_review；类型：code_entry
- `utils/train.py`
  - 能力：训练辅助与数据装配
  - 用途：提供训练循环、调度和数据装配辅助
  - 复用状态：partial；类型：code_entry

## 使用限制

- 仅做静态清单审阅，未执行仓库代码。
- 未安装依赖、未运行测试，不能证明可复现或可运行。
- 未发现 tracked bundled data 或 checkpoint 文件。
- LICENSE 已发现，但未解析出 SPDX，具体条款需人工核读。

## 仍未知

- CrossDocked/PDBbind 仅从配置与脚本路径可见，实际数据版本与获取方式未核实。
- utils/evaluation/sascorer.py 与 fpscores.pkl.gz 的第三方来源与许可未核实。
- 仓库中是否存在未跟踪大文件或外部下载产物，静态清单无法确认。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
