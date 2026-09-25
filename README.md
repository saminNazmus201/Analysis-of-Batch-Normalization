# Analysis of Batch Normalization

An experimental study on how Batch Normalization affects the training and performance of different deep learning models when working with a limited and varied image dataset.

## About the Project

Batch Normalization is commonly used in deep neural networks to make training more stable and efficient. However, its effect can vary depending on the model and the characteristics of the dataset.

In this project, we explore how adding Batch Normalization changes the performance of different image classification models. We compare models trained with and without Batch Normalization and look at both their accuracy and training time.

The main goal is not simply to check whether Batch Normalization improves accuracy, but to understand how its effect changes across different architectures.

## Dataset

The dataset contains:

- **3,799 JPG images**
- **5 classes**
- Approximately **9.04 GB** in size
- Separate training, validation, and testing sets

The five classes are:

- Dyskeratotic
- Koilocytotic
- Metaplastic
- Parabasal
- Superficial-Intermediate

The dataset is relatively limited in size while containing variations in image conditions, making it useful for studying how normalization affects model training.

## Models

We experimented with several CNN-based architectures:

- Custom CNN
- ResNet-50
- ResNet-101
- MobileNetV2
- MobileNetV3 Large

For each architecture, we compared versions with and without Batch Normalization where applicable.

## Experimental Setup

The experiments were designed to keep the comparison as consistent as possible while changing the use of Batch Normalization.

The main setup included:

- **Optimizer:** Adam
- **Evaluation:** Training and validation accuracy
- **Comparison:** With vs. without Batch Normalization
- **Regularization:** No explicit L1/L2 regularization was used
- **Additional baseline:** CNN without Batch Normalization using Dropout

We also recorded the training time to see whether Batch Normalization affected how quickly the models trained.

## Results

The final test accuracies from our experiments are shown below:

| Model | Batch Normalization | Accuracy |
|---|---:|---:|
| CNN + Dropout | No | 93.27% |
| CNN | Yes | 94.91% |
| ResNet-50 | Yes | 73.89% |
| ResNet-50 | No | 76.19% |
| ResNet-101 | Yes | 93.43% |
| ResNet-101 | No | 90.48% |
| MobileNetV2 | Yes | 66.01% |
| MobileNetV2 | No | 76.52% |
| MobileNetV3 Large | Yes | 22.17% |
| MobileNetV3 Large | No | 22.33% |

These results show that the effect of Batch Normalization was not the same for every architecture.

For example, the CNN improved from **93.27% to 94.91%** when Batch Normalization was used. ResNet-101 also showed an improvement, increasing from **90.48% to 93.43%**.

On the other hand, ResNet-50 and MobileNetV2 achieved higher accuracy without Batch Normalization in our experiments. MobileNetV3 Large showed very similar results in both settings.

This suggests that Batch Normalization does not necessarily provide the same benefit across different architectures and datasets.

## Training Time

We also compared the training time of the different models.

| Model | With Batch Normalization | Without Batch Normalization |
|---|---:|---:|
| CNN | 4 min 39 sec | 5 min |
| ResNet-50 | 39 min | 41 min |
| ResNet-101 | 6 min 30 sec | 7 min 28 sec |
| MobileNetV2 | 4 min 33 sec | 4 min 46 sec |
| MobileNetV3 Large | 4 min 45 sec | 4 min 52 sec |

In our experiments, the models using Batch Normalization generally had slightly shorter training times. The difference was not identical across all architectures, but the training curves also showed that Batch Normalization could make the training process more stable in some cases.

## What We Learned

One of the main observations from this project is that **Batch Normalization is not a guaranteed improvement for every model**.

Its effect depends on factors such as the model architecture and the characteristics of the dataset. In some experiments, Batch Normalization improved both performance and training behavior, while in others the model without Batch Normalization achieved higher test accuracy.

The training and validation curves also helped us understand how differently the models behaved during training.

Overall, the experiments highlight the importance of testing architectural choices rather than assuming that a commonly used technique will always improve the final result.

## Repository Structure

```text
Analysis-of-Batch-Normalization/
│
├── With_batch_norm_wo_do.ipynb
├── Without_batch_norm.ipynb
├── CSE465Presentation.pptx
└── README.md
