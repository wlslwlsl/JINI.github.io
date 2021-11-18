---
date: 2021-11-16
title: "MicroSoft Azure Machine Learning - Jupyter Notebook"
subtitle: "AutoML : MicroSoft Azure Machine Learning - Jupyter Notebook"
categories: AutoML
tags:
  - AutoML
  - 자동화
  - MS
  - jupyter
  - Azure
# 목차
toc: true  
toc_sticky: true 
---


## Azure AutoML 무료 계정 생성 URL
[계정만들기](https://azure.microsoft.com/ko-kr/free/search/?&ef_id=Cj0KCQiA6t6ABhDMARIsAONIYyyEgVPa8oL6tWphXpORyHS0f-qiffy41o3VvuoTX8WFpCtQbmtfQVYaAjqREALw_wcB:G:s&OCID=AID2100068_SEM_Cj0KCQiA6t6ABhDMARIsAONIYyyEgVPa8oL6tWphXpORyHS0f-qiffy41o3VvuoTX8WFpCtQbmtfQVYaAjqREALw_wcB:G:s&gclid=Cj0KCQiA6t6ABhDMARIsAONIYyyEgVPa8oL6tWphXpORyHS0f-qiffy41o3VvuoTX8WFpCtQbmtfQVYaAjqREALw_wcB)

→ 무료 계정을 생성하고 30일간 실습을 진행할 수 있음


## 실습 참고 URL - 유료버전

[참고사이트](https://docs.microsoft.com/ko-kr/azure/machine-learning/how-to-use-automated-ml-for-ml-models)


## 실습 process

Azure Machine Learning을 사용하여 실습

Azure Machine Learning Studio에 로그인 후 해당 구독과 직접 만든 작업 영역을 선택한 가정에서 진행


## <span style="color:#9BC3FF; font-weight:bold"> Jupyter Notebook </span>


### 1. Notebook 선택


![process_1]({{https://github.com/wlslwlsl/wlslwlsl.github.io}}/assets/AutoML/j1.png){:.aligncenter}


→ 왼쪽에 있는 Notebook에서 샘플탭 선택

→ tutorials를 복제하여 자기 경로에 저장

- 1.20.0 : Python SDK의 현재 릴리스


### 2. 복제된 Notebook 열기(컴퓨팅 인스턴스 설정)

→ Automl을 실행할 데이터를 클릭한다.

- sample 폴더에서는 Notebook을 볼 수 있지만 실행은 불가능

- 실행하기 위해서는 파일 섹션에 복제하여 사용해야 함


* 진행하고자 하는 파일을 선택하기

*tutorials/regression-automl-nyc-taxi-data/regression-automated-ml.ipynb* 파일 선택

![process_2]({{https://github.com/wlslwlsl/wlslwlsl.github.io}}/assets/AutoML/j2.png){:.aligncenter}

→ 컴퓨팅을 선택하여 실행하면 된다.

→ 컴퓨팅이 없다면 새 컴퓨팅을 추가해준다.(무료 계정 생성시 주어진 크레딧으로 결제되는 것 같음)


### 3. 모델 학습

→ 패키지 가져오기 : 필요한 python 패키지를 불러온다.

> numpy, plt 등


#### 1) 데이터 준비

→ Spark 이외의 환경에서 작업하는 경우 Open Datasets는 큰 데이터 세트와 관련된 MemoryError를 방지하기 위해 특정 클래스를 사용하여 한 번에 1개월 분량의 데이터만 다운로드할 수 있다.

→ 택시 데이터를 다운로드하려면 데이터 프레임의 급격한 증가를 방지하기 위해 한 번에 1개월 분량씩 반복해서 가져오고 각 월 데이터에서 레코드 2000개를 임의로 샘플링

→ 필요하지 않는 열을 제거한다.

→ 이상 값 및 불필요한 열 제거한다.

→ 학습 및 테스트 데이터로 분할한다.


#### 2) 자동 모델 학습

→ 자동으로 모델을 학습하기 전 수행해야할 부분

- 실험 실행을 위한 설정 정의 학습 데이터를 구성에 연결하고, 학습 프로세스를 제어하는 설정을 수정

- 모델 튜닝을 위한 실험 제출 실험을 제출한 후 프로세스는 다른 기계 학습 알고리즘 및 하이퍼 매개 변수 설정을 반복하여 정의된 제약 조건을 준수

- 정확도 메트릭을 최적화하여 가장 적합한 모델을 선택


**학습설정 정의**

| **속성** | **값** | **설명** |
|:---:|---|---|
| iteration_timeout_minutes |10|각 반복에 대한 분 단위 시간 제한 각 반복에 더 많은 시간이 필요한 대규모 데이터 세트의 경우 이 값을 늘림|
| experiment_timeout_hours |0.3|실험을 종료하기까지 모든 반복 조합에 소요되는 최대 시간(시간)|
| enable_early_stopping |True|점수가 단기간에 개선되지 않는 경우 조기 종료를 활성화하는 플래그|
| primary_metric |spearman_correlation|최적화하려는 메트릭 → 이 메트릭에 따라 최적화된 모델이 선택|
| 기능화 |auto|auto를 사용하면 실험은 입력 데이터를 전처리할 수 있다(누락 데이터 처리, 텍스트를 숫자로 변환 등)|
| verbosity |logging.INFO|로깅 수준을 제어|
| n_cross_validations |5|유효성 검사 데이터가 지정되지 않은 경우 수행할 교차 유효성 검사 분할 수|

#### 3) 학습

→ 작업 영역에 실험 개체를 만든다.

→ 실험은 개별 실행에 대한 컨테이너 역할

→ 정의된 automl_config 개체를 실험에 전달하고 출력을 True로 설정하여 실행하는 동안 진행률을 확인

→ 실험을 시작한 후에 표시되는 출력은 실험이 실행됨에 따라 실시간으로 업데이트

- 각 반복의 경우 모델 유형, 실행 지속 및 학습 정확도가 표시

- 필드 BEST는 메트릭 유형에 따라 최적의 실행 학습 점수를 추적


#### 4) 최적 모델을 검색하여 테스트를 진행



참고 : [MachineLearningNotebooks](https://github.com/Azure/MachineLearningNotebooks)