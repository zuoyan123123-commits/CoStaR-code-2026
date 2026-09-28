# CoStaR

Official implementation of **CoStaR: Coordinate Stability Regression** for neural visual relocalization.

CoStaR improves scene-coordinate prediction by jointly modeling directional spatial structure and prediction reliability.

The method contains three main components:

- **C-DSM**: Coordinate Directional Spatial Mixing Module
- **RGRR**: Reliability-Guided Residual Refinement
- **GCSO**: Geometry-Calibrated Coordinate Stability Objective

## Repository Structure

CoStaR includes the standalone method implementation and its integration with GLACE.

- `costar/`: core CoStaR modules
- `glace/`: GLACE + CoStaR integration
- `configs/`: training configurations
- `scripts/`: feature extraction, training and evaluation examples
- `tools/`: visualization utilities
- `train.py`: training entry point
- `test.py`: evaluation entry point

## Core Components

### C-DSM

Coordinate Directional Spatial Mixing Module models multi-directional local spatial interactions to improve geometric feature representation.

### RGRR

Reliability-Guided Residual Refinement estimates coordinate prediction reliability and uses it to guide residual coordinate correction.

### GCSO

Geometry-Calibrated Coordinate Stability Objective constrains coordinate prediction and residual refinement during training.

## Dataset Format

The GLACE integration expects scenes organized as:

```
scene/
  train/
    rgb/
    poses/
    calibration/
    features.npy
  test/
    rgb/
    poses/
    calibration/
    features.npy
```

Datasets are not included in this repository.

## Global Feature Extraction

Run:

```
bash scripts/extract_features.sh /path/to/scene /path/to/global_feature_checkpoint.pth
```

## Training

Run:

```
python train.py /path/to/scene outputs/model.pt
```

Default parameters are stored in:

```
configs/glace_default.json
```

## Evaluation

Run:

```
python test.py /path/to/scene outputs/model.pt --session costar
```

## Pretrained Models

Pretrained encoder weights, trained scene models and global-feature checkpoints are not included.

## Supported Benchmarks

Our experiments use:

- 7Scenes
- Cambridge Landmarks
- Wayspots

## Acknowledgements

The implementation builds upon the ACE and GLACE visual relocalization frameworks.

Please cite the corresponding original works when using the associated integration code.

## Citation

Citation information will be added upon publication.
