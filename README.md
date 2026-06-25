# border-confined-grid
Generates an evenly spaced reference grid from a border-only checkerboard to provide an unoccluded view for tracking 

![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)

A Python pipeline for border-confined grid generation and camera calibration to enable unobstructed visual tracking in tissue phantoms.

This repository contains the software pipeline used for the benchtop experimental setup described in our paper: *Design and Validation of a Needle Driver System for Minimally Invasive Surgery*.

## Overview

Traditional benchtop experimental setups for needle steering often require a calibration grid directly beneath the tissue phantom, which visually occludes the phantom and interferes with accurate needle tracking. 

This pipeline solves that problem by using a **border-confined checkerboard pattern**. It detects the centroids of the border squares and programmatically generates an evenly spaced reference grid over the blank, unobstructed interior. 

### Key Features
* **Camera Calibration**: Removes lens distortion and applies planar homography to correct residual camera tilt.
* **Border Grid Detection**: Detects and uses border checkerboard squares to generate an internal 10x10 mm reference grid.
* **High Precision**: Achieves a root-mean-square reprojection error of 0.68 pixels and a final distance measurement error of -0.21 ± 0.16 mm.

## Prerequisites
* Python 3.8+
* OpenCV (`cv2`)
* NumPy
* SciPy

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/PranaliIngole/border-confined-grid.git
   cd border-confined-grid
   ```
2. Install the required dependencies:
   ```bash
   pip install opencv-python numpy scipy
   ```

## Usage

1. **Print the Grid**: Print a border-only checkerboard and place it beneath your gelatin phantom. (You can use the included sample PDF of the 5 mm pattern, or create your own with any box size according to your desired grid resolution).
2. **Run Calibration**: 
   ```bash
   python generate_grid.py --image path/to/your/setup_image.jpg
   ```
3. The script will output the distortion coefficients, homography matrix, and the pixel-to-metric conversion factor (typically ~0.2 mm/pixel).

## Citation

If you use this code in your research, please cite our paper:

```bibtex
@unpublished{ingole2026design,
  title={Design and Validation of a Needle Driver System for Minimally Invasive Surgery},
  author={Ingole, P. and Patel, N.},
  note={Submitted to the IPROMM Conference},
  year={2026}
}
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
