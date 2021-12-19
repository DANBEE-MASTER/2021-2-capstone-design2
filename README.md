## Self-Supervised Learning과 Domain Adaptation을 통한 식물에 대한 병충해 인식 연구
#### - 경희대학교 컴퓨터공학과 2004200157 박장선
#### - 지도 교수님 : &nbsp;최진우 교수님 <br/>

## 1. 연구 배경  <br/>
농업의 현대화가 많이 진행되었다고는 하나 특정 작물, 반복 동작에 대한 부분적인 기계화만 진행되었을 뿐 진정한 의미의 자동화 스마트팜은 이제서야 막 왕성한 성장 발전을 하고 있다. 또한 농업의 구조상 진입장벽이 높고, 경험 위주의 산업 형태로 핵심 인력의 연령이 높다보니, 젊은 기술자들의 신생 기술이 접목되어 다양한 연구가 진행되기에는 오랜 시간이 걸리고 있어, 다양한 연구 사례가 많지 없다. 위와 같은 이유로 기존 네트워크 모델이 한국에서 재배되는 작물 이미지 DATA에 대한 질병 진단에 있어 어떠한 결과를 보여주는지, 연구 결과에 따른 활용과 향후 계획을 연구를 통해 직접 확인해 보고자 한다. 

## 2. 목표  <br/>
다양한 질병에 대해서 풍부한 Data가 확보되어 있는 작물을 Source domain 이라고 정의하고, 
새로운 작물 Data를 Target domain 이라고 정의하여 Domain Adaptation 방법을 통해 질병 진단 인식 연구를 수행하면서, 성능을 극대화하기 위한 연구를 진행하고자 한다.

## 3. 관련 연구 <br/>
### 3-1. Unsupervised Domain Adaptation by Backpropagation <br/>
![Readme_Image_01](https://raw.githubusercontent.com/DANBEE-MASTER/2021-2-capstone-design2/main/README_Image/Readme_Image_01.gif) <br/>
Source Domain과 Target Domain를 유사하게 학습하기 위하여 Backpropagation의 구조에 Gradient reversed layer를 사용하여 Domain label을 잘 분류할 수 없도록 한다. 즉 label predictor은 label을 잘 맞추는 방향으로 업데이트 하고, domain classifier는  domain을 잘 맞추는 방향으로 업데이트 하지만 gradient reversal layer을 통해 domain을 잘 맞추는 방향과 반대 방향으로 업데이트 하여 source domain과 target domain의 차이를 해결한다.

## 4. 설계 및 연구 <br/>
### 4-1. AI HUB Data set 재구성 <br/>
![Readme_Image_02](https://raw.githubusercontent.com/DANBEE-MASTER/2021-2-capstone-design2/main/README_Image/Readme_Image_02.png) <br/>
AI HUB 는 한국지능정보사회진흥원의 사업결과로 지능정보산업 인프라 조성사업으로 추진한 AI 학습용 데이터를 공개한 곳으로 이곳의 데이터를 활용하여 동일 질병 기준으로 [표1]과 같이 Data set을 재구성하여 문제를 정의하였다. 
### 4-2. DA Model 에 따른 네트워크 성능 측정 <br>
![Readme_Image_03](https://raw.githubusercontent.com/DANBEE-MASTER/2021-2-capstone-design2/main/README_Image/Readme_Image_03.png) <br/>

SOURCE ONLY : Source data 만을 사용하여 학습한 뒤 Target data로 성능 측정<br>
TRAIN ON TARGET : Target data 로 학습하고, Target data 성능 측정<br>
[표2] DA 모델에 따른 네트워크 성능 측정 결과<br>
<br>
## 5. 결론 및 향후 연구 <br/>
본 논문에서는 Label이 존재하는 고추 작물 Data를 통해 Domain Adaptaiton 모델을 적용하여 여러 작물의 질병 진단 인식 연구를 시도하였다. 본 연구를 통해 DA 모델 구조에 따른 네트워크 성능 차이. 네트워크 성능 극대화 방법을 보임으로써, 스마트팜 작물 질병 진단을 위한 효과적인 방법으로 사용 가능할 것이라고 기대한다.                                     
