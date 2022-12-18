## 2022- AIMMO X AIFFEL Project

# 🚚 [Data-centric Task] 환경조건별 객체 탐지성능 강건화를 위한 자율주행 학습데이터셋 구성비 도출 프로젝트
#### [Data-centric Task] Self-driving Dataset Composition Ratio Derivation Project for Robust Object detection

Project Name : 불꽃주행 
Project execution period : 2022.11 ~ 2022.12

# Index
1. Description
2. Environment
3. Files
4. Data
5. Project
6. Result
7. Feedback
8. Member
   
## 1. Description
---
![image](https://user-images.githubusercontent.com/108614874/206998885-cd327b15-e806-42f0-b502-04f1df61854d.png)

AI 데이터 기업 **AIMMO** 와 AI 혁신학교 **AIFFEL** 이 협업하여 진행한 Data-centric AI 개발 방법론 프로젝트입니다.

**AIMMO 기업소개**
전 세계 인공지능과 관련된 문제를 해결하기 위해 맞춤형 인공지능 데이터를 제공하는 스타트업입니다. AIMMO 자율주행팀에서는 Data-centric AI 개발 방법론에 기반해 자율주행 학습용 Data 생산 및 서비스를 제공하며 최적화, 강건화 컨셉을 바탕으로 자율주행 Dataset을 검증 진행중입니다. 

**프로젝트 개요**
모델을 고정한 데이터 중심의 AI 개발 방법론을 이용, 주 / 야 / 맑음 / 비 각 환경조건에서 객체 탐지성능 편차를 최소화 할 수 있는 학습 데이터셋의 구성비를 도출하고 테스트 데이터의 추론 결과에 대해 구성비 선정 결과 / 근거 / 결론을 정리했습니다.

## 2. Environment  
* Python 3.9
* Pytorch 1.7.1
* Google Colab, jupyter notebook(GPU : Tesla_t4), GCP(GPU : Tesla_v100)

## 3. Files
`/runs/final_composition_ratio.ipynb` : 가장 결과가 좋았던  구성비의 Jupyter Notebook  
`/runs/train.txt` : 학습에 사용된 이미지 목록  
`/runs/best.pt` : best 가중치파일  

## 4. Data
AIMMO 원본 데이터 : 총 7.8만장 png + json 쌍 사용

## 5. Project 

## 6. Result
**Preprocessing**
* 원본 데이터에서 잘림, 가림이 심한(75%이상) 데이터를 제외
* 라벨링 일관성 오류 데이터 제외

**(time : 주간, 야간, 일몰 weather : 맑음, 흐림, 비)**
* 위 meta 정보를 기반으로 구성비를 나눈 실험 결과를 기반으로 이미지 개수를 조절하거나 구성비를 조절하는 실험 진행
![image](https://user-images.githubusercontent.com/108614874/207001283-79741e2a-ba11-4ee1-99c6-ec8e73b001f7.png)

### 최종 구성비 
![image](https://user-images.githubusercontent.com/108614874/207000994-8a86e8e8-5979-4017-b693-7a1fc52f4ef4.png)
Test Data 총 56560장 사용, Test **mAP50 기준 0.788** 기록

## 7. Feedback
* 회고
	* 모델튜닝  
	보행자와 같은 작은 객체에 대한 모델튜닝을 못해서 아쉬웠다.
	augmentation이나 focal loss gamma값과 같은 하이퍼파라미터 튜닝을 잘 못해서 아쉬웠다.
	* 구성비 선정의 어려움  
	구성비 선정에 어려움이 있어 시간이 많이 소요되어 아쉽.
	* 데이터셋 이해의 중요성  
	다양한 feature (도로 타입, 역광 여부, 속도 등)가 있었지만 날씨, 시간대만 사용해서 실험했기 때문에 아쉬웠다. 실험결과를 토대로 다른 feature들을 변화시키며 실험했더라면 더 좋은 결과가 나왔을 수도
	* 협업 시 파일 정리의 중요성  
	프로젝트 초반부터 파일정리를 잘 해보자고 시작했으나 프로젝트가 진행될수록 잘 안되고 어수선했음. 효율적인 파일 정리에 대해 생각해보게 됨
	* 대용량 데이터셋 다운/업로드 어려움과 시간이 지체됨  
	cv task 특성상 데이터셋 규모가 큰데 대용량 파일을 다운로드, 업로드 하는 과정에 시간이 많이 소요됐다. 이 시간만 줄였더라면 구성비 실험을 더 많이 할 수 있지 않았을까나
	* 코드작성의 어려움  
	다른사람들도 한눈에 알아볼 수 있는 코드를 짜는게 힘들었다. 어떻게 코드를 완성할 수는 있지만 미래에 문제가 될 수 있는 다른 요인들을 미리 고려한 코딩은 쉽지 않았다.


* Aimmo측 feedback (정리필요)  
	-   작은객체 인식 성능 향상 위해 다양한 방법을 고려해봤어도 좋았을 것.
		- 리소스는 제한적인 경우가 많으니    
	-   클래스 단일화 기준, truncation, occlusion 75%이상까지 제외한 기준과 같은 요소에서 학습결과를 기반으로 한 논리적인 근거가 있었으면 더 좋았을 것.
	-   데이터 분포를 나눌 때 이미지 기준 vs 객체 기준
	-   데이터 분석이 가장 중요, 객체 분포에서나 어떤것이 부족한지 알기 위해서는 데이터 분석의 중요성이 계속 커지고 있다.
	-   영상을 프레임 단위로 자른 이미지므로, 프레임 간 유사도가 자칫하면 높아질 수 있다.
   		- 랜덤하게 뽑아 랜덤하게 검증하면 결과도 랜덤하게 나온다.
		- solution 1) test 환경과 비슷하게 하려면 하나의 scene을 통째로 validation 데이터로 사용하는 방법.
		- solution 2) **meta정보**를 기준으로 추출하는 방법. 학습, 평가 구성이 메타기준으로 고른 분포를 갖도록 하는 것이 좋다.

## 8. Member
| Name           | Role                                                              |                           Github                           |         Email         |
|:----------------:|-------------------------------------------------------------------|:----------------------------------------------------------:|:---------------------:|
| 김동욱 (Leader) | 총괄 및 모델링                                                    | [@dong-uk-kim97](https://github.com/dong-uk-kim97)         |                       [✉](kdw24739577@gmail.com)|
| 김건희         | YOLOv5 구동 여부 확인 및 모델링 🛠                                 | [@xpelqpdj0422](https://github.com/xpelqpdj0422)           |                       [✉](xpelqpdj0422@gmail.com)|
| 김용식         | 작업 보조 및 지원 / 모델 구동                                     | [@aivrm](https://github.com/aivrm)                         |                [✉](a01023820775@gmail.com)         |
| 모예송         | 데이터 전처리 / EDA / 데이터 분석 / 가설 수립 / Notion 수리공 👩🏻‍🔧 | [@yesong98](https://github.com/yesong98)                   |                       [✉](yesongmo98@gmail.com)|
| 이주미         | 데이터 전처리 / EDA / 데이터 분석 / 가설 수립 / Notion 수리공 👩🏻‍🔧 | [@itchyfeet-patient](https://github.com/itchyfeet-patient) | [✉](jumi.lee106@gmail.com) |
