# Unsupervised domain adaptation을 이용한 작물 질병 진단 인식 연구
#### - 경희대학교 컴퓨터공학과 2004200157 박장선
#### - 지도 교수님 : &nbsp;최진우 교수님 <br/> <br/> <br/>

## 1. 연구 배경  <br/>
농업의 현대화가 많이 진행되었다고는 하나 특정 작물, 반복 동작에 대한 부분적인 기계화만 진행되었을 뿐 진정한 의미의 자동화 스마트팜은 이제서야 막 왕성한 성장 발전을 하고 있다. 또한 농업의 구조상 진입장벽이 높고, 경험 위주의 산업 형태로 핵심 인력의 연령이 높다보니, 젊은 기술자들의 신생 기술이 접목되어 다양한 연구와 서비스가 진행되기에는 오랜 시간이 걸리고 있어, 아직 작물에 대한 질병 Image 검색 서비스 조차 없는 상황이다. <br/>
특히 작물에 대한 질병 예측에 관해서는 농업에 대한 경험이 풍부하더라고 신규 작물, 익숙지 않은 작물인 경우 같은 질병이더라도 작물의 형태, 재배 환경에 따라 다르게 보일 수 있기 때문에 정확한 질병을 진단하기가 쉽지 않다. 위와 같은 이유로 확보되어 있는 특정 작물에 대한 label Image data를 통해 classifier를 만든다고 하여도, class는 같지만 다른 작물을 분류하게 되면 class 수에 따른 random 결과값이 나오거나 그보다 못한 성능이 못한다. <br/>
작물의 종류가 너무 많아 모든 작물에 대한 Data 확보가 현실적으로 불가능하고 작물 질병에 대한 labeling 또한 쉽지 않거나 생소한 질병인 경우 질병의 label 조차 알 수 없다는 가장 큰 문제가 있다. 이에 따라 ‘작물의 종류는 많지만 질병은 같다’라는 작물의 특징을 이용하여 확보되어 있는 특정 작물에 대한 label Image data를 통해 다른 작물의 질병명을 판단함에 있어 성능을 높이고자 하는 연구를 수행하고자 한다. <br/>

## 2. 연구 목표  <br/>
AI HUB의 작물 질병 진단 Image를 재구성하여 label이 있는 Data set을 Source domain, label이 없다고 가정하는 Data set을 Target domain으로 구분하여 Data set을 class에 수에 따라 다양하게 재정의한다. 이후 Base model로 사용할 네트워크 모델을 찾고, Source domain을 사용하여 학습한 뒤 Target domain에 대한 성능 측정을 한다. 
이후 Domain Adaptation의 모델 중 하나인 DANN 모델을 통해 Target domain에 대한 성능 차이를 확인하고, Target domain 에서의 성능을 극대화하기 위해 SimCLR 사전학습모델(Pre-trained model)에 따른 성능 차이 연구를 수행한다. <br/>

## 3. 관련 연구 <br/>
도메인 적응(Domain Adaptation, DA)은 영역(Domain)이 다르지만, Class가 비슷할 때, 도메인의 차이를 좁히는 것으로 Source domain에서 학습된 classifier를 Transfer Learning 하여 Target domain을 이용할 수 있게 해준다. 이때 Source domain과 Target domain의 차이를 다음과 같은 방법으로 해결할 수 있다
  
### Unsupervised Domain Adaptation by Backpropagation <br/>
![Readme_Image_01](https://raw.githubusercontent.com/DANBEE-MASTER/2021-2-capstone-design2/main/README_Image/Readme_Image_01.gif) <br/>
Source domain과 Target domain의 domain shift를 좁혀주기 위해 Backpropagation의 구조에 Gradient reversed layer를 사용하여 domain label를 잘 분류할 수 없게 만들어 Source domain과 Target domain을 유사하게 만들어준다. 즉 label predictor는 label을 잘 맞추는 방향으로 loss를 업데이트하고, domain classifier는 domain을 잘 맞추는 방향으로 loss를 업데이트 하지만 gradient reversal layer을 통해 domain을 잘 맞추는 방향과 반대 방향으로 업데이트 하여 Source domain과 Target domain의 domain shift 차이를 해결하여 domain을 유사하게 만들어준다. [1]

## 4. 실험 환경 및 성능 확인 <br/>
### 4-1. AI HUB Data set 재구성 <br/>
AI HUB 는 한국지능정보사회진흥원의 사업결과로 지능정보산업 인프라 조성사업으로 추진한 AI 학습용 데이터를 공개한 곳으로 이곳의 데이터를 활용하여 동일 질병 기준으로 [표1]과 같이 Data set을 재구성하여 문제를 정의하였다. 
![Readme_Image_02](https://raw.githubusercontent.com/DANBEE-MASTER/2021-2-capstone-design2/main/README_Image/Readme_Image_02.png){:width="80%" height="80%"} <br/>

### 4-2. DA Model 에 따른 네트워크 성능 측정 <br>
<img src="https://raw.githubusercontent.com/DANBEE-MASTER/2021-2-capstone-design2/main/README_Image/Readme_Image_03.png" width="80%" height="80%">
※ SOURCE ONLY : Source data을 사용하여 학습한 뒤 Target data 성능 측정 <br/>
※ TRAIN ON TARGET : Target data로 학습하고, Target data 성능 측정 <br/>
<br>

## 5. 결론 및 추후연구 <br/>
본 연구에서는 Domain Adaptaiton 기술 중 하나인 DANN 모델을 이용하여 label이 없는 작물 Data set인 Target domain에 대한 작물 질병 분류 네트워크 모델 성능을 확인해보았다. <br/>
Base model 으로는 Noise가 많은 Image에 별다른 이미지처리 없이도 Xception 모델에 Imagenet weights를 사용한 경우 90% 이상의 네트워크 성능을 확인하였으며, Source domain을 사용하여 학습한 뒤 Target domain으로 성능을 측정한 결과 ‘Binary classification’의 ‘고추 → 단호박’ Data set에 대해서는 67.2%가 나왔지만, SimCLR 모델을 통해 만든 사전학습모델(Pre-trained model)에 DANN을 사용하여 87.5% 까지 향상된 결과가 나왔음을 확인할 수 있었다. <br/>
작물마다 Binary classification 문제로 정의하면 질병 초기에 질병 유무 진단을 바로 확인할 수 있고 이를 통해 작물 질병 이미지 검색 서비스 가능 등의 기대효과를 확인할 수 있었다. 하지만 Domain에 다양한 작물이 존재하는 경우 질병이 아닌 작물의 구분을 학습하려는 경향이 있기 때문에 작물에 대한 Debiasing 필요성에 대해 제기한다. <br/>                
