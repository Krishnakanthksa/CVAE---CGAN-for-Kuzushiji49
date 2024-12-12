# CVAE-CGAN-for-Kuzushiji49
This project focuses on implementing and comparing Conditional Variational Autoencoders (C-VAE) and Conditional Generative Adversarial Networks (C-GAN) to generate Japanese Hiragana characters from the Kuzushiji-49 dataset (https://github.com/rois-codh/kmnist). The Kuzushiji-49 dataset contains 28x28 grayscale images of 49 different Hiragana character classes, making it a rich resource for implementing generative models. The goal is to explore how conditioning on class and style labels (thick/thin) influences the generation quality and model performance.

## Data Preparation

The dataset preparation was a crucial step. Each image was normalized to scale the pixel values between 0 and 1, which is essential for neural network stability. Additionally, a new style label was created to categorize characters as “thick” or “thin,” based on the median number of foreground pixels in each class. These style labels, along with the one-hot encoded class labels, were integrated into the dataset to enable conditional generation.

This are images having the styles = thick.
![image](https://github.com/user-attachments/assets/b5c899c2-b8f2-446e-b0a1-644b1f817dea)

This are images having the styles = thin.
![image](https://github.com/user-attachments/assets/b2bb5756-4824-4ab5-a75d-8aff6a882501)

The processed dataset was visualized to verify correctness, ensuring that the input to the models was clean and well-labeled.

## Conditional Variational Autoencoder (C-VAE)

The C-VAE is an extension of the traditional VAE, where the model is conditioned on additional labels. In this project, the encoder takes an image and its corresponding class and style labels to map them into a latent space. The decoder then reconstructs the image from this latent representation while considering the same labels.

Key aspects of the C-VAE include:
	•	A latent space that enables controlled sampling, allowing the generation of new images based on desired class and style labels.
	•	A training process that combines reconstruction loss and a regularization term (KL Divergence), ensuring that the latent space is well-organized and meaningful.

During training, the C-VAE consistently generated smooth and coherent images. Although these images sometimes appeared slightly blurry due to the reconstruction-focused loss function, the model demonstrated stable and efficient training.
