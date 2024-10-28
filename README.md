Here’s a refined description to showcase your face recognition project using PCA on your GitHub profile:

---

# Face Recognition System using PCA (Eigenfaces Approach)

## Project Overview
This project is a **Face Recognition System** built using **Principal Component Analysis (PCA)** with the Eigenfaces approach, aimed at recognizing faces based on a limited number of principal components. The system was trained on the **Georgia Tech Face Database** and achieved a testing accuracy of **86%** with only 10 principal components.

## Dataset
The dataset comprises:
- **750 images** (150x150 pixels) of **50 individuals** from the Georgia Tech face database.
- Each person has **15 images** captured under varying lighting and slight variations in facial expressions, making it suitable for testing the PCA approach.

## Approach and Methodology
1. **Preprocessing**: All images were first converted to grayscale to reduce computational complexity and ensure consistent feature extraction.
  
2. **Flattening the Images**: Each grayscale image, originally of size 150x150, was flattened into a one-dimensional vector, facilitating PCA transformation.

3. **Applying PCA**:
   - **Principal Component Analysis (PCA)** was applied to extract the principal components, which capture the significant variance in facial features.
   - After training, the first **10 principal components** (Eigenfaces) were retained, as these captured the essential features required for face recognition with high accuracy.

4. **Testing**: The model was tested on a separate subset of images, achieving an **86% accuracy** rate, demonstrating PCA’s effectiveness in face recognition even with a relatively low-dimensional feature space.

## Key Results
The system was able to successfully distinguish between individuals with high accuracy by utilizing only a fraction of the original image data, highlighting the efficiency of PCA in dimensionality reduction for face recognition.

## Future Scope
Future improvements could include testing with a larger dataset, experimenting with more advanced algorithms like **LDA (Fisherfaces)**, and implementing real-time face recognition using this foundational approach.

---

This summary provides a clear, concise overview of your project and its technical approach, making it a great addition to your GitHub profile! Let me know if you'd like any further modifications.
