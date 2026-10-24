# End-to-End AI Pipeline for Cow Re-Identification in Dairy Farms

**Master’s thesis | University of Rostock · Fraunhofer IGD | 2026**  
**Author:** MD Humayun Kabir

[Read the full thesis (PDF)](Master_Thesis_MD_Humayun_Kabir.pdf)

## Overview

This thesis investigates how individual cows can be identified from farm videos using visual appearance. I developed a modular computer vision pipeline combining detection, segmentation, multi-object tracking, visual embeddings and gallery-based identity matching.

The work was conducted at Fraunhofer IGD as part of my M.Sc. in Computer Science International at the University of Rostock, contributing to ongoing research in automated livestock monitoring.

## My contribution

- Built a Python/PyTorch video re-identification pipeline integrating YOLO segmentation, BoT-SORT tracking, embedding extraction, gallery matching and track-level identity decisions.
- Fine-tuned and compared ResNet-50, MegaDescriptor and DINOv3 on two farm-specific datasets.
- Prepared a segmentation dataset of **3,681 images** using SAM3-generated pseudo-labels and fine-tuned YOLO11m for cow images affected by metal-bar occlusion.
- Evaluated image retrieval, continuous-video identity recovery and cross-farm transfer, analysing errors associated with viewpoint, illumination, occlusion and segmentation quality.

## Selected results

### Farm A: closed-set image retrieval

| Embedding model | Rank-1 accuracy | Retrieval mAP |
| --- | ---: | ---: |
| ResNet-50 | 92.17% | 92.56% |
| MegaDescriptor | 91.92% | 92.62% |
| DINOv3 | **93.43%** | **93.57%** |

These results measure retrieval between separate query and gallery images of identities represented during model training.

### Farm B: RFID-supported temporal video evaluation

| Configuration | Precision | Gallery-identity recall | F1-score |
| --- | ---: | ---: | ---: |
| DINOv3 + custom YOLO11m | **93.55%** | **71.31%** | **80.93%** |
| MegaDescriptor + custom YOLO11m | 86.30% | 51.64% | 64.62% |

The DINOv3 configuration recovered **87 of 122 RFID-confirmed gallery identities**, achieving **19.67 percentage points higher recall** than MegaDescriptor under the same segmentation, tracking and evaluation settings.

This evaluation used a separate 30-minute video recording from the gallery source recording. Precision and recall describe gallery-identity recovery within RFID-supported temporal windows. The thesis provides the evaluation protocol, thresholds and limitations.

## Technical stack

- **Development:** Python, PyTorch, OpenCV.
- **Models and methods:** ResNet-50, MegaDescriptor, DINOv3, YOLO11, SAM3, BoT-SORT.
- **Compute:** Ubuntu Linux, CUDA-enabled NVIDIA RTX A6000; one GPU per training or inference run.

## Repository contents and code availability

This repository presents the thesis PDF and project overview. Research source code is maintained in Fraunhofer IGD’s internal GitLab. Source code, research datasets and trained model weights are not included here.

