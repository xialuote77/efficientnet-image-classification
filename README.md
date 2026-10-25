# Image Classification with EfficientNet Features and Ensembles

## 中文概览

**项目定位：机器学习 / 图像分类 / 迁移特征与模型集成。** 在动物类别和细粒度鸟类识别任务中，比较手工特征与预训练 EfficientNet 特征，并评估 SVM、逻辑回归和加权投票方案。

- **个人贡献**：负责集成方案设计、模型调试与性能优化，并承担报告的主要撰写工作；完整项目为团队成果，其他模块不表述为本人独立开发。
- **技术栈**：Python、PyTorch/torchvision、scikit-learn、EfficientNet-B4/B2、SVM、ensemble、误差分析。
- **结果口径**：任务 1 的 EfficientNet-B4 + RBF SVM 五折 CV 均值为 **92.59%**；任务 2 的加权 ensemble 在误差分析留出集上为 **90.5%**。两者不是同一测试口径，不能混称独立测试准确率。
- **实现范围**：EfficientNet 用作冻结特征提取器，不表述为从零训练或端到端微调；留出集存在模型选择依赖，完整训练本轮未重跑。整理版已修复图片读取与汇总表口径问题。

## English documentation

Compare handcrafted image features with pretrained **EfficientNet-B4/B2 embeddings**, classical classifiers and weighted soft voting on animal and fine-grained bird classification tasks.

## My contribution

I designed the ensemble approach, debugged and optimised models to improve classification accuracy, and was a principal report writer. This was a team project; the full workflow is retained as context, not claimed as entirely my individual implementation.

## Reported evaluation

| Experiment | Evaluation | Accuracy |
| --- | --- | ---: |
| Task 1: handcrafted features + linear SVM | Validation split | 55.6% |
| Task 1: EfficientNet-B4 + RBF SVM | 5-fold CV mean | 92.59% |
| Task 2: handcrafted features + linear SVM | Validation split | 30.5% |
| Task 2: EfficientNet-B2 + linear SVM | 5-fold CV mean | 93.05% |
| Task 2: weighted ensemble | Held-out split used for error analysis | 90.5% |

These are different evaluation protocols, not a single test leaderboard. No independent test accuracy is claimed. The original summary code used a weighted average of constituent CV means, which is **not measured ensemble CV accuracy**. The portfolio notebook corrects this summary to the observed error-analysis holdout result, with its selection-dependence caveat. The error-analysis holdout may overlap observations used for model/weight selection, so it is not an untouched final test.

The original comparison figure (under assets/) and [full team report](reports/image-classification-report.pdf) are original coursework artefacts; their combined CV/validation labels need the distinctions above. See `docs/REVIEW.md` before public release.

## Run and data

Install `requirements.txt` in a dedicated environment and start Jupyter from the repository root. Open `notebooks/image_classification.ipynb`. Place the original `task1_data/` and `task2_data/` beside `notebooks/`, then check the path configuration cell. Dataset metadata, feature tables and images are not bundled. Obtain them through the original authorised course/data source; raw images and trained weights are not redistributed.

The dependencies are unpinned and this environment is not fully rerun/verified. Pretrained weights may download on first run. The notebook uses EfficientNet as a frozen feature extractor; this repository does not claim end-to-end backbone fine-tuning.

Originally COMP30027 Project 2, University of Melbourne. See `docs/CONTRIBUTIONS.md` for individual scope. No new licence is assigned.
