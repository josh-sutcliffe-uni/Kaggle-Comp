# Kaggle Notebooks
The notebooks in this folder were run on Kaggle using its free Tesla T4 GPU instead of my laptop's CPU. On the CPU one ResNet-18 epoch at 128 px takes more than an hour; on the GPU it takes about one minute.

`kaggle_resnet18_baseline_notebook.ipynb` is the notebook every run was based on. It uses the same split, dataset classes, transforms and training functions as `kaggle_comp.ipynb`, so a change to those functions has to be made in both notebooks. Each run is a copy of it with one setting changed from run 1.

| Run | Notebook | Results folder | Setting changed from run 1 | Best validation accuracy | Kaggle public score |
|---|---|---|---|---|---|
| 1 | `resnet-18_notebook_run1_128px.ipynb` | `resnet-18_results_run1_128px-imgsize/` | none (128 px, 3 frozen + 7 fine-tuning epochs) | 99.21% | 0.9728 |
| 3 | `resnet-18_notebook_run3_224px-imgsize.ipynb` | `resnet-18_results_run3_224px-imgsize/` | image size 224 px | 98.74% | 0.9687 |
| 4 | `resnet-18_notebook_run4_96px-imgsize.ipynb` | `resnet-18_results_run4_96px-imgsize/` | image size 96 px | 99.01% | 0.9676 |
| 5 | `resnet-18_notebook_run5_64px-imgsize.ipynb` | `resnet-18_results_run5_64px-imgsize/` | image size 64 px | 98.92% | 0.9698 |
| 6 | `resnet-18_notebook_run6_128px_20epochs.ipynb` | `resnet-18_results_run6_128px-imgsize_20epochs/` | 17 fine-tuning epochs (20 in total); **final model** | 99.36% | 0.9747 |
| 8 | `resnet-18_notebook_run8_128px-noaug.ipynb` | `resnet-18_results_run8_128px-noaug/` | no augmentation | 99.29% | 0.9696 |

There are no runs 2 and 7: both were mis-runs (run 7 was a first attempt at the no-augmentation run that was not saved), so they were not used or submitted.

Each results folder holds what the run saved on Kaggle:
- `figures/`: the training history (`resnet18_history.csv`, `resnet-18_history.csv` in run 8) and the learning-curve figure.
- `submissions/`: the submission file uploaded to Kaggle.
- `models/`: the saved weights (`.pt`). These are large, so they are not in git.
- `__results___files/`: the images from the notebook's output.

`../kaggle_comp.ipynb` does not train ResNet-18 itself. It reads each run's history from copies in `../results/` (for example `resnet18_run4_96px_history.csv`), and the final model's weights from `../models/resnet18_final_best.pt`, a copy of run 6's `models/resnet18_best.pt`.
