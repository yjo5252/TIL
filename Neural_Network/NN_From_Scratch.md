## 뉴럴 네트워크 파이썬으로 코드 제작

<Implementing a Neural Network from Scratch in Python – An Introduction>
* 논문 파이썬 코드 실습하기 (2020.12.19 토요일)

* [yjo5252/NN_from_scratch.ipynb](https://github.com/yjo5252/Neural_Network/blob/main/NN_from_scratch.ipynb)
* [블로그 | Implementing a Neural Network from Scratch in Python – An Introduction](http://www.wildml.com/2015/09/implementing-a-neural-network-from-scratch/)
* [깃허브 실습 코드 | All of the code is available as an iPython notebook on Github](https://github.com/dennybritz/nn-from-scratch). 
### Exercises
Here are some things you can try to become more familiar with the code:

1. Instead of batch gradient descent, use minibatch gradient descent (more info) to train the network. Minibatch gradient descent typically performs better in practice.
2. We used a fixed learning rate \epsilon for gradient descent. Implement an annealing schedule for the gradient descent learning rate (more info).
1. We used a \tanh activation function for our hidden layer. Experiment with other activation functions (some are mentioned above). Note that changing the activation function also means changing the backpropagation derivative.
1. Extend the network from two to three classes. You will need to generate an appropriate dataset for this.
1. Extend the network to four layers. Experiment with the layer size. Adding another hidden layer means you will need to adjust both the forward propagation as well as the backpropagation code.
