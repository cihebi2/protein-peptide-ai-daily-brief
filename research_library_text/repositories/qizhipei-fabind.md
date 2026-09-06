# qizhipei/fabind

- **仓库：** [https://github.com/qizhipei/fabind](https://github.com/qizhipei/fabind)
- **固定 commit：** `0698bd4f39f74169aaefc5b9350d6968a8076065`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 0

## 仓库摘要

该仓库静态上是 FABind/FABind+ 的蛋白-配体对接实现，含模型、训练、推理和评估代码；仅见示例数据与占位 ckpt 目录，未见可核验权重文件。

## 可复用模块与资源

- 未发现可公开描述的结构化资产。
## 使用限制

- 仅做静态清点，未执行仓库代码、测试或训练。
- dependencies 未安装，submodules 未初始化；`.gitmodules` 存在但外部内容未核验。
- 未见可核验的具体 checkpoint 文件；`ckpt` 仅作为目录/引用迹象出现。
- 示例数据与 split 文件的来源和单独许可未明，不能按 MIT 自动外推。
- large_blobs_over_5MiB_may_be_promisor_only，且 LFS smudge 被禁用。

## 仍未知

- `FABind/ckpt` 与 `FABind_plus/ckpt` 内是否存在被冻结清单漏列的权重文件。
- 示例 PDB/SDF/MOL2 是否来自外部数据库或论文自建数据集，以及对应许可。
- `generate_esm2_t33.py` 是否依赖外部 ESM2 权重或额外下载项。
- 训练/验证/测试原始数据是否完全未随仓库冻结，还是仅未出现在 tracked inventory 中。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
