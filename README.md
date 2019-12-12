# Description
This repository is to present and check how to perform quantization in PyTorch from Float32 to Int8

# Limitations
This code works with PyTorch 1.3 and above.
In 1.3 in which it was created the uantization feture is *EXPERIMENTAL*.

# Details
There is simple model that is trained (brute force, no validation dataset) on MNIST dataset.

Model is build with:
* Feature extraction: 3 blocks of (conve2D,ReLU, maxpool2D) layers 
* Classification: adaptive average pooling with final dense layer

MNIST dataset is used with [python-mnist](https://pypi.org/project/python-mnist/) library.


**You can see the code [here](pytorch_quantize.ipynb)**

# Results

Code was run on Macbook Pro 13" Core i7 3.1GHz CPU only)

**Original model:**
  Inference time (1000 runs): **4908ms**  
  Saved model size: **12992 bytes**
  Accuracy: **98.2%**  

**Quantized model:**
  Inference time (1000 runs): **2447ms** (50% of original time)
  Saved model size: **5243 bytes** (40.4% of original size)
  Accuracy: **95.7%**  (-2.5%)

  # Discussion

  The model was pretty random so I would not trust this huge accuracy drop. The idea was more to veryfi it the model is not broken completly for this repository.