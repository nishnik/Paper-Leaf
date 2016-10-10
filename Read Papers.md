- [Training Support Vector Machines: an Application to Face Detection](http://web.mit.edu/rfreund/www/10.1.1.9.6021.pdf)

  Edgar Osunay, Robert Freund, Federico Girosiy - CVPR'97<br>
  CV, SVM<br>
  2 Generate the support vectors and then use decomposition algorithm (suggested by paper)<br>

- [Learning Deep Architectures for AI](http://papers.nips.cc/paper/4824-imagenet-classification-with-deep-convolutional-neural-networks.pdf)

  Yoshua Bengio - Technical Report 1312 <br>
  DL<br>
  2 The main conclusion of this section is that functions that can be compactly represented by a depth k architecture might require an exponential number of computational elements to be represented by a depth k − 1 architecture.<br>

- [ImageNet Classification with Deep Convolutional Neural Networks](http://papers.nips.cc/paper/4824-imagenet-classification-with-deep-convolutional-neural-networks.pdf)
  
  Alex Krizhevsky, Ilya Sutskever, Geoffrey E. Hinton - NIPS, 2012.<br>
  CV, DL, CNN<br/>
  3.1 Shows that ReLU converges faster than tanh and sigmoid. *About six times (when not using regularization).<br>*
  3.2 Used two GPUs. *The parallelization scheme that we employ essentially puts half of the kernels (or neurons) on each GPU, with one additional trick: the GPUs communicate only in certain layers. Choosing the pattern of connectivity is a problem for cross-validation. This scheme reduces our top-1 and top-5 error rates by 1.7% and 1.2%, respectively*<br>
  3.3 Used Local Response Normalization. *Response normalization reduces our top-1 and top-5 error rates by 1.4% and 1.2%, respectively.* [Blog: Normalization in Neural Network](http://yeephycho.github.io/2016/08/03/Normalizations-in-neural-networks/)<br>
  3.4 Used overlapping pooling. *This scheme reduces the top-1 and top-5 error rates by 0.4% and 0.3%*<br>
  4.1 Used 32*32*2(2048) varaiations of same image from translation and reflection and PCA on RGB pixels value. *This scheme reduces the top-1 error rate by over 1%*<br>
  4.2 Used Dropout and then averaged by a factor of 0.5<br>
  5 *We initialized the neuron biases in the second, fourth, and fifth convolutional layers, as well as in the fully-connected hidden layers, with the constant 1. This initialization accelerates the early stages of learning by providing the ReLUs with positive inputs.*<br>
  
