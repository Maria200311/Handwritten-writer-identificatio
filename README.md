
##  Project Title
**Handwritten Writer Identification**

##  Team Members
- Maria Iqbal  
- Fathima Mahmoodha   
- Mohamed Abdullahi Ali 

---

##  Introduction
Writer identification aims to identify the individual who wrote a given handwritten document, regardless of the written content.  
This field has important applications in **forensic analysis**, **document verification**, and **security systems**.

Each person’s handwriting contains unique patterns formed by strokes, spacing, and writing style. These features can be effectively learned using **Deep Neural Networks**, particularly **Convolutional Neural Networks (CNNs)**.

The goal of this project is to develop a **CPU-based deep learning system** capable of identifying the writer of a handwritten page.


##  Dataset Description
- The dataset consists of **high-resolution scanned handwritten documents**
- Each writer represents **one class**
- **Training set:** 1 page per writer  
- **Testing set:** 2 pages per writer  
- **Total test samples:** 140 handwritten pages  


##  Methodology

###  Preprocessing & Segmentation
- Each handwritten page is divided into **three vertical patches**
- Line segmentation using:
  - Projection profiles
  - Morphological techniques
- Word segmentation is applied
- Character segmentation is attempted
  - If it fails, word-level segmentation is used
- All images are resized to **64 × 64 pixels**
- Pixel values are normalized to **[0, 1]**

###  Data Augmentation
To improve generalization and reduce overfitting:
- Random rotation
- Translation
- Zooming
- Contrast adjustment
- Gaussian noise addition

Each vertical strip is augmented, producing **six patches per page**.

---

##  CNN Architecture
The CNN model consists of:
- **Five convolutional blocks**, each containing:
  - Conv2D layer
  - Normalization layer
  - Max-pooling layer
  - Dropout layer
- Global Average Pooling
- Dense layer with **1024 neurons**
- Dropout layer
- Softmax output layer

###  Training Details
- Optimizer: **Adam**
- Loss function: **Categorical Cross-Entropy**
- Training environment: **CPU-only**
- Class weighting used to handle imbalance
- Early stopping based on validation accuracy
- Learning rate reduction on validation loss plateau
- Final model saved as `model.keras`

##  Testing & Evaluation
- Test pages undergo the same preprocessing and segmentation pipeline
- CNN predicts probabilities for each segmented crop
- Probabilities are averaged to obtain **document-level prediction**

###  Evaluation Metrics
- **Accuracy**
- **Macro F1 Score** (used due to class imbalance)


##  Results
- **Test Accuracy:** 88.57%
- **Macro F1 Score:** 0.86

Additional outputs include:
- Confusion matrix
- Per-writer performance report
- Prediction result files


##  Model & Demo Video
The trained model and demonstration video are available at:

**Google Drive Link:**  
https://drive.google.com/drive/folders/1ae7jLsuZKspHas-VpDdzxNMPAW6ZEL9W?usp=sharing


##  Note on Source Code
The source code for this project is not included in this repository due to access limitations.  
This repository serves as a **documentation and results showcase** for the project.


##  Technologies Used
- Deep Learning
- Convolutional Neural Networks (CNN)
- Python (conceptual)
- TensorFlow / Keras (conceptual)


## 📌 Disclaimer
This repository is created for **academic and educational purposes only**.
