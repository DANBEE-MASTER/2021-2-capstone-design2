## Self-Supervised Learning과 Domain Adaptation을 통한 식물에 대한 병충해 인식 연구
#### - 경희대학교 컴퓨터공학과 2004200157 박장선
#### - 지도 교수님 : &nbsp;최진우 교수님 <br/>

## 1. 연구 배경  <br/>
농업의 현대화가 많이 진행되었다고는 하나 특정 작물, 반복 동작에 대한 부분적인 기계화만 진행되었을 뿐 진정한 의미의 자동화 스마트팜은 이제서야 막 왕성한 성장 발전을 하고 있다. 또한 농업의 구조상 진입장벽이 높고, 경험 위주의 산업 형태로 핵심 인력의 연령이 높다보니, 젊은 기술자들의 신생 기술이 접목되어 다양한 연구가 진행되기에는 오랜 시간이 걸리고 있어, 다양한 연구 사례가 많지 없다. 위와 같은 이유로 기존 네트워크 모델이 한국에서 재배되는 작물 이미지 DATA에 대한 질병 진단에 있어 어떠한 결과를 보여주는지, 연구 결과에 따른 활용과 향후 계획을 연구를 통해 직접 확인해 보고자 한다. 

## 2.목표  <br/>
다양한 질병에 대해서 풍부한 Data가 확보되어 있는 작물을 Source domain 이라고 정의하고, 
새로운 작물 Data를 Target domain 이라고 정의하여 Domain Adaptation 방법을 통해 질병 진단 인식 연구를 수행하면서, 성능을 극대화하기 위한 연구를 진행하고자 한다.

## 3. 관련 연구 <br/>
#### 3-1 .Unsupervised Domain Adaptation by Backpropagation <br/>
![Readme_Image_01](https://raw.githubusercontent.com/DANBEE-MASTER/2021-2-capstone-design2/main/README_Image/Readme_Image_01.png) <br/>
Source Domain과 Target Domain를 유사하게 학습하기 위하여 Backpropagation의 구조에 Gradient reversed layer를 사용하여 Domain label을 잘 분류할 수 없도록 한다. 즉 label predictor은 label을 잘 맞추는 방향으로 업데이트 하고, domain classifier는  domain을 잘 맞추는 방향으로 업데이트 하지만 gradient reversal layer을 통해 domain을 잘 맞추는 방향과 반대 방향으로 업데이트 하여 source domain과 target domain의 차이를 해결한다.
