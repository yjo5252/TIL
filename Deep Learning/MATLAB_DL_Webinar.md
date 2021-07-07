# MATLAB_DL_Webinar

## 1. 영상 분석을 위한 딥러닝 
(2021.7.7) [영상 분석을 위한 딥러닝 유튜브](https://youtu.be/Xv8sDZq6_jk)

[MATLAB Deep Learning - GitHub](https://github.com/matlab-deep-learning)

### 주제: How to Fine-tune Computer Vision Models using MATLAB : 
* Transfer Learning :학습하는 방법을 보여줌.

* 딥러닝 모델을 만들 때 접근법
  * 각 레이어를 직접 설계하고 학습을 시킨다. (예를 들어. CNN(Convolutional Neural Network))
  * Pre-trained Model 을 가져와서 Fine-Tuning 시킨다: 네트워크의 웨이트들을 fine-tuning 시킨다.  
    * Filter size + Number of Filters (= classes), final Classification 레이어를 수정한다.

* [DeepNetworkDesigner](https://www.mathworks.com/help/deeplearning/gs/get-started-with-deep-network-designer.html)
  * : 딥뉴럴네트워크를 GUI로 구현할 수 있음. 
  * : classification 결과를 확인할 수 있음.

* Image Classification 
  * 영상과 이미지에 라벨링하여 분류를 하는 딥러닝 모델

* Object detection
  * pre-trained 된 YOLO3로 구현
  * 예제) 마스크 디텍션을 만들었다. 소스 (마스크 데이터셋, bounding information) 

* Segmentation Detection
  * pixel-by-pixel. 배경, 사물의 categorical detection
  * 예제) 철강 영상, 다리와 댑, 건설공간의 하수 높이, 조립의 선들을 예측 프로젝트 

* 사용되는 분야: 이미지 프로세싱, 컴퓨터 비전, 라이더 디텍션
