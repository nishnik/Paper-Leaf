### Have a look at [issues](https://github.com/nishnik/Paper-Leaf/issues) for recent reads.

### Summaries of papers read before I started tracking them in issues

- [A Convolutional Neural Network for Modelling Sentences](https://arxiv.org/abs/1404.2188)<br>
  Nal Kalchbrenner, Edward Grefenstette, Phil Blunsom <br/>
  1.) Applying the weights m in a wide convolution has some advantages over applying them in a narrow one. A wide convolution ensures that all weights in the filter reach the entire sentence, including the words at the margins. This is particularly significant when m is set to a relatively large value such as 8 or 10.<br>
  2.) The max pooling operation has some disadvantages too. It cannot distinguish whether a relevant feature in one of the rows occurs just one or multiple times and it forgets the order in which the features occur<br>
  3.) The k-max pooling operation makes it possible to pool the k most active features in p that may be a number of positions apart; it preserves the order of the features, but is insensitive to their specific positions. (I think for words, it makes sense because even the neigboring words can significantly alter the sense. Ex, "I  am not there", both 'not' and 'there' are significant, which is generally not the case in images, but then I think we should try using k-max pooling in the last layers of the image classification models.)<br/>
  4.) For an example in sentiment prediction, according to the equation a first order feature such as a positive word occurs at most k1 times in a sentence of length s, whereas a second order feature such as a negated phrase or clause occurs at most k2 times. (Here k_i is the k for k-max pooling at layer i, they have k_i > k_i+1)<br/>
  5.) Feature detectors in different rows, however, are independent of each other until the top fully connected layer. A simple method called folding that does not introduce any additional parameters. After a convolutional layer and before (dynamic) k-max pooling, one just sums every two rows in a feature map component-wise. For a map of d rows, folding returns a map of d/2 rows, thus halving the size of the representation, and also two rows get combined.<br/>
- [Swish: a Self-Gated Activation Function](https://arxiv.org/abs/1710.05941) <br>
  Prajit Ramachandran, Barret Zoph, Quoc V. Le <br>
  New activation function `x.sigmoid(x)` <br> Key points from paper: <br>
  1.) The success of Swish implies that the gradient preserving property of ReLU (i.e., having a derivative of 1 when x > 0) may no longer be a distinct advantage in modern architectures.<br>
  2.) Activation functions should be unbounded<br>
  3.) But being bounded below is desirable as it works as a regularizer<br>
  Nice discussion on reddit: <br>
  1.) [Combining with selu](https://www.reddit.com/r/MachineLearning/comments/773epu/r_swish_a_selfgated_activation_function_google/doj24ps/) <br>
- [Densely Connected Convolutional Networks](https://arxiv.org/pdf/1608.06993.pdf) <br>
  Gao Huang, Zhuang Liu, Kilian Q. Weinberger, Laurens van der Maaten <br>
  Best paper CVPR 2017, Every layer connected to every subsequent layer, SOR without data augmentation. <br>
  Two types of proposed architecture, Densenet and DensenetBC which has 1x1 convolutional bottleneck layers, and compresses the number of channels at each transition layer by 0.5. <br>

- [Bitcoin: A Peer-to-Peer Electronic Cash System ](https://bitcoin.org/en/bitcoin-paper) <br>
  Anonymous <br>
  Bitcoin original paper<br>
  
- [Deep Speech: Scaling up end-to-end speech recognition](https://arxiv.org/abs/1412.5567) <br>
  Awni Hannun, Carl Case, Jared Casper, Bryan Catanzaro, Greg Diamos, Erich Elsen, Ryan Prenger, Sanjeev Satheesh, Shubho Sengupta, Adam Coates, Andrew Y. Ng <br>
  DL, Speech, HPC <br>
  Paper on speech recognition. Key points from paper<br>
  1.) One disadvantage of LSTM cells is that they require computing and storing multiple gating neuron responses at each step. Since the forward and backward recurrences are sequential, this small additional cost can become a computational bottleneck.<br>
  2.) Used language model to improve the results from RNN. <br>
  3.) Data parallelism as the next paper.<br>
  4.) Model parallelism. Model is sequential, and would need h_f and h_b for the bidirectional RNN. When computing the recurrent layer activations, the first GPU begins computing the forward activations h(f) , while the second begins computing the backward activations h(b). At the mid-point (t = T(i)/2), the two GPUs exchange the intermediate activations, h(f) at T/2 and h(b) at T/2 and swap roles. The first GPU then finishes the backward computation of h(b) and the second GPU finishes the forward computation of h(f).<br>
  5.) Why Model Parallelism: Data parallelism yields training speedups for modest multiples of the minibatch size (e.g., 2 to 4), but faces diminishing returns as batching more examples into a single gradient update fails to improve the training convergence rate.<br>
  6.) Captured Lombard effect in training data: speakers actively change the pitch or inflections of their voice to overcome noise around them.

- [Bandwidth optimal all-reduce algorithms for clusters of workstations](http://www.sciencedirect.com/science/article/pii/S0743731508001767) <br>
  Pitch Patarasuk, Xin Yuan <br>
  HPC <br>
  How to use different computing resources together. A nice explanation [here](http://research.baidu.com/bringing-hpc-techniques-deep-learning/).

- [Effective Dimensionality Reduction for Word Embeddings](https://arxiv.org/abs/1708.03629)
  Vikas Raunak<br>
  ML, NLP<br>
  A nice post processing method, and simple PCA. Idea: experiment for PCA, or images

- [Iterative Deep Convolutional Encoder-Decoder Network for Medical Image Segmentation](https://arxiv.org/abs/1708.03431)
  Jung Uk Kim, Hak Gu Kim, Yong Man Ro<br>
  DL, CV, Medical<br>
  Read it for the new error function based on dice coefficient and the iterative algorithm. SOR. 

- [An Effective Training Method For Deep Convolutional Neural Network](https://arxiv.org/abs/1708.01666)
  Yang Jiang, Zeyang Dou, Jie Cao, Kun Gao, Xi Chen <br>
  DL <br>
  Learn non-linearity (a variant of Relu) using backpropagation, better training

- [Tutorial on Variational Autoencoders](https://arxiv.org/pdf/1606.05908.pdf)
  Carl Doersch <br>
  VAE, DL <br>
  Not a conference published research paper, but informative about VAEs.

- [Genetic CNN](https://arxiv.org/abs/1703.01513)
  Lingxi Xie, Alan Yuille <br>
  DL <br>
  Represented connection between Conv layers as binary numbers which can eventually represent networks like VGG or ResNet. As for k layered network, number of connections is of order 2^k. So to effectively search this space, they have used Genetic Algorithm.

- [Poincaré Embeddings for Learning Hierarchical Representations](https://arxiv.org/abs/1705.08039)
  Maximilian Nickel, Douwe Kiela <br>
  NLP <br/>
  Summary at [blog](https://medium.com/towards-data-science/facebook-research-just-published-an-awesome-paper-on-learning-hierarchical-representations-34e3d829ede7)

- [Opinion Mining with Deep Recurrent Neural Networks](https://www.cs.cornell.edu/~oirsoy/files/emnlp14drnt.pdf)
  Ozan Irsoy and Claire Cardie <br>
  DL, RNN, NLP <br>
  Summary at [blog](https://medium.com/towards-data-science/paper-summary-opinion-mining-with-deep-recurrent-neural-networks-1fa791098fa5)

- [ A Strong Baseline for Learning Cross-Lingual Word Embeddings from Sentence Alignments](https://arxiv.org/abs/1608.05426)
  Omer Levy, Anders Søgaard, Yoav Goldberg <br>
  NLP <br/>
  Summary at [blog](https://medium.com/towards-data-science/cross-lingual-word-embeddings-what-they-are-af7987df6670)

- [Character-level Convolutional Networks for Text Classification](https://arxiv.org/abs/1509.01626)
  Xiang Zhang, Junbo Zhao, Yann LeCun <br>
  NLP, DL <br/>
  Summary at [blog](https://medium.com/@nishantnikhil/paper-summary-character-level-convolutional-networks-for-text-classification-6edf86e65106)

- [Using very deep autoencoders for content-based image retrieval](http://www.cs.toronto.edu/~fritz/absps/esann-deep-final.pdf)
  Krizhevsky, Alex and Hinton, Geoffrey E. <br>
  CV, DL <br/>
  Summary at [shortscience](http://www.shortscience.org/paper?bibtexKey=conf/esann/KrizhevskyH11#nishnik)

- [Learning semantic representations using convolutional neural networks for web search](https://pdfs.semanticscholar.org/8478/c0f46dd30ef7f4052145983d6d315c2e1f17.pdf)
  Shen, Yelong and He, Xiaodong and Gao, Jianfeng and Deng, Li and Mesnil, Grégoire <br>
  NLP, DL <br/>
  Summary at [shortscience](http://www.shortscience.org/paper?bibtexKey=conf/www/ShenHGDM14#nishnik)

- [Ask Me Anything: Dynamic Memory Networks for Natural Language Processing](https://arxiv.org/pdf/1506.07285v5.pdf)
  Ankit Kumar, Peter Ondruska, Mohit Iyyer, James Bradbury, Ishaan Gulrajani, Victor Zhong, Romain Paulus, Richard Socher <br>
  NLP, GRU, DL<br>
  Summary is in the next paper.

- [Dynamic Memory Networks for Visual and Textual Question Answering](https://arxiv.org/abs/1603.01417)
  Caiming Xiong*, Stephen Merity*, Richard Socher, MetaMind, Palo Alto, CA USA<br>
  NLP, GRU, DL<br>
  Initallly proposed Dynamic Memory Network has:
  1.) Input module: This module processes the input data about which a question is being asked into a set of vectors termed facts. This module consists of GRU over input words.<br>
  2.) Question Module: Represention of question as a vector. (final hidden state of the GRU over the words in the question)<br>
  3.) Episodic Memory Module: Retrieves the information required to answer the question from the input facts (input module). Consists of two parts- i.) attention mechanism ii.) memory update mechanism. To get it more intuitive: When we see a question, we only have the question in our memory(i.e. the initial memory vector == question vector), then based on our question and previous memory we pass over the input facts and generate a contextual vector (this is the work of attention mechanism), then memory is updated again based upon the contextual vector and the previous memory, this is repeated again and again.<br>
  4.) Answer Module: The answer module uses the question vector and the most updated memory from 3rd module to generate answer. (a linear layer with softmax activation for single word answers, RNNs for complicated answers)<br>
  Improved DMN+:
  The input module used single GRU to process the data. Two shortcomings: i.) The GRU only allows sentences to have context from sentences before them, but not after them. This prevents information propagation from future sentences. Therfore bi-directional GRUs were used in DMN+. ii.) the supporting sentences may be too far away from each other on a word level to allow for these distant sentences to interact through the word level GRU. In DMN+ they used sentence embeddings rather than word embeddings. And then used the GRUs to interact between the sentence embeddings(input fusion layer).
  For Visual Question Answering:
  Split the image into parts, consider them parallel to sentences in input module for text. Linear layer with tanh activation to project the regional vectors(from images) to textual feature space (for text based question answering they used positional encoding for embedding sentences). Again use bi-directional GRUs to form the facts.


- [Shallow Networks for High-Accuracy Road Object-Detection](https://arxiv.org/pdf/1606.01561v1.pdf)

  Khalid Ashraf, Bichen Wu, Forrest N. Iandola, Mattthew W. Moskewicz, Kurt Keutzer - <br>
  CV, CNN, DL<br>
  This paper emphasized on two things: 1.) Bigger input images lead to higher accuracy and 2.) Shallow models can deliver high accuracy.<br>

- [DeepLogo: Hitting Logo Recognition with the Deep Neural Network Hammer](https://arxiv.org/pdf/1510.02131v1.pdf)

  IANDOLA, SHEN, GAO, KEUTZER - 2015<br>
  CV, CNN, DL<br>
  Modification on GoogleLeNet for logo classification<br>

- [Training Support Vector Machines: an Application to Face Detection](http://web.mit.edu/rfreund/www/10.1.1.9.6021.pdf)

  Edgar Osunay, Robert Freund, Federico Girosiy - CVPR'97<br>
  CV, SVM<br>
  2 Generate the support vectors and then use decomposition algorithm (suggested by paper)<br>

- [Learning Deep Architectures for AI](http://papers.nips.cc/paper/4824-imagenet-classification-with-deep-convolutional-neural-networks.pdf)

  Yoshua Bengio - Technical Report 1312 <br>
  DL<br>
  2 The main conclusion of this section is that functions that can be compactly represented by a depth k architecture might require an exponential number of computational elements to be represented by a depth k − 1 architecture.<br>
  3 *TODO*<br>
  4 Distributed Representations are better than one hot representation in tackling the limitation of local generalization.<br>

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
  
