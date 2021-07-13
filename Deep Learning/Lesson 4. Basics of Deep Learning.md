# 4단원 Basics of Deep Learning 
 Deep Learning for NLP and Speech Recognition, Springer

### 1. Linear Support vector가 뭐야 ? 

    gradient 반응이 얼마에 한번 업데이트 되고 
    크면 비례해서 많이 업데이트 되고 작으면 적게 업데이트 될테니까 변화가 없을때까지. 
    converge 할 때까지 속도 나타냄.

### 2. Forward Propagation :입력에 대한 모델의 결과 계산
    feed forward neural network 

### 3. Universal Approximation Theorem

    한 개의 히든 레이어를 가진 뉴럴 네트워크를 이용해 어떤 함수든 근사시킬 수 있다.

## How to train a Neural Network ? 
  * activation functions 
  * error metrics 
  * optimization methods

### 4. Activation Function : 출력값을 결정하는 함수 [0,1]

### 5. 미분 가능해야하는 이유가 뭐야? 
    학습이 되려면 기울기가 미분한 값에 backpropagation을 해야하므로. 
    학습을 할 때 back propagation 과정에서 learning rate을 미분가능해야 SED 에 쓸 수 있다.

### 5-1. 비슷한 게 뭐지 ? Sigmoid, Tahh (탄취, ReLU)

### 6. Softmax가 뭐야? 왜 사용해?

    Class Figuration을 하려면 일정한 threshold을 넘어야 해서 사용한다. 
    그 클래스에 속하는지 아닌지 알기 위해서. 

### 6-1. Low Softmax는 뭐야? 왜 사용해? 

    underflow issue를 방지하기 위해서. 너무 작은 값을 처리하기 위해서. 

### 6-2. 왜 log를 이용해서 처리하면 되지? 

    엄청 작은 값이 된다. 입력값이 작으면 작을수록 출력값 크기가 커진다. 

### 7. Loss Function 왜 정의해? 

    Loss Function을 정의해야 Optimizer을 사용할 수 있다. 
    Loss 값이 가장 작아지는 global minimum 값을 찾아야 한다. 

### 7-1. 다양한 값을 정의하는 이유는? 
    outlier에 의해서도 영향을 받으면 안되고 특성이 다르니까. 데이터셋에 따라 다르다. 

### 7-2. convex function (볼록함수)
    gradient 가 0 벡터가 되면 글로벌 미니멈이라는 의미이다. 
    convex가 아닌 경우에는 로컬 미니멈인 경우에도, gradient=0이다. 

### 7-3. gradient descent 계산하는 이유: 미니멈을 찾기 위해서. 

### 7-4. 교재의 예제는 simplify하면 convex있지만 실질적으로는 convex 없다.

### 8. MLP (Multi Layer Perceptron) Classifier
     Feed-forward neural networks
