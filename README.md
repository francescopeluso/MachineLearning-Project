# Solar Filament Segmentation

Machine Learning project work, A.Y. 2025/26, MSc in Computer Engineering, DIEM,
University of Salerno.

**Author:** Francesco Peluso
**Team:** `2026_MLrec_gr02`
**Competition:** [filament-segmentation-2026](https://www.kaggle.com/competitions/filament-segmentation-2026)

Solar filaments are ribbons of cooler plasma suspended over the solar disk, visible
as dark elongated structures in H-alpha images. Given a 2048x2048 observation, the
task is to predict which pixels belong to a filament, split the mask into one
connected component per filament, and submit each component as COCO run-length
encoding.

The model is a U-Net with an ImageNet-pretrained ResNet18 encoder. Threshold and
post-processing are searched jointly on validation, at native resolution, against
the competition's own metric. The full report is in `docs/`, the experiment ledger
in `experiments/README.md`.

The project brief sets a GPU memory budget: at most 5 GB of VRAM in training and
4 GB at inference. Both notebooks measure the actual peak at runtime and report it
in the experiment metrics.

## Running it

```bash
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
jupyter lab notebooks/01_training.ipynb
```

Place the competition data under `dataset/` as `dataset/train/train_images/`,
`dataset/train/MAGFiLO_1.0_Annotations_kaggle2026_train.json` and
`dataset/test/test_images/`. The notebooks locate the project root on their own and
are self-contained: nothing to install beyond `requirements.txt`, and they run in
Colab, Kaggle or locally.

Edit only the **configuration cell** of `01_training.ipynb`, then run it top to
bottom. It writes everything under `experiments/<ID>/`, including
`metrics/submission_recipe.json`, which `02_inference.ipynb` reads to produce
`submission.csv`.

## Scoring

Validation is scored with the competition's own Panoptic Quality, re-implemented
from the organisers' self-evaluation notebook and verified against it, so local
numbers are directly comparable with the leaderboard. Dice is tracked alongside it:
the two disagree in an informative way, since a fragmented or noisy mask barely
moves Dice and destroys PQ.
