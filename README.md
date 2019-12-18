# Description
This repository is to present and check how to perform quantization in PyTorch from Float32 to Int8

# Limitations
This code works with PyTorch 1.3 and above.
In 1.3 in which it was created the uantization feture is *EXPERIMENTAL*.

# Details
There is simple model that is trained on MNIST dataset.

Model is build with:
* Feature extraction: 3 blocks of (conve2D,ReLU, maxpool2D) layers + Dropouts with rates 0.1
* Classification: adaptive average pooling with final dense layer with 0.3 Dropout

MNIST dataset is used with [python-mnist](https://pypi.org/project/python-mnist/) library.


**You can see the code here:**  
- [Static quantization](pytorch_quantize.ipynb)
- [Quantization-aware training](pytorch_quantize_training-aware.ipynb)

# Results

Code was run on Macbook Pro 13" Core i7 3.1GHz CPU only)

**Original model:**  
  Inference time (1000 runs): **5280ms**  
  Saved model size: **13595 bytes**  
  Accuracy on test: **96.5%**  

**Quantized model (static):**  
  Inference time (1000 runs): **2763ms** (52% of original time)  
  Saved model size: **5792 bytes** (42.6% of original size)  
  Accuracy on test : **95.0%**  (-1.5%)  

**Quantization-aware training model:**  
*Notice*: weights taken from original model results, then 'fine-tuned' for 5 epochs.  
  Inference time (1000 runs): **2693ms**  (51% of original time)  
  Saved model size: **6527 bytes** (48.0% of original size)  
  Accuracy on test : **95.5%**  (-1.0% / -1.3% vs fineduned model) 

  # Discussion
  The model was pretty random so I would say the accuracy drop is acceptable.   
  The idea was more to verify if the model is not broken completly after the conversion.