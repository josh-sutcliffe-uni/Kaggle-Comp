# Cat and Dog Facial Feature Classification (Kaggle)

Coursework for the ENGE 707 Kaggle competition: classify close-up crops of cat and dog faces into 8 classes (eye, face, mouth and nose for each animal). Kaggle username: joshsutcliffe1.

## Results
| Model | Validation accuracy | Kaggle public score |
|---|---|---|
| Baseline CNN (from scratch, 64 px, laptop CPU) | 95.47% | 0.9338 |
| ResNet-18, run 6 (pretrained, 128 px, Kaggle GPU) - final model | 99.36% | 0.9747 |

## Files
| Path | What it is |
|---|---|
| `kaggle_comp.ipynb` | Main notebook, Tasks 1-6: data exploration, preprocessing, models, training analysis, evaluation and results analysis. Runs on the laptop CPU. |
| `kaggle_notebooks/` | The ResNet-18 runs trained on a Kaggle GPU, with their results. See `kaggle_notebooks/Description.md`. |
| `results/` | Tables saved by the notebooks: per-image information and information from Task 1 (`images_info.csv`, `image_sharpness.csv`, saved so the images are only scanned once), training histories, predictions and metrics. |
| `figures/` | Figures saved by the notebook. |
| `submissions/` | Main submission files uploaded to Kaggle. |
| `evidence/` | Screenshots of the Kaggle submissions and leaderboard. |
| `models/` | Only the two weight files the notebook loads: `baseline_cnn_best.pt` and `resnet18_final_best.pt`. |

Not in git: the other weight files (too large), `splits/` (rebuilt from the fixed seed), and the competition data.

## How to run
1. Use Python 3.12 with PyTorch 2.2.2, torchvision 0.17.2, pandas, NumPy, Matplotlib, Pillow and scikit-learn.
2. Put the competition data folder `enge-707-2026-s-2-cat-and-dog-facial-feature-classification-ch` next to this folder.
3. Open `kaggle_comp.ipynb` and run all cells. With every switch set to `False` (`RESCAN_IMAGES`, `REMAKE_SPLIT`, `RETRAIN_BASELINE`, `REPREDICT`, `REPREDICT_TTA`), saved results are loaded instead of recomputed, and Run All takes about 5-15 minutes on a laptop.

Run All needs the weight files `models/baseline_cnn_best.pt` and `models/resnet18_final_best.pt` (sections 3.7 and 4.6 load them). `resnet18_final_best.pt` is run 6's `models/resnet18_best.pt` from Kaggle.
