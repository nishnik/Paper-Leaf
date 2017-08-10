- [Using very deep autoencoders for content-based image retrieval](http://www.cs.toronto.edu/~fritz/absps/esann-deep-final.pdf)
  Krizhevsky, Alex and Hinton, Geoffrey E. 
  CV, DL <br/>
  Summary at http://www.shortscience.org/paper?bibtexKey=conf/esann/KrizhevskyH11#nishnik

- [Learning semantic representations using convolutional neural networks for web search](https://pdfs.semanticscholar.org/8478/c0f46dd30ef7f4052145983d6d315c2e1f17.pdf)
  Shen, Yelong and He, Xiaodong and Gao, Jianfeng and Deng, Li and Mesnil, Grégoire 
  NLP, DL <br/>
  Summary at http://www.shortscience.org/paper?bibtexKey=conf/www/ShenHGDM14#nishnik

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
  
