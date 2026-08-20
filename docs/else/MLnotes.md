---
noindex: true
search:
  exclude: true
---

# Machine Learning Notes

- **Batch norm parameter initialization**: ones for weights and zeros for the bias, discussed [here](https://discuss.pytorch.org/t/batchnorm-initialization/16184/7)
- **Linear layer parameter initialization**: biases and weights, by default, are initialized in a uniform distribution, discussed [here](https://discuss.pytorch.org/t/how-are-layer-weights-and-biases-initialized-by-default/13073)
- **Feature maps in CNN**: when the size is not an integer, will do a floor down to make it an integer, as mentioned [here](https://www.coursera.org/learn/convolutional-neural-networks/lecture/wfUhx/strided-convolutions)
- **Tanh derivative**: [here](https://blogs.cuit.columbia.edu/zp2130/derivative_of_tanh_function/)
- **Sigmoid derivative**: [here](https://math.stackexchange.com/questions/78575/derivative-of-sigmoid-function-sigma-x-frac11e-x)
- **Binary logistic regression derivative**: [here](https://math.stackexchange.com/questions/477207/derivative-of-cost-function-for-logistic-regression)

The reason why log + sigmoid is used in the cost function is that it provides a nice derivative for training the model using backpropagation. Mean square error + sigmoid is not a good idea for the cost function, because it is non-convex, i.e., its second derivative is not non-negative. Andrew N.G. also mentioned this in [his course](https://www.coursera.org/lecture/neural-networks-deep-learning/logistic-regression-cost-function-yWaRd). The log-based cost function can also be interpreted from the perspective of maximum likelihood, as discussed [here](https://math.stackexchange.com/questions/886555/deriving-cost-function-using-mle-why-use-log-function). The probability multiplication in the maximum likelihood has nothing to do with the dependency or independency of the events.

- The **softmax function is convex**, proved [here](https://math.stackexchange.com/questions/3427763/convexity-of-softmax-logistic-regression) and [here](https://math.stackexchange.com/questions/2416837/the-second-derivative-of-log-left-sum-limits-i-1nex-i-right-seems-neg).
- The **convolutional layer and its derivative** are explained [here](https://drive.google.com/file/d/1C7JOk0srA3DITZE1nk9_aXIr3wSEVGvd/view?usp=drive_link).
- **Convex properties** are discussed [here](https://en.wikipedia.org/wiki/Convex_function).
- **Warmup in training**: when a model is large regarding the number of parameters, the loss value can easily explode. Therefore, we should start training the model using a warmup to gradually increase the learning rate to a relatively large value. This can prevent the loss from exploding.
- **Vision transformer** is explained well by Shusen Wang [here](https://www.youtube.com/watch?v=HZ4j_U3FC94).
- The **source code for different versions of ViT** is provided [here](https://github.com/lucidrains/vit-pytorch?tab=readme-ov-file).
- The **Swin transformer source code** is available [here](https://github.com/microsoft/Swin-Transformer/tree/main).
- **ResNet32-CIFAR** is available [here](https://github.com/akamaster/pytorch_resnet_cifar10) in PyTorch.
- **Deep learning specialization course assignments** are available [here](https://github.com/amanchadha/coursera-deep-learning-specialization) on GitHub.
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
- **Metrics for object detection** explained [here](https://medium.com/@henriquevedoveli/metrics-matter-a-deep-dive-into-object-detection-evaluation-ef01385ec62).
- **IOU calculation**: <https://www.kaggle.com/code/iezepov/fast-iou-scoring-metric-in-pytorch-and-numpy>

[Back to Else](index.md)
