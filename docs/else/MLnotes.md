---
noindex: true
search:
  exclude: true
---

# Machine Learning Notes

- **Batch norm parameter initialization**: ones for weights and zeros for the bias, discussed here
- **Linear layer parameter initialization**: biases and weights, by default, are initialized in a uniform distribution, discussed here
- **Feature maps in CNN**: when the size is not an integer, will do a floor down to make it an integer, as mentioned here
- **Tanh derivative**: here
- **Sigmoid derivative**: here
- **Binary logistic regression derivative**: here

The reason why log + sigmoid is used in the cost function is that it provides a nice derivative for training the model using backpropagation. Mean square error + sigmoid is not a good idea for the cost function, because it is non-convex, i.e., its second derivative is not non-negative. Andrew N.G. also mentioned this in his course. The log-based cost function can also be interpreted from the perspective of maximum likelihood, as discussed here. The probability multiplication in the maximum likelihood has nothing to do with the dependency or independency of the events.

- The **softmax function is convex**, proved here and here.
- The **convolutional layer and its derivative** are explained here.
- **Convex properties** are discussed here.
- **Warmup in training**: when a model is large regarding the number of parameters, the loss value can easily explode. Therefore, we should start training the model using a warmup to gradually increase the learning rate to a relatively large value. This can prevent the loss from exploding.
- **Vision transformer** is explained well by Shusen Wang here.
- The **source code for different versions of ViT** is provided here.
- The **Swin transformer source code** is available here.
- **ResNet32-CIFAR** is available here in PyTorch.
- **Deep learning specialization course assignments** are available here on GitHub.
- **Moment**: <https://en.wikipedia.org/wiki/Moment_(mathematics)>
- **Bayes' theorem**: <https://en.wikipedia.org/wiki/Bayes%27_theorem>
- **Visualization feature distribution**: T-SNE, PCA
- **Colour theory**: <https://electronics360.globalspec.com/article/10403/how-your-computer-actually-creates-color>
- **YIQ colour space**: <https://en.wikipedia.org/wiki/YIQ>
- **Seven colours**: <https://en.wikipedia.org/wiki/ROYGBIV>, <https://spie.org/publications/pm105_11_color>

## Image process

- **First derivative operator**: <https://www.youtube.com/playlist?list=PL2zRqk16wsdqXEMpHrc4Qnb5rA1Cylrhx>
- **Wavelet transform for images** is well explained here: <https://www.youtube.com/watch?v=zAfHlTjX0XU>

## CNN visualization

- <https://github.com/jacobgil/pytorch-grad-cam>
- <https://github.com/utkuozbulak/pytorch-cnn-visualizations>
- **Metrics for object detection** explained here.
- **IOU calculation**: <https://www.kaggle.com/code/iezepov/fast-iou-scoring-metric-in-pytorch-and-numpy>

[Back to Else](index.md)
