# BioEc142-Ani-Final-Project
# ANI HD-NNP for Small Organic Molecules

Final project for BioE C142/242 (Spring 2026).

This project implements and trains an ANI-style high-dimensional neural
network potential on the GDB s01–s04 subset of the ANI-1 dataset
(organic molecules with 1–4 heavy atoms drawn from H, C, N, O).

## Result

Final test MAE: **0.30 kcal/mol** (mean of two production trials)
— well below the 1 kcal/mol chemical-accuracy threshold.

## Architecture

- 384-element AEV input (radial cutoff 5.2 Å, angular cutoff 3.5 Å)
- Per-atom NNP: 384 → 128 → 128 → 64 → 1 with ReLU activations
- One independent network per element type (H, C, N, O)
- Total parameters: ~1.18 M

## Training

- Optimizer: Adam, lr = 1×10⁻⁴
- Loss: MSE on energy in Hartree
- Batch size: 512
- L2 regularization: none (model was not overfitting)
- 240 epochs on 90% of train+val data

## Files

- `ANI_Final_Project_complete.ipynb` — final notebook including all trials and final model

## Dataset

The ANI-1 GDB s01–s04 dataset is not included in this repo (too large
for GitHub). It can be downloaded from the bCourses page for the class.

## References

1. Behler, J.; Parrinello, M. *Phys. Rev. Lett.* **2007**, 98, 146401.
2. Smith, J. S.; Isayev, O.; Roitberg, A. E. *Chem. Sci.* **2017**, 8, 3192–3203.
