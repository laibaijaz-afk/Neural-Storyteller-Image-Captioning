# Neural-Storyteller-Image-Captioning

Introduction
Image captioning is one of the most fascinating applications of Deep Learning that combines Computer Vision and Natural Language Processing .In this project, I built an end-to-end Image Captioning model that can generate meaningful textual descriptions for images using:

CNN (ResNet) for feature extraction
LSTM for sequence generation
Beam Search for improved caption decoding
BLEU & classification metrics for evaluation
Gradio for deployment
Model Architecture
The architecture follows an Encoder–Decoder framework:

🔹 Encoder (CNN)
Pretrained ResNet
Extracts visual feature vectors from images
Output feature vector passed to decoder
🔹 Decoder (LSTM)
Takes image features as initial hidden state
Generates caption word-by-word
Uses word embeddings + LSTM + Linear layer
Dataset & Preprocessing
Cleaned captions
Dataset split:

90% Training
10% Validation

Training Process
The model was trained for multiple epochs to ensure proper learning and convergence. During training, the training loss consistently decreased, showing that the model was effectively learning from the data. The validation loss initially improved and later stabilized, indicating the model’s generalization behavior. Based on both validation performance and the quality of generated captions, a balanced checkpoint around epoch 8–10 was selected for the final model to ensure coherent caption generation and stable performance on unseen images.

Loss Curve Analysis
The loss curves show that the training loss decreased consistently over epochs, indicating effective learning. The validation loss initially improved and later stabilized, reflecting the model’s ability to generalize. This analysis helped in selecting a balanced model checkpoint that avoids underfitting and excessive memorization.

Decoding Strategy
Initially, greedy decoding was used to generate captions by selecting the most probable word at each time step. However, this approach often produced shorter or less descriptive captions. To improve caption quality, Beam Search (beam size = 5) was implemented. Beam Search considers multiple candidate sequences at each step, resulting in more coherent and meaningful captions.

Quantitative Evaluation
The model was evaluated using BLEU-4 score to measure n-gram overlap between predicted and ground-truth captions. Additionally, token-level Precision, Recall, and F1-score were computed to assess word-level prediction accuracy. These metrics provided a comprehensive evaluation of both linguistic quality and prediction consistency.

Caption Examples
Five random test images were selected to qualitatively evaluate the model. For each image, the ground-truth caption and the model-generated caption were displayed. Beam Search produced more descriptive and contextually relevant captions compared to greedy decoding, demonstrating the effectiveness of improved decoding strategies.

App Deployment
To demonstrate the model interactively, a web-based interface was built using Gradio. The application allows users to upload an image and receive an automatically generated caption in real time. This deployment makes the model accessible and showcases its practical usability beyond training and evaluation.


Conclusion
This project successfully combines Computer Vision and Natural Language Processing to generate captions from images using a CNN–LSTM architecture. By integrating Beam Search and proper evaluation metrics, the model produces coherent and meaningful captions. The deployment further highlights the practical application of deep learning models in real-world scenarios.
Added special tokens: <start> and <end>
Tokenization & vocabulary creation
Padding sequences to fixed length
