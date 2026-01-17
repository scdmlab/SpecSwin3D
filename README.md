# SpecSwin3D

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Python](https://img.shields.io/badge/python-3.8%2B-blue.svg)
![Deep Learning](https://img.shields.io/badge/framework-pytorch-red.svg)

A state-of-the-art deep learning framework for hyperspectral image (HSI) band reconstruction, spectral modeling, and band importance analysis.

## Overview

SpecSwin3D focuses on reconstructing full hyperspectral signatures from sparse spectral observations, with applications in remote sensing and Earth observation. This repository provides advanced deep learning solutions for hyperspectral data processing and analysis.

## Repository Structure

This repository contains two versions of the SpecSwin3D framework:

| Version | Description | Status |
|---------|-------------|--------|
| **SpecSwin3D v1** | Original implementation for early experiments | Legacy (this repository) |
| **SpecSwin3D v2** | Enhanced model with advanced features | Available in `SpecSwin3D_v2.zip` |

## Key Features

### Core Capabilities
- **Hyperspectral Band Reconstruction**: Reconstruct full spectral signatures from sparse observations
- **Spectral Modeling**: Advanced deep learning models for spectral analysis
- **Band Importance Analysis**: Identify and analyze critical spectral bands
- **Remote Sensing Applications**: Optimized for Earth observation tasks

### SpecSwin3D v2 Enhancements

#### Advanced Regularization Framework
- **Anchor Consistency Constraints**: Enforce agreement between reconstructed hyperspectral outputs and observed multispectral bands via sensor spectral response function (SRF) projection
- **PCA Manifold Constraints**: Restrict reconstructed spectra to low-dimensional spectral subspace for improved physical plausibility
- **Spectral Angle Mapper (SAM) Loss**: Preserve spectral shape by penalizing angular deviations
- **Spectral Smoothness Regularization**: Suppress non-physical oscillations and encourage smooth wavelength transitions
- **Modular Design**: All constraints can be independently enabled or disabled

#### Spectral Positional Embedding (SPE)
- Explicit encoding of band-wise spectral ordering within transformer attention blocks
- Support for both learned embeddings and continuous wavelength-based embeddings
- Enhanced long-range spectral dependency modeling
- Improved discrimination across spectrally distant bands

#### Training Strategy
- **Cascade Curriculum Learning**: Progressive increase in spectral reconstruction difficulty
  - Early stages focus on anchor spectral bands
  - Later stages expand to full-spectrum reconstruction
  - Improved training stability and convergence
- **No-cascade Baseline**: Direct comparison option available

#### Enhanced Evaluation Protocol
- Full-spectrum band-wise reconstruction metrics
- Confidence interval estimation for reconstruction accuracy
- Error analysis with respect to spectral distance
- Attention map visualization for spectral interpretability

## Dataset Information

### Data Source
- **Primary Dataset**: AVIRIS (Airborne Visible/Infrared Imaging Spectrometer)
- **Mission Website**: [https://aviris.jpl.nasa.gov/](https://aviris.jpl.nasa.gov/)

### Data Access
The processed dataset used for training and evaluation is not publicly available. For data access requests, please contact:

**Tang Sui**  
Email: [tsui5@wisc.edu](mailto:tsui5@wisc.edu)

## Applications

- Remote sensing and Earth observation
- Hyperspectral image analysis
- Spectral reconstruction and enhancement
- Band selection optimization
- Environmental monitoring
- Agricultural monitoring
- Mineral exploration

## Getting Started

### Prerequisites
- Python 3.8+
- PyTorch
- CUDA-compatible GPU (recommended)

### Installation
```bash
# Clone the repository
git clone https://github.com/yourusername/SpecSwin3D.git
cd SpecSwin3D

# Install dependencies
pip install -r requirements.txt
```

### Quick Start
```python
# Basic usage example
from specswin3d import SpecSwin3D

# Initialize model
model = SpecSwin3D(config='default')

# Load and process hyperspectral data
# ... (additional examples to be added)
```

## Citation

If you use SpecSwin3D in your research, please cite:

```bibtex
@article{specswin3d2024,
  title={SpecSwin3D: Advanced Hyperspectral Band Reconstruction with Transformer Architecture},
  author={Sui, Tang},
  journal={Journal Name},
  year={2024},
  publisher={Publisher}
}
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

**Author**: Tang Sui  
**Email**: [tsui5@wisc.edu](mailto:tsui5@wisc.edu)  
**Institution**: University of Wisconsin-Madison

For questions, bug reports, or collaboration inquiries, please contact the author directly.
