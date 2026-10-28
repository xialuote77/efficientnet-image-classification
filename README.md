# Image Classification with EfficientNet Features and Ensembles

## 中文概览

### 基于 EfficientNet 特征与模型集成的图像分类

面向动物类别和细粒度鸟类识别，比较手工特征与预训练 EfficientNet 特征，结合 SVM、逻辑回归和加权投票完成分类。

- **个人工作**：负责集成方案设计、模型调试与性能优化，并承担报告的主要撰写工作。项目由团队协作完成。
- **主要方法**：使用冻结的 EfficientNet-B4/B2 提取图像特征，比较分类器和集成方案，并进行交叉验证及误差分析。
- **实验结果**：动物分类中，EfficientNet-B4 + RBF SVM 的五折交叉验证平均准确率为 **92.59%**；鸟类分类中，加权集成模型在误差分析留出集上的准确率为 **90.5%**。

两项结果采用不同评估方式。鸟类留出集存在模型选择依赖，因此其结果需结合下方的评估说明理解。仓库提供代码和团队报告，完整训练未在本次整理中重跑。

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
