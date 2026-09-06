# fppgroup/thplm

- **仓库：** [https://github.com/fppgroup/thplm](https://github.com/fppgroup/thplm)
- **固定 commit：** `250249a4108435cb82bac09ef53011dbcd2c535b`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 16

## 仓库摘要

仓库是 THPLM 的静态发布包：含推断脚本、ESM 特征提取辅助、S2648 交叉验证切分、多个测试集/特征张量与权重文件；代码为 MIT，但数据与模型的单独许可边界未能从静态库存确认。

## 可复用模块与资源

### checkpoints

- `Model/THPLM.pt`
  - 能力：checkpoint
  - 用途：主模型权重文件。
  - 复用状态：partial；类型：model_weight
- `Model/THPLM_rmS350.pt`
  - 能力：checkpoint
  - 用途：变体模型权重文件。
  - 复用状态：partial；类型：model_weight
- `Model/FoldModels/Fold0_cross_CNN.pth`
  - 能力：checkpoint
  - 用途：5 折交叉验证中的单折模型权重；同目录还有 Fold1-Fold4。
  - 复用状态：partial；类型：model_weight
- `Model/Model_1426_rmhomoSsym.pth`
  - 能力：checkpoint
  - 用途：额外保存的模型权重文件。
  - 复用状态：partial；类型：model_weight

### datasets

- `Datasets/Datasets/S2648Cleaned/S2648.csv_cross_valid_clean0.train.csv`
  - 能力：training
  - 用途：S2648 5-fold CV 的训练切分示例；与对应 .fea.npy 特征一同构成训练输入。
  - 复用状态：partial；类型：unknown
- `Datasets/Datasets/S2648Cleaned/S2648.csv_cross_valid_clean0.test.csv`
  - 能力：evaluation
  - 用途：S2648 5-fold CV 的测试切分；用于评估而非训练。
  - 复用状态：partial；类型：unknown
- `Datasets/Datasets/S669_forward.csv`
  - 能力：evaluation
  - 用途：独立 benchmark 测试集/外部验证集之一。
  - 复用状态：partial；类型：unknown
- `Datasets/DataFromCleaned/TestwithFea/global_muta_embedding.npy`
  - 能力：dataset bundle
  - 用途：测试侧特征/嵌入张量与标签 bundle。
  - 复用状态：partial；类型：unknown
- `Datasets/Datasets/OK_Sym_S2648_overlaps.csv`
  - 能力：dataset filtering
  - 用途：重叠检查/去泄漏过滤与样本清理。
  - 复用状态：partial；类型：unknown

### evaluation

- `Datasets/DataFromCleaned/TestwithFea/site_glo_embed_36_sym194_label.npy`
  - 能力：evaluation
  - 用途：测试标签张量，可支撑静态评估输入。
  - 复用状态：partial；类型：unknown
- `Datasets/Datasets/S2648Cleaned/S2648.csv_cross_valid_clean0.test.csv`
  - 能力：evaluation
  - 用途：交叉验证评估切分。
  - 复用状态：partial；类型：unknown

### inference

- `THPLM_predict.py`
  - 能力：inference
  - 用途：本仓库的主要推断脚本。
  - 复用状态：ready_for_review；类型：code_entry
- `examples/wild.fasta`
  - 能力：inference
  - 用途：wild-type 示例输入。
  - 复用状态：partial；类型：unknown

### reusable_assets

- `THPLM_predict.py`
  - 能力：inference
  - 用途：推断入口；用于加载 THPLM 相关权重并对点突变样本做 stability change prediction。
  - 复用状态：ready_for_review；类型：code_entry
- `esmscripts/extract.py`
  - 能力：inference
  - 用途：ESM 表征/embedding 提取辅助脚本，支撑上游特征生成。
  - 复用状态：partial；类型：code_entry

### training

- `Datasets/Datasets/S2648Cleaned/S2648.csv_cross_valid_clean0.train.csv`
  - 能力：training
  - 用途：训练样本切分；仓库未见训练入口，只能静态确认训练数据准备件存在。
  - 复用状态：partial；类型：unknown

## 使用限制

- 仅做静态清点；未运行代码、未安装依赖、未验证权重可加载。
- 未见训练主入口或配置 рецепी/recipe，训练复现只能依赖现有数据与权重痕迹。
- 数据与模型文件的来源、再分发许可和作者自训练事实都未被静态库存证明。
- examples/esm3Bout/*.pt 的生成来源与语义不明，可能只是示例输出而非可复用权重。

## 仍未知

- THPLM.pt、THPLM_rmS350.pt 和 FoldModels 是否由仓库作者训练或仅为转存。
- S2648、S669、Ssym、Frataxin、OK_S2298 等数据是否为原始数据、清洗后再打包，还是第三方基准的派生物。
- THPLM_predict.py 是否是唯一推断入口，还是还依赖未枚举的隐藏脚本/参数。
- 评估指标、阈值和具体实验结果未在静态库存中得到证实。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
