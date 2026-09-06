# andreimargeloiu/TabEBM

- **仓库：** [https://github.com/andreimargeloiu/TabEBM](https://github.com/andreimargeloiu/TabEBM)
- **固定 commit：** `72eb78dab896c7a8f39c4dcc288c834fd72eff2b`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **资产记录数：** 8

## 仓库摘要

该仓库是 TabEBM 的静态代码发布，已识别到核心实现、3 个教程 notebook、安装/依赖文件与 Apache-2.0 许可证；未发现 bundled data、训练/推理/评测入口或 checkpoint，因此只能确认静态资产与许可边界，不能证明执行或复现。

## 可复用模块与资源

### reusable_assets

- `src/tabebm/TabEBM.py`
  - 能力：核心实现
  - 用途：TabEBM 的主要算法/模型实现参考
  - 复用状态：ready_for_review；类型：code_entry
- `src/tabebm/__init__.py`
  - 能力：包初始化
  - 用途：Python 包导入与命名空间组织参考
  - 复用状态：ready_for_review；类型：code_entry
- `tutorials/tutorial1_generate_data.ipynb`
  - 能力：教程示例
  - 用途：生成数据流程的交互式示例
  - 复用状态：ready_for_review；类型：unknown
- `tutorials/tutorial2_augment_real_world_data.ipynb`
  - 能力：教程示例
  - 用途：真实数据增强流程的交互式示例
  - 复用状态：ready_for_review；类型：unknown
- `tutorials/tutorial3_approximated_density.ipynb`
  - 能力：教程示例
  - 用途：近似密度相关流程的交互式示例
  - 复用状态：ready_for_review；类型：unknown
- `setup.py`
  - 能力：环境/打包配置
  - 用途：Python 打包与安装配置参考
  - 复用状态：ready_for_review；类型：code_entry
- `requirements.txt`
  - 能力：依赖清单
  - 用途：运行环境依赖声明参考
  - 复用状态：ready_for_review；类型：unknown
- `requirements_paper.txt`
  - 能力：论文环境依赖清单
  - 用途：论文复现实验的依赖声明参考
  - 复用状态：ready_for_review；类型：unknown

## 使用限制

- 仅做静态清单审查，未运行仓库代码，未安装依赖，未执行测试。
- 冻结清单未发现 bundled data、checkpoint、训练入口、推理入口或评测入口。
- Notebook 仅作为路径级证据，正文未解析，不能据此证明其中实际执行流程。
- requirements 中的第三方依赖各自许可证未在本次清单中单独核验。

## 仍未知

- `tutorials/` 内 notebook 是否包含可执行训练、评测或下载数据逻辑，当前仅有路径级证据。
- 外部数据集来源、下载方式与版本未出现在冻结资产中。
- `requirements.txt`/`requirements_paper.txt` 所列依赖的具体许可证与兼容性未知。
- 代码运行结果、模型性能与复现性均未知。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
