# GNN (Graph Neural Network) 
* July 12 (monday)


* GNN 은 그래프의 노드와 엣지를 학습해서 사용한다.
* 머신러닝 학습의 과정 및 흐름에 논리를 뒷받침할 수 있는 뉴럴 네트워크다. (다른 알고리즘은 훈련 데이터의 feature을 통해서 학습되는 이유를 파악하지는 못한다)
* 뉴럴네트워크 학습을 통해 노드에서 state을 얻는다. 
  * 이때 방법은?
    1. Recurrent Mechanism: 시간 측면에서 한 번에 state 을 업데이트 하는 것.
    2. Banach Fixed-Point Theorem : l (label)끼리 수렴하는 것. weight matrix을 곱해서 feed forward 학습시키고 w를 업데이트 한다. 

* Almeida - Pineda algorithm 
  * forward, gradient 계산 시 하나로 수렴하는 데 마지막 state만 확인한다. 
  * 참고) RNN은 hidden state이 보장이 안되므로 x

* 수식 
  * n : node #
  * ln : 자신의 label 
  * co[n] : edge의 label 
  * ue[n] : edge의 state 
  * out gw (xn, ln) : (업데이트되는 state 값)+ (고정된 label 값)을 인자로 받아 아웃풋을 출력한다.

* 계산량이 많고 비효율적이어서 이를 개선하려고 나온 대안: GCN 등
  * GCN : 인접행렬을 사용함.
  * GNN의 node 을 인자로 가져오는 측면을 응용했다. 
  * 레이어 1개마다 wegith matrix가 정해져서 업데이트 되고 
  * MLP (fully-connected layout)이 사용된다. 

* GNN의 응용 takss
  * VQA : 이미지(책상 위에 물건)을 보고 무엇인지 text로 답변
  * Recommended System : 추천시스템 
  * 분자식 입력 - 향 예측 
  * Graph Transformer (NLP) 
