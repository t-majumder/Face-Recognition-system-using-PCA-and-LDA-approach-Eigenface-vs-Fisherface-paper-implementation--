# Face Recognition System using PCA (Eigenfaces) and LDA (Fisherfaces) Approaches

## Project Overview

This project explores two well-known techniques for face recognition: **Eigenfaces (PCA-based)** and **Fisherfaces (LDA-based)**, trained and tested on the **Georgia Tech Face Database**. The goal was to build a face recognition system that identifies individuals by their unique facial features, using dimension-reduction techniques to improve computational efficiency and generalization. Testing on this dataset achieved:
- **87% accuracy** with the Eigenfaces approach (PCA)
- **100% accuracy** with the Fisherfaces approach (LDA)

## Dataset

The Georgia Tech Face Database includes:
- **750 images** (150x150 pixels) of **50 individuals**
- **15 images per person**, under various lighting conditions and with slight variations in expression and pose.

## Approach and Methodology

### 1. Preprocessing
All images were converted to grayscale to focus on luminance features, which are most relevant for recognition and reduce computational load. Then each 150x150 image was flattened into a one-dimensional vector (22,500 pixels), ready for dimensionality reduction using PCA and LDA.

### 2. Eigenfaces Approach (PCA)

**Principal Component Analysis (PCA)** transforms the high-dimensional image data into a lower-dimensional subspace while preserving as much variance as possible:
- **Goal**: Capture significant features in the face images using "principal components," or **Eigenfaces**, which are essentially basis images representing main facial feature variations across individuals.
- **Process**:
  1. **Compute the mean face** of the training set and subtract it from each image, creating mean-centered data.
  2. Calculate the **covariance matrix** of the dataset, then its eigenvalues and eigenvectors.
  3. Retain the top **10 eigenvectors** (principal components) corresponding to the largest eigenvalues, which capture the most variance in facial features.
  4. **Project images** onto this reduced feature space. Each face is represented as a combination of the 10 Eigenfaces, making recognition faster.
- **Testing**: New images were projected onto the Eigenface subspace and compared to stored face projections using similarity metrics like Euclidean distance.
- **Results**: Achieved an **87% accuracy**, showing that PCA efficiently captures core facial features for recognition but may struggle with varying lighting and expression changes.

### 3. Fisherfaces Approach (LDA)

**Linear Discriminant Analysis (LDA)** focuses on maximizing the separation between different classes (individuals) in the dataset:
- **Goal**: Find a linear combination of features that best separates classes, creating a unique subspace that maximizes **between-class variance** while minimizing **within-class variance**.
- **Process**:
  1. Project each face image onto a PCA subspace to reduce dimensionality initially (typically fewer than with Eigenfaces).
  2. Apply LDA to maximize the discrimination among classes by computing the **scatter matrices** (within-class and between-class).
  3. Find the **eigenvectors** and **eigenvalues** of the scatter matrix ratio, retaining those with the highest discriminative power.
  4. Each image is then represented in this new "Fisherface" subspace for effective classification.
- **Testing**: New faces were projected onto the Fisherface subspace and matched based on their projections.
- **Results**: Achieved **100% accuracy** on this dataset, with LDA excelling in distinguishing between individuals even under different lighting and facial expressions due to its class-focused optimization.

## Key Comparison: Eigenfaces vs. Fisherfaces

| Aspect               | Eigenfaces (PCA)                              | Fisherfaces (LDA)                                |
|----------------------|-----------------------------------------------|--------------------------------------------------|
| **Objective**        | Maximize total variance in face data          | Maximize between-class variance, minimize within-class variance |
| **Feature Extraction** | Uses principal components (Eigenfaces)       | Uses linear discriminants (Fisherfaces) to enhance class separability |
| **Computational Complexity** | Generally faster with fewer components | Slightly higher due to initial PCA, then LDA computation |
| **Robustness to Variations** | Sensitive to lighting and expressions | More robust, as it focuses on inter-class distinctions |
| **Accuracy**         | 87%                                           | 100%                                            |
| **Ideal Use Case**   | Suitable when there’s less variability in expression/lighting | Ideal for datasets with significant class differences and variability in images |

### Summary

- **Eigenfaces** are excellent for representing key facial features with low dimensionality but may struggle when there’s high variability in lighting and facial expressions.
- **Fisherfaces** provide a more discriminative approach, ideal for classifying faces under varied conditions, as it maximizes separation between individual classes, resulting in higher accuracy.

### Future Scope

1. **Real-time Deployment**: Implementing the Fisherfaces model in a real-time application, perhaps using OpenCV with a live camera feed.
2. **Larger Dataset Testing**: Testing both approaches on larger datasets with more diversity in faces, lighting, and background.
3. **Advanced Models**: Experimenting with deep learning models like Convolutional Neural Networks (CNNs) or transfer learning using pre-trained networks, as they can further improve accuracy and generalizability.

---
