# SpecSwin3D

SpecSwin3D is a deep learning framework for hyperspectral image (HSI) band reconstruction, spectral modeling, and band importance analysis. The project focuses on reconstructing full hyperspectral signatures from sparse spectral observations, with applications in remote sensing and Earth observation.

This repository contains the original SpecSwin3D implementation (v1) used for early experiments on band selection, reconstruction, and visualization.
The updated and extended model (SpecSwin3D v2) is provided separately as a packaged release.

==================================================
SpecSwin3D v2
==================================================

IMPORTANT NOTICE
The latest version of the model is provided in:

SpecSwin3D_v2.zip

SpecSwin3D v2 introduces significant upgrades in model design, training strategy, and evaluation methodology, with a focus on physically informed spectral modeling and improved reconstruction accuracy.

--------------------------------------------------
What’s New in SpecSwin3D v2
--------------------------------------------------

1. Unified Spectral Regularization Framework

A physically informed spectral regularization objective is introduced during training, combining multiple complementary constraints:

- Anchor Consistency Constraint
  Enforces consistency between reconstructed hyperspectral outputs and observed multispectral bands through sensor spectral response function (SRF) projection.

- PCA Manifold Constraint
  Constrains reconstructed spectra to lie within a low-dimensional spectral subspace learned from training data, improving physical plausibility and robustness.

- Spectral Angle Mapper (SAM) Loss
  Penalizes angular deviation between reconstructed and reference spectra, emphasizing spectral shape preservation.

- Spectral Smoothness Regularization
  Encourages smooth spectral transitions along the wavelength dimension, suppressing non-physical oscillations.

All constraints are modular and can be enabled or disabled independently.

--------------------------------------------------
2. Spectral Positional Embedding (SPE)
--------------------------------------------------

SpecSwin3D v2 introduces Spectral Positional Embedding (SPE) to explicitly encode band-wise spectral ordering within transformer attention blocks.

- Supports learned and continuous (wavelength-based) spectral embeddings
- Enhances long-range spectral dependency modeling
- Improves discrimination across spectrally distant bands

--------------------------------------------------
3. Cascade Curriculum Training Strategy
--------------------------------------------------

A multi-stage cascade curriculum is adopted to progressively increase spectral reconstruction difficulty:

- Early stages emphasize easier or anchor spectral bands
- Later stages expand toward full-spectrum reconstruction
- Improves training stability and convergence behavior

A no-cascade baseline is also supported for direct comparison.

--------------------------------------------------
4. Extended Evaluation and Analysis
--------------------------------------------------

SpecSwin3D v2 expands the evaluation protocol with:

- Full-spectrum band-wise reconstruction metrics
- Confidence interval estimation for reconstruction accuracy
- Error analysis with respect to spectral distance
- Attention map visualization for spectral interpretability

==================================================
Original SpecSwin3D (v1) Repository Structure
==================================================

SpecSwin3D/
├── data_preprocessing/
│   ├── input-label.py
│   ├── restack_bands_to_16.py
│   └── restack_bands_to_16_repeated.py
├── evaluation/
│   ├── band_metrics_summary.py
│   ├── comprehensive_band_model_evaluation.py
│   └── evaluate_models.py
├── strategies/
│   ├── correlation_strategy.txt
│   ├── mutual_info_strategy.txt
│   ├── spectral_physics_strategy.txt
│   └── variance_strategy.txt
├── train/
│   ├── calculate_band_importance.py
│   ├── denormalize_utils.py
│   ├── fine_tune_all_strategies_219_bands.py
│   └── train_SpecSwin3D_16.py
├── visualize/
│   ├── analyze_checkpoints_structure.py
│   └── visualize_model_output.py

==================================================
Data
==================================================

The raw hyperspectral dataset used in this project is from the AVIRIS mission:
https://aviris.jpl.nasa.gov/

The processed dataset used for training and evaluation is not publicly available.
For access, please contact the author:

Tang Sui
Email: tsui5@wisc.edu
