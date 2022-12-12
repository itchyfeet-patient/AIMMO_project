### 2022- AIMMO X AIFFEL Project

## 🚚 [Data-centric Task] 환경조건별 객체 탐지성능 강건화를 위한 자율주행 학습데이터셋 구성비 도출 프로젝트
##### [Data-centric Task] Self-driving Dataset Composition Ratio Derivation Project for Robust Object detection

Project Name : 불꽃주행 
Project execution period : 2022.11 ~ 2022.12

## Index
1. Description
2. Environment
3. Files
4. Data
5. Result
6. Member
   
### 1. Description
---
AI 데이터 기업 **AIMMO** 와 AI 혁신학교 **AIFFEL** 이 협업하여 진행한 Data-centric AI 개발 방법론 프로젝트입니다.

**AIMMO 기업소개**
전 세계 인공지능과 관련된 문제를 해결하기 위해 맞춤형 인공지능 데이터를 제공하는 스타트업입니다. AIMMO 자율주행팀에서는 Data-centric AI 개발 방법론에 기반해 자율주행 학습용 Data 생산 및 서비스를 제공하며 최적화, 강건화 컨셉을 바탕으로 자율주행 Dataset을 검증 진행중입니다. 

**프로젝트 개요**
모델을 고정한 데이터 중심의 AI 개발 방법론을 이용, 주 / 야 / 맑음 / 비 각 환경조건에서 객체 탐지성능 편차를 최소화 할 수 있는 학습 데이터셋의 구성비를 도출하고 테스트 데이터의 추론 결과에 대해 구성비 선정 결과 / 근거 / 결론을 정리했습니다.

### 2. Environment  
* Python 3.9
* Pytorch 1.7.1
* Google Colab, jupyter notebook(GPU : Tesla_t4), GCP(GPU : Tesla_v100)

### 3.  Files
`/Runs` : 가장 결과가 좋았던  구성비의 Jupyter Notebook (`final_composition_ratio.ipynb`)

### 4.  Data
AIMMO 원본 데이터 : 총 7.8만장 png + json 쌍 사용

### 5.  Result
**Preprocessing**
* 원본 데이터에서 잘림, 가림이 심한(75%이상) 데이터를 제외
* 라벨링 일관성 오류 데이터 제외

**(time : 주간, 야간, 일몰 weather : 맑음, 흐림, 비)**
* 위 meta 정보를 기반으로 구성비를 나눈 실험 결과를 기반으로 이미지 개수를 조절하거나 구성비를 조절하는 실험 진행



### 6.  Member
| Name           | Role                                                              |                           Github                           |         Email         |
|:----------------:|-------------------------------------------------------------------|:----------------------------------------------------------:|:---------------------:|
| 김동욱 (Leader) | 총괄 및 모델링                                                    | [@dong-uk-kim97](https://github.com/dong-uk-kim97)         |                       [✉](kdw24739577@gmail.com)|
| 김건희         | YOLOv5 구동 여부 확인 및 모델링 🛠                                 | [@xpelqpdj0422](https://github.com/xpelqpdj0422)           |                       [✉](xpelqpdj0422@gmail.com)|
| 김용식         | 작업 보조 및 지원 / 모델 구동                                     | [@aivrm](https://github.com/aivrm)                         |                [✉](a01023820775@gmail.com)         |
| 모예송         | 데이터 전처리 / EDA / 데이터 분석 / 가설 수립 / Notion 수리공 👩🏻‍🔧 | [@yesong98](https://github.com/yesong98)                   |                       [✉](yesongmo98@gmail.com)|
| 이주미         | 데이터 전처리 / EDA / 데이터 분석 / 가설 수립 / Notion 수리공 👩🏻‍🔧 | [@itchyfeet-patient](https://github.com/itchyfeet-patient) | [✉](jumi.lee106@gmail.com) |
