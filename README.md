# **EviRCOD: Evidence-Guided Probabilistic Decoding for Referring Camouflaged Object Detection**

**EviRCOD** is an evidence-guided probabilistic framework for Referring Camouflaged Object Detection (Ref-COD). As introduced in the accompanying paper, the framework addresses key limitations in existing Ref-COD methods by integrating three novel components:

1.  **Reference-Guided Deformable Encoder (RGDE)**: Designed to alleviate semantic mismatch and cross-scale inconsistency. It employs adaptive reference-driven modulation and deformable multi-scale aggregation to construct a semantically aligned latent space for target localization.
2.  **Uncertainty-Aware Evidential Decoder (UAED)**: Aims to reconstruct fine-grained spatial structures while explicitly modeling prediction confidence. It integrates evidential learning into a hierarchical Transformer decoder, jointly modeling aleatoric and epistemic uncertainty for robust confidence propagation.
3.  **Boundary-Aware Refinement Module (BARM)**: Leverages low-level edge priors and high-level uncertainty maps to selectively refine ambiguous boundaries, achieving precise contour recovery while preserving reliable regions.

The framework is optimized end-to-end via a joint hybrid loss that enforces structural fidelity, boundary sharpness, and well-calibrated uncertainty.

## **Visual Results**

The visual results below demonstrate the superior performance of EviRCOD compared to existing methods such as R2CNet [3] and UAT [4]. As stated in the paper, the proposed EviRCOD generates more complete segmentation structures, sharper boundaries, and fewer background misclassifications.
![Visual Comparison 1](figures/figure1.png) 
![Visual Comparison 2](figures/figure3.png)

The following supplementary visualization further showcases the overall effectiveness of EviRCOD across diverse and challenging camouflage scenarios.

![Supplementary Visualization](figures/all_1.png)

## **Framework Architecture**

The overall pipeline of EviRCOD is illustrated below, detailing the interaction between the RGDE, UAED, and BARM modules within an end-to-end architecture.

![EviRCOD Framework](figures/framework.png)

## 📈 **Performance Summary**

Extensive experiments on the Ref-COD benchmark (R2C7K) demonstrate that EviRCOD establishes a new state-of-the-art. As shown in the paper, EviRCOD consistently outperforms existing methods such as R2CNet and UAT across multiple evaluation metrics. The following table highlights the quantitative comparison:

| Method | Sₘ ↑ | ωF ↑ | αE ↑ | MAE ↓ |
|--------|------|------|------|-------|
| R2CNet | 0.805 | 0.669 | 0.879 | 0.036 |
| UAT | 0.855 | 0.757 | 0.912 | 0.026 |
| **EviRCOD (Ours)**| **0.869** | **0.799** | **0.944** | **0.021** |

*Note: Higher values are better for Sₘ, ωF, and αE; lower values are better for MAE.*

The full model of EviRCOD achieves the best performance across all metrics, validating the effectiveness of the proposed framework.

## **Requirements**

- Python 3.9
- PyTorch 2.5.1
- CUDA 12.8
- TensorboardX 2.0
- opencv-python

```bash
pip install torch==2.5.1 torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121
pip install tensorboardX opencv-python
```

## **Getting Started**

### 1. **Data Preparation**

Download the **R2C7K** dataset from [Baidu Netdisk](https://pan.baidu.com/s/1LHdqpD3w24fcLb_dbR6DyA) (access code: `2013`). Organize the dataset as follows:

```
R2C7K/
├── Camo/
│   ├── train/                # Training set (camo-subset, 64 categories)
│   └── test/                 # Testing set (camo-subset, 64 categories)
└── Ref/
    ├── Images/               # Reference images (ref-subset, 64 categories)
    ├── RefFeat_ICON-R/       # Pre-extracted object representations
    └── Saliency_ICON-R/      # Pre-extracted foreground maps
```

Update the `data_root` parameter in `train.py`, `infer.py`, and `test.py` with your dataset path.

### 2. **Training**

1. Download the pre-trained PVTv2 weights from [Baidu Netdisk](https://pan.baidu.com/s/1czmAayK9N5bW2HqrBDHWaw) (code: `EviR`).
2. Place the weights in your custom folder.
3. Run the training script:
```bash
python train.py
```

A pre-trained EviRCOD model is also available: [Baidu Netdisk](https://pan.baidu.com/s/10UtikqOnWzyGHxI8Ij-o2g) (code: `EviR`).

### 3. **Testing**

Evaluate the model performance on the test set:
```bash
python test.py
```

### 4. **Inference**

Generate prediction maps:
```bash
python infer.py
```

Pre-generated prediction maps are available: [Baidu Netdisk](https://pan.baidu.com/s/1oU18MDWG6BuyyFdaoOkOzQ) (code: `EviR`).
