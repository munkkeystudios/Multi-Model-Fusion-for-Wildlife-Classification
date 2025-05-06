# 🦁 Multi-Model Fusion with Cross-Attention for Wildlife Classification 🐻

[![GitHub license](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![PyTorch](https://img.shields.io/badge/PyTorch-1.10%2B-orange)](https://pytorch.org/)

## 📊 Project Overview

This repository implements a novel multi-model fusion approach for wildlife classification, leveraging the synergy between two powerful vision models through cross-attention mechanisms. Our framework achieves significantly improved accuracy in classifying challenging wildlife categories (bears, big cats, big dogs, and deer) while effectively filtering out non-target images.

### 🏆 Key Results

- *84.94%* overall accuracy on the test set (36.14% improvement over baselines)
- Effective handling of the challenging 'other' class with *82.0% F1 score*
- Parameter-efficient architecture with only *2.5M trainable parameters*

## 🔍 Model Architecture

Our approach consists of three main components:

1. *🕵 Animal Detection*: Using MegaDetectorV6 to precisely locate and crop animal regions
2. *🧠 Dual Feature Extraction*: Parallel feature extraction using frozen YOLOv11x-cls and EfficientNet-B0
3. *🔀 Cross-Attention Fusion*: Dynamic feature integration with a trainable cross-attention module

## ⬇ Pre-trained Weights

Two pre-trained model checkpoints are available in the [Releases](https://github.com/munkkeystudios/Multi-Model-Fusion-for-Wildlife-Classification/releases) section:

- *fusion_model_v1.pth*: Fusion model trained on 4 animal classes (without 'other' class)
- *fusion_model_final.pth*: Complete model with 'other' class handling

## 📋 Dataset Structure

The model was trained on the following distribution:

| Class | Training Images | Testing Images |
|-------|----------------|---------------|
| Bear | 600 | 300 |
| Big Cat | 1,800 | 500 |
| Big Dog | 1,500 | 500 |
| Deer | 2,960 | 600 |
| Others | - | 1,195 |

## 📈 Performance Comparison

| Model | Accuracy | Macro F1 | Parameters |
|-------|----------|----------|------------|
| EfficientNet-B0 | 48.80% | 0.581 | 5.3M |
| YOLOv11x-cls | 55.90% | 0.631 | 29.6M |
| *Our Model* | *84.94%* | *0.860* | *2.5M* (trainable) |

## 🔍 Key Findings

Our extensive ablation studies revealed:

- Cross-attention fusion significantly outperforms single-backbone approaches
- MegaDetectorV6 provides superior localization compared to general-purpose detectors
- The two-stage detection-classification pipeline effectively handles non-target classes
- Class balancing techniques successfully address the dataset imbalance challenges

## 📝 Citation

If you find this project useful in your research, please consider citing:

bibtex
@article{talha2025multimodel,
  title={Multi-Model Fusion with Cross-Attention for Wildlife Classification},
  author={Talha, Muhammad and Ahmed, Uzair},
  journal={arXiv preprint arXiv:2505.00000},
  year={2025}
}


## 📄 License

This project is licensed under the APACHE-2.0 License - see the [LICENSE](LICENSE) file for details.
