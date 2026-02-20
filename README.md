# Medical_Image_Processing

This repository contains the code and the final report related to the group project developed for the "**Medical Image Processing**" course (AY 2025/2026).

### 🎯 Aim of the project

The aim of this project was to develop an automated pipeline for **retinal vessel segmentation** using the **FIVES dataset**. 

The study involved training a **U-Net** architecture to perform binary segmentation on high-resolution fundus images. The project focused on overcoming common dataset issues like underexposure and noise through a custom **Red-Green channel fusion** and specific pre-processing steps. To ensure clinical readability, a morphological post-processing stage was implemented to remove small non-vascular artifacts based on skeleton length.

### 💻 Technologies

**Model Architecture**: **U-Net** with 16 initial filters, a depth of 4 and skip connections for fine detail recovery.

**Image Processing Pipeline**:
* **Pre-processing**: Custom channel combination ($Y = 0.337R + 0.663G$), Gaussian filtering ($3\times3$, $\sigma=1$), and Gamma Correction ($\gamma=0.9$).
* **Data Augmentation**: Geometric transformations including horizontal/vertical flips, $90^\circ$ rotations and transpositions to triple the training set size.
* **Post-processing**: Morphological skeletonization and removal of isolated components with a skeleton length shorter than 40 pixels.
* **Optimization**: 2-step gradient accumulation and **Dice Loss** optimization.

**Evaluation Metrics**: Performance assessment via Dice Similarity Coefficient (DSC), Centerline Dice (clDice), Precision and Recall.