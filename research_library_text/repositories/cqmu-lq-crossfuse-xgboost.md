# cqmu-lq/CrossFuse-XGBoost

- **仓库：** [https://github.com/cqmu-lq/CrossFuse-XGBoost](https://github.com/cqmu-lq/CrossFuse-XGBoost)
- **固定 commit：** `7b7b04a223c8336317545b1bb150d4498a950668`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 18

## 仓库摘要

仓库以notebook、CSV数据和若干pkl序列化产物为主，像是论文配套实验与模型工件集合；未见LICENSE，静态审核无法确认训练、推理与检查点内容的真实可复用边界。

## 可复用模块与资源

### checkpoints

- `src/data/xgboostc_parameters.pkl`
  - 能力：XGBoost classification parameters
  - 用途：序列化分类模型参数/状态，可能用于加载推理。
  - 复用状态：unknown；类型：unknown
- `src/data/xgboostr_parameters.pkl`
  - 能力：XGBoost regression parameters
  - 用途：序列化回归模型参数/状态，可能用于加载推理。
  - 复用状态：unknown；类型：unknown
- `src/data/lightfm_dosage.pkl`
  - 能力：LightFM serialized artifact
  - 用途：LightFM 相关序列化对象，可能为推荐模型或参数。
  - 复用状态：unknown；类型：unknown
- `src/data/lightfm_example.pkl`
  - 能力：LightFM serialized artifact
  - 用途：LightFM 相关示例序列化对象，可能为模型或中间状态。
  - 复用状态：unknown；类型：unknown

### datasets

- `src/data/surprise_train.csv`
  - 能力：training set
  - 用途：CSV 训练数据。
  - 复用状态：blocked；类型：unknown
- `src/data/surprise_test.csv`
  - 能力：test set
  - 用途：CSV 测试数据。
  - 复用状态：blocked；类型：unknown
- `src/data/training_set.pkl`
  - 能力：training / intermediate table
  - 用途：序列化训练集或中间数据表。
  - 复用状态：unknown；类型：unknown
- `src/data/external_validation_set.pkl`
  - 能力：external validation table
  - 用途：外部验证集序列化对象。
  - 复用状态：unknown；类型：unknown
- `src/data/y_class.pkl`
  - 能力：label / target arrays
  - 用途：分类目标。
  - 复用状态：unknown；类型：unknown
- `src/data/y_regress.pkl`
  - 能力：label / target arrays
  - 用途：回归目标。
  - 复用状态：unknown；类型：unknown

### evaluation

- `src/code/ADMETlab_autosub.ipynb`
  - 能力：ADMETlab automation notebook
  - 用途：自动化提交/整理 ADMETlab 相关结果，疑似评估或结果汇总流程。
  - 复用状态：blocked；类型：unknown
- `src/code/ADMETlab_output/admet2_res_file.csv`
  - 能力：evaluation output table
  - 用途：评估结果 CSV。
  - 复用状态：blocked；类型：unknown
- `src/code/ADMETlab_output/admet2_res_file.html`
  - 能力：evaluation report HTML
  - 用途：评估结果 HTML 报告。
  - 复用状态：blocked；类型：unknown
- `src/code/ADMETlab_output/admet2_index.html`
  - 能力：evaluation index HTML
  - 用途：评估报告索引页。
  - 复用状态：blocked；类型：unknown

### inference

- `src/code/recommendation_task.ipynb`
  - 能力：recommendation / inference notebook
  - 用途：推理或推荐任务；按文件名推断为加载已保存模型后做预测。
  - 复用状态：blocked；类型：unknown

### reusable_assets

- `src/code/ml_methods.py`
  - 能力：Python helper functions / feature engineering helper
  - 用途：可能承载特征处理、模型辅助或交叉验证相关通用函数；按文件名判断为核心辅助代码。
  - 复用状态：blocked；类型：code_entry
- `src/requirements.txt`
  - 能力：runtime dependency manifest
  - 用途：记录 Python 依赖，便于重建运行环境。
  - 复用状态：blocked；类型：unknown

### training

- `src/code/crossfuse_xgboost.ipynb`
  - 能力：training notebook
  - 用途：主训练/筛选流程，名称指向 CrossFuse-XGBoost。
  - 复用状态：blocked；类型：unknown

## 使用限制

- 仅静态清单审计，未执行代码、未安装依赖、未运行测试。
- 未读取 notebook 内部内容，训练/推理/评估角色主要依据文件名与路径。
- 若干 .pkl 文件可能是模型参数、特征表或中间数据，静态清单无法准确区分。
- 仓库未发现 LICENSE，代码、数据和模型工件的再利用边界未厘清。
- CSV/HTML 输出是否对应论文最终实验结果，无法由静态信息确认。

## 仍未知

- 是否存在未跟踪的下载脚本、外部数据拉取或隐藏配置，静态清单无法判断。
- xgboostc_parameters.pkl、xgboostr_parameters.pkl、lightfm_dosage.pkl、lightfm_example.pkl 是否为真实 checkpoint 而非普通序列化对象，未验证。
- training_set.pkl、external_validation_set.pkl、y_class.pkl、y_regress.pkl 的生成来源与许可未确认。
- ADMETlab_output 下的 HTML/CSV 是否为最终论文结果或仅为示例输出，未确认。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
