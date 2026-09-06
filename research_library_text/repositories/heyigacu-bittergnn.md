# heyigacu/BitterGNN

- **仓库：** [https://github.com/heyigacu/BitterGNN](https://github.com/heyigacu/BitterGNN)
- **固定 commit：** `80baa233351bc1ee8e0a7f03fc9f22e3e8d0cf20`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 22

## 仓库摘要

仓库包含 BitterGNN 的核心图网络实现、多个对照 GNN/味觉基线、公开性质数据与味觉数据 CSV、以及对应的预训练权重；但未见独立训练入口或明确评测流水线，且本次仅做静态盘点，无法证明可复现运行。

## 可复用模块与资源

### checkpoints

- `pretrained/bn_hgnn.pth`
  - 能力：bitterness 二分类预训练权重
  - 用途：面向 bn 任务的 HGNN 权重；同目录还有 bn_afp、bn_gsage、bn_wln
  - 复用状态：partial；类型：model_weight
- `pretrained/bs_hgnn.pth`
  - 能力：bitter/sweet 预训练权重
  - 用途：面向 bs 任务的 HGNN 权重；同目录还有 bs_afp、bs_gsage、bs_wln
  - 复用状态：partial；类型：model_weight
- `pretrained/multi_hgnn.pth`
  - 能力：multi_flavor 预训练权重
  - 用途：面向 multi_flavor 任务的 HGNN 权重；同目录还有 multi_afp、multi_gsage、multi_wln
  - 复用状态：partial；类型：model_weight

### datasets

- `dataset/public_dataset/classification/BACE.csv`
  - 能力：公开分类基准数据
  - 用途：用于分类任务的公开基准集合；同目录还包含 BBBP2、ClinTox2、N6512
  - 复用状态：partial；类型：unknown
- `dataset/public_dataset/regression/FreeSolv.csv`
  - 能力：公开回归基准数据
  - 用途：用于回归任务的公开基准集合；同目录还包含 Lipop、PDBbind、delaney
  - 复用状态：partial；类型：unknown
- `dataset/taste_dataset/bitter_nonbitter/bn_train.csv`
  - 能力：bitterness/ non-bitter 划分数据
  - 用途：用于二分类 taste 任务的训练/测试划分；对应 bn_test.csv
  - 复用状态：partial；类型：unknown
- `dataset/taste_dataset/multi_flavor/Bitter.csv`
  - 能力：多味型标签数据
  - 用途：用于多标签/多类别 taste 任务；同目录含 Astringent、Kokumi、Salt、Sour、Sweet、Tasteless、Umami
  - 复用状态：partial；类型：unknown
- `dataset/taste_dataset/qikprop.CSV`
  - 能力：分子描述符表
  - 用途：提供 QikProp 描述符/特征表，可能用于特征构建或对照实验
  - 复用状态：partial；类型：unknown

### evaluation

- `compare_gnns.ipynb`
  - 能力：GNN 对比评估笔记本
  - 用途：比较 BitterGNN 与其他 GNN 变体的实验结果
  - 复用状态：partial；类型：unknown
- `compare_taste_predictors.ipynb`
  - 能力：taste predictor 对比评估笔记本
  - 用途：比较不同 taste predictor/baseline 的表现
  - 复用状态：partial；类型：unknown
- `analysis.ipynb`
  - 能力：分析与讨论笔记本
  - 用途：保存实验分析与结果解读；同类还有 discussion.ipynb
  - 复用状态：partial；类型：unknown

### inference

- `predictor.py`
  - 能力：主推理入口
  - 用途：加载模型并对输入分子/样本生成预测结果
  - 复用状态：partial；类型：code_entry
- `contrast_predictors/VirtualTasteAPI.py`
  - 能力：VirtualTaste 推理接口
  - 用途：为对照预测器提供 API 级调用封装
  - 复用状态：partial；类型：code_entry
- `contrast_predictors/VirtuousSweetBitter.py`
  - 能力：味觉基线推理脚本
  - 用途：运行另一组 taste baseline 并导出结果
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `hgnn/model.py`
  - 能力：核心 BitterGNN 模型结构
  - 用途：定义主图神经网络的前向与层级结构，用于 bitterness/taste 预测
  - 复用状态：ready_for_review；类型：code_entry
- `hgnn/load_data.py`
  - 能力：图特征与数据加载辅助
  - 用途：加载图输入并衔接训练/推理所需的数据组织
  - 复用状态：partial；类型：code_entry
- `contrast_gnns/GraphSAGE.py`
  - 能力：对照 GNN backbones
  - 用途：提供 GraphSAGE 对照实现；同目录还包含 GraphTransformers.py、GraphVAE.py、WLN.py
  - 复用状态：ready_for_review；类型：code_entry
- `contrast_predictors/BitterPredict.py`
  - 能力：味觉基线预测器
  - 用途：提供非 GNN 的 taste/bitterness baseline；同目录还有 CNN、MLP、VirtualTaste、VirtuousSweetBitter 等
  - 复用状态：ready_for_review；类型：code_entry
- `predictor.py`
  - 能力：统一推理包装
  - 用途：对外封装预测调用入口，便于加载模型与生成结果
  - 复用状态：partial；类型：code_entry

### training

- `hgnn/trainers.py`
  - 能力：训练循环与优化器编排
  - 用途：承载模型训练、参数更新与批处理逻辑
  - 复用状态：partial；类型：code_entry
- `hgnn/early_stop.py`
  - 能力：early stopping
  - 用途：训练过程中的提前停止辅助
  - 复用状态：ready_for_review；类型：code_entry
- `hgnn/utils.py`
  - 能力：训练通用工具
  - 用途：提供训练/评测过程中共用的辅助函数
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态盘点，未执行代码、未安装依赖、未运行测试。
- 未见独立 training_entrypoint 或 config_recipe，训练流程只能从模块/笔记本名称推断。
- 数据集与预训练权重的来源和授权未在冻结清单中单独确认。
- 静态存在不等于可直接复现；.pth 与 notebook 仅能说明资产存在。

## 仍未知

- bn/bs/multi 预训练权重是否对应论文最终报告的具体实验设置，无法仅凭路径确认。
- dataset/public_dataset 与 dataset/taste_dataset 是否为原始、清洗后或二次整理版本，来源不明。
- compare_* 笔记本是否覆盖全部论文表格与指标，无法从静态清单确认。
- predictor.py 与各 baseline 脚本的实际参数、输入格式和输出协议未验证。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
