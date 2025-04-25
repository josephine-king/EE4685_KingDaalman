# Environment setup
## Prerequisites
Install the following:
 - CUDA 12.6 (preferred, not needed but will be much faster if you have the hardware)
 - Python 3.12.5
 - Torch 2.7
 - Matplotlib 
 - Tokenizers
 - Numpy

# Running code
 - Open "miniGPT.ipynb"
 - Run all cells (models are not included in repo, but will be saved locally after training)
 - The notebook has different sections, which define the models, helper functions, a grid search (training) and text generation (based on existing model, if it doesnt exist it will be trained)

# Results and metrics
The models are primarily compared based on perplexity (of the validation set), number of parameters, and final (after 1000 iterations) training loss. We explored the effects of tokenizer vocabulary size, embedding dimension, and number of layers on model performance and computation efficiency. Our results (below) indicate that while increasing these parameters generally improves model performance, there can be diminishing returns, training instability, and increased computational costs if the model parameters are too large for the dataset. This case can especially be seen with 8 decoder layers, where GPT-2 performs good with 12, our models seem to be performing worse.

## Results for All 12 Model Configurations (Vocab Sizes: 5k, 10k, 20k)

| Model | Perplexity (5k) | Training Loss (5k) | Time/Iter (ms, 5k) | Params (M, 5k) | Perplexity (10k) | Training Loss (10k) | Time/Iter (ms, 10k) | Params (M, 10k) | Perplexity (20k) | Training Loss (20k) | Time/Iter (ms, 20k) | Params (M, 20k) |
|-------|------------------|---------------------|----------------------|----------------|-------------------|----------------------|-----------------------|------------------|-------------------|----------------------|----------------------|------------------|
| 0     | 43.87           | 3.60               | 3.35                | **3.43**       | 42.66            | 3.52                | 3.00                 | **5.36**         | 39.45             | 3.43                 | 3.13                 | **9.21**         |
| 1     | 42.17           | 3.56               | 4.38                | 4.91           | 41.35            | 3.50                | 4.27                 | 6.84             | 38.69             | 3.41                 | 4.31                 | 10.69            |
| 2     | 41.77           | 3.55               | 7.00                | 7.87           | 41.02            | 3.49                | 6.85                 | 9.80             | **38.32**         | 3.40                 | 6.94                 | 13.65            |
| 3     | 43.98           | 3.60               | 12.14               | 13.79          | 42.98            | 3.57                | 11.85                | 15.72            | 39.09             | 3.44                 | 12.00                | 19.57            |
| 4     | 42.69           | 3.52               | **2.99**            | 7.44           | 42.67            | 3.48                | 2.96                 | 11.29            | 39.74             | 3.39                 | **2.98**             | 18.98            |
| 5     | 41.23           | 3.50               | 4.28                | 10.99          | 41.26            | 3.47                | 4.20                 | 14.83            | 39.13             | 3.38                 | 4.34                 | 22.52            |
| 6     | 41.18           | 3.49               | 6.78                | 18.09          | **40.16**        | 3.45                | 6.70                 | 21.93            | 38.82             | 3.37                 | 6.79                 | 29.62            |
| 7     | 49.96           | 3.77               | 11.70               | 32.28          | 46.98            | 3.68                | 11.68                | 36.12            | 41.59             | 3.49                 | 11.65                | 43.81            |
| 8     | 40.93           | 3.38               | **2.99**            | 23.02          | 42.57            | **3.41**            | **2.93**             | 32.62            | 40.83             | **3.35**             | 3.00                 | 51.83            |
| 9     | 40.10           | 3.37               | 4.28                | 36.30          | 41.92            | **3.41**            | 4.21                 | 45.91            | 40.78             | **3.35**             | 4.26                 | 65.12            |
| 10    | **39.82**       | **3.36**           | 6.76                | 62.88          | 41.66            | **3.41**            | 6.66                 | 72.49            | 40.10             | **3.35**             | 6.78                 | 91.70            |
| 11    | 113.27          | 4.61               | 11.74               | 116.04         | 110.86           | 4.54                | 11.61                | 125.64           | 108.23            | 4.47                 | 11.58                | 144.85           |

**Note**: Best values for each column are bolded.

# Reflection
This project has been an enriching and hands-on opportunity to deepen our understanding of generative language models, specifically the GPT architecture. From exploring foundational components like tokenization and embeddings to implementing a transformer-based model from scratch, we were able to translate theoretical knowledge into practical application. Working with the TinyShakespeare dataset allowed us to grasp the nuances of training language models on limited textual data, which highlighted both the strengths and limitations of scaled-down LLMs.

One of the most valuable aspects of the experience was performing a comprehensive grid search over key hyperparameters. This process helped us understand how vocabulary size, embedding dimension, and the number of transformer layers impact model performance, generalization, and computational efficiency. It reinforced the belief that there is no universally optimal configuration; instead, effective tuning is highly context-dependent and requires a balance between accuracy, training stability, and resource constraints.

We also faced a variety of technical and conceptual challenges. Training deeper models proved unstable at times, especially those with a high number of decoder layers and large embedding dimensions. These models often plateaued or diverged, illustrating firsthand the difficulties posed by vanishing gradients and optimization in high-dimensional parameter spaces. Additionally, interpreting metrics like perplexity across different vocabulary sizes required critical thinking, as numerical improvements did not always correlate with qualitative improvements in text generation across various vocabulary sizes.

Another challenge was managing computational limitations. While GPU acceleration helped, training even modest-sized models still demanded significant resources and time. We learned the importance of efficient code implementation, batch size selection, and regularization techniques such as dropout to mitigate overfitting and improve generalization.

Despite the challenges, the process of building MiniGPT has been both educational and motivating. It provided a concrete framework for understanding transformer-based architectures and prepared us for more advanced work in natural language processing. We leave this project with a stronger grasp of machine learning principles, an appreciation for the difficulty of model tuning, and a sense of excitement for future explorations in AI.
