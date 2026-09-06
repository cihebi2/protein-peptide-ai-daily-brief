# EperLuo/scDiffusion

- **仓库：** [https://github.com/EperLuo/scDiffusion](https://github.com/EperLuo/scDiffusion)
- **固定 commit：** `e20ee19090739a874fd8ae001d8337e4d480e52b`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 25

## 仓库摘要

静态清点显示该仓库围绕 scDiffusion 的单细胞条件生成任务组织：包含 VAE/扩散模型实现、训练脚本、采样入口、多个单细胞数据集加载器，以及若干 downstream evaluation notebook；未见 tracked bundled data 或 checkpoint，代码许可为 MIT。

## 可复用模块与资源

### datasets

- `guided_diffusion/cell_datasets_loader.py`
  - 能力：dataset_loader
  - 用途：单细胞数据集加载入口/分发器
  - 复用状态：partial；类型：code_entry
- `guided_diffusion/cell_datasets_WOT.py`
  - 能力：dataset_loader
  - 用途：WOT 数据集适配/读取
  - 复用状态：partial；类型：code_entry
- `guided_diffusion/cell_datasets_lung.py`
  - 能力：dataset_loader
  - 用途：lung 数据集适配/读取
  - 复用状态：partial；类型：code_entry
- `guided_diffusion/cell_datasets_muris.py`
  - 能力：dataset_loader
  - 用途：muris 数据集适配/读取
  - 复用状态：partial；类型：code_entry
- `guided_diffusion/cell_datasets_pbmc.py`
  - 能力：dataset_loader
  - 用途：PBMC 数据集适配/读取
  - 复用状态：partial；类型：code_entry
- `guided_diffusion/cell_datasets_sapiens.py`
  - 能力：dataset_loader
  - 用途：sapiens 数据集适配/读取
  - 复用状态：partial；类型：code_entry

### evaluation

- `exp_script/script_static_eval.ipynb`
  - 能力：evaluation_notebook
  - 用途：静态评测 notebook
  - 复用状态：partial；类型：unknown
- `exp_script/script_random_forest.ipynb`
  - 能力：evaluation_notebook
  - 用途：随机森林下游评测 notebook
  - 复用状态：partial；类型：unknown
- `exp_script/down_stream_analysis_muris.ipynb`
  - 能力：evaluation_notebook
  - 用途：muris 下游分析 notebook
  - 复用状态：partial；类型：unknown
- `exp_script/script_diffusion_umap.ipynb`
  - 能力：evaluation_notebook
  - 用途：扩散结果 UMAP 可视化 notebook
  - 复用状态：partial；类型：unknown
- `exp_script/script_diffusion_interpolation.ipynb`
  - 能力：evaluation_notebook
  - 用途：插值实验/分析 notebook
  - 复用状态：partial；类型：unknown
- `exp_script/script_diffusion_multi-condi.ipynb`
  - 能力：evaluation_notebook
  - 用途：多条件生成/分析 notebook
  - 复用状态：partial；类型：unknown

### inference

- `cell_sample.py`
  - 能力：inference_entrypoint
  - 用途：单细胞生成/采样入口
  - 复用状态：partial；类型：code_entry
- `classifier_sample.py`
  - 能力：inference_entrypoint
  - 用途：分类器推理/采样入口
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `VAE/VAE_model.py`
  - 能力：model_architecture
  - 用途：VAE 主模型定义
  - 复用状态：ready_for_review；类型：code_entry
- `guided_diffusion/cell_model.py`
  - 能力：model_architecture
  - 用途：条件细胞扩散模型定义
  - 复用状态：ready_for_review；类型：code_entry
- `guided_diffusion/gaussian_diffusion.py`
  - 能力：model_architecture
  - 用途：扩散过程与采样数学核心
  - 复用状态：ready_for_review；类型：code_entry
- `guided_diffusion/nn.py`
  - 能力：training_support
  - 用途：神经网络基础构件
  - 复用状态：partial；类型：code_entry
- `guided_diffusion/losses.py`
  - 能力：training_support
  - 用途：训练损失实现
  - 复用状态：partial；类型：code_entry

### training

- `train.sh`
  - 能力：training_entrypoint
  - 用途：顶层训练启动脚本
  - 复用状态：partial；类型：code_entry
- `guided_diffusion/train_util.py`
  - 能力：training_module
  - 用途：扩散模型训练循环与辅助逻辑
  - 复用状态：partial；类型：code_entry
- `VAE/VAE_train.py`
  - 能力：training_entrypoint
  - 用途：VAE 训练脚本
  - 复用状态：partial；类型：code_entry
- `cell_train.py`
  - 能力：training_entrypoint
  - 用途：cell 模型训练脚本
  - 复用状态：partial；类型：code_entry
- `classifier_train.py`
  - 能力：training_entrypoint
  - 用途：分类器训练脚本
  - 复用状态：partial；类型：code_entry
- `celltypist_train.py`
  - 能力：training_entrypoint
  - 用途：CellTypist 相关训练脚本
  - 复用状态：partial；类型：code_entry

## 使用限制

- 仅做静态清点，未安装依赖、未运行代码、未验证训练/推理/评测结果。
- tracked inventory 中未见 bundled data，当前只能确认数据加载器/适配器代码存在。
- tracked inventory 中未见 checkpoint 文件，因此没有可复用模型权重可直接确认。
- 部分 notebook 仅能证明评测/分析材料存在，不能证明其中指标已成功复现。

## 仍未知

- guided_diffusion 目录是否为原创实现还是第三方改编，当前没有足够 provenance 证据。
- 各数据加载器是否依赖外部下载源、具体数据版本与数据许可边界未见。
- classifier_train.py、celltypist_train.py 与各 evaluation notebook 的实际运行参数和输出未被静态验证。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
