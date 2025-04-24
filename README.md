*Environment setup
**Prerequisites
Install the following:
 - CUDA 12.6 (preferred)
 - Python 3.12.5
 - Torch 2.7
 - Matplotlib 
 - Tokenizers
 - Numpy

** Running code
 - Open "miniGPT.ipynb"
 - Run all cells (models are not included in repo, but will be saved locally after training)
 - The notebook has different sections, which define the models, helper functions, a grid search (training) and text generation (based on existing model, if it doesnt exist it will be trained)

** Results and metrics
The models are primarily compared based on perplexity and number of parameters.

### Results for All 12 Model Configurations (Vocab Sizes: 5k, 10k, 20k)

| Model | Perplexity (5k) | Training Loss (5k) | Time/Iter (ms, 5k) | Perplexity (10k) | Training Loss (10k) | Time/Iter (ms, 10k) | Perplexity (20k) | Training Loss (20k) | Time/Iter (ms, 20k) |
|-------|------------------|---------------------|----------------------|-------------------|----------------------|-----------------------|--------------------|-----------------------|------------------------|
| 0     | 43.87           | 3.60               | 3.35                | 42.66            | 3.52                | 3.00                 | 39.45             | 3.43                 | 3.13                  |
| 1     | 42.17           | 3.56               | 4.38                | 41.35            | 3.50                | 4.27                 | 38.69             | 3.41                 | 4.31                  |
| 2     | 41.77           | 3.55               | 7.00                | 41.02            | 3.49                | 6.85                 | **38.32**         | 3.40                 | 6.94                  |
| 3     | 43.98           | 3.60               | 12.14               | 42.98            | 3.57                | 11.85                | 39.09             | 3.44                 | 12.00                 |
| 4     | 42.69           | 3.52               | **2.99**            | 42.67            | 3.48                | 2.96                 | 39.74             | 3.39                 | **2.98**              |
| 5     | 41.23           | 3.50               | 4.28                | 41.26            | 3.47                | 4.20                 | 39.13             | 3.38                 | 4.34                  |
| 6     | 41.18           | 3.49               | 6.78                | **40.16**        | 3.45                | 6.70                 | 38.82             | 3.37                 | 6.79                  |
| 7     | 49.96           | 3.77               | 11.70               | 46.98            | 3.68                | 11.68                | 41.59             | 3.49                 | 11.65                 |
| 8     | 40.93           | 3.38               | **2.99**            | 42.57            | **3.41**            | **2.93**             | 40.83             | **3.35**             | 3.00                  |
| 9     | 40.10           | 3.37               | 4.28                | 41.92            | **3.41**            | 4.21                 | 40.78             | **3.35**             | 4.26                  |
| 10    | **39.82**       | **3.36**           | 6.76                | 41.66            | **3.41**            | 6.66                 | 40.10             | **3.35**             | 6.78                  |
| 11    | 113.27          | 4.61               | 11.74               | 110.86           | 4.54                | 11.61                | 108.23            | 4.47                 | 11.58                 |

**Note**: Best values for each column are bolded.
