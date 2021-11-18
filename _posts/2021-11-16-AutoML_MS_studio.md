---
date: 2021-11-16
title: "MicroSoft Azure Machine Learning - Studio"
subtitle: "AutoML : MicroSoft Azure Machine Learning - Studio"
categories: AutoML
tags:
  - AutoML
  - 자동화
  - MS
  - Azure
# 목차
toc: true  
toc_sticky: true 
---


## <span style="color:#9BC3FF; font-weight:bold"> 스튜디오(자동화된 ML) </span>


* 데이터 셋 : bankmaketing_train.csv*

→ 스튜디오를 통해 AutoML 실습 가능

![studio_1]({{https://github.com/wlslwlsl/wlslwlsl.github.io}}/assets/AutoML/s1.png){:.aligncenter}

→ 왼쪽 섹션에서 자동화된 ML을 클릭 후 새로운 자동화 ML을 클릭한다.


## 1. 데이터 생성

**1) 기본 정보**

→ 양식에서 데이터 집합에 고유한 이름을 지정하고 설명(선택 사항)을 제공

![studio_2]({{https://github.com/wlslwlsl/wlslwlsl.github.io}}/assets/AutoML/s2.png){:.aligncenter}

**다음**을 선택하여 **데이터 저장소 및 파일 선택 양식**을 클릭.

→ 이 양식에서 데이터 세트를 업로드할 위치 또는 작업 영역에서 자동으로 만들어지는 기본 스토리지 컨테이너를 선택하거나 실험에 사용하려는 스토리지 컨테이너를 선택


3) 데이터가 가상 네트워크 뒤에 있는 경우 **유효성 검사 함수 건너뛰기**를 사용 하도록 설정하여 작업 영역에서 데이터에 액세스할 수 있도록 해야 함


4) **찾아보기**를 선택하여 데이터 집합에 대한 데이터 파일을 업로드


5) **설정 및 미리 보기** 양식을 검토하여 확인

- 양식은 파일 형식에 따라 지능적으로 채워진다.

- 다음 클릭 시 유효성 검사 및 업로드, 상태가 업데이트 된다.

![studio_3]({{https://github.com/wlslwlsl/wlslwlsl.github.io}}/assets/AutoML/s3.png){:.aligncenter}

6) 테이블 1필드 Description파일 형식파일에 저장된 데이터의 **레이아웃 및 유형을 정의**

![studio_4]({{https://github.com/wlslwlsl/wlslwlsl.github.io}}/assets/AutoML/s4.png){:.aligncenter}


- 해당 파일은 쉼표로 구분되어 있으므로 양식을 맞춰준다.

- Encoding 데이터 세트를 읽는 데 사용할 문자 스키마 테이블을 식별

- 열 머리글데이터 세트의 헤더(있는 경우)가 처리되는 방법을 나타낸다.

- 행 건너뛰기데이터 세트에서 건너뛴 행(있는 경우)의 수를 나타낸다.


7) **다음**을 클릭하면 스키마가 나오는데 **스키마** 양식은 **설정 및 미리 보기** 양식의 선택 사항에 따라 지능적으로 채워짐.

![studio_5]({{https://github.com/wlslwlsl/wlslwlsl.github.io}}/assets/AutoML/s5.png){:.aligncenter}

- 여기서는 각 열의 데이터 형식을 구성하고, 열 이름을 검토하고, 실험에 포함하지 않을 열을 선택


8) **다음**을 클릭하면 세부 정보 확인 양식이 나오는데 해당 양식은 **기본 정보** 및 **설정 및 미리 보기** 양식에 채운 정보를 요약한 것

- 프로파일링을 사용하도록 설정된 컴퓨팅을 사용하여 데이터 세트에 대한 데이터 프로필을 만드는 옵션도 존재.


9) 만들기를 클릭하면 데이터가 생성된 목록을 보여주는 화면으로 이동


10) 해당 화면에서 데이터를 선택한 후 다음을 클릭

![studio_6]({{https://github.com/wlslwlsl/wlslwlsl.github.io}}/assets/AutoML/s6.png){:.aligncenter}


## 2. 실행구성

**1) 실행 구성**

→ 실험 이름 및 target_metric을 선택하고 컴퓨팅을 새로 만든다.

![studio_7]({{https://github.com/wlslwlsl/wlslwlsl.github.io}}/assets/AutoML/s7.png){:.aligncenter}

- Standard_DS12_V2

- 최소노드 : 1

- 최대노드 : 2

- 규모 축소 전 유휴 시간 : 120(기본값)


**2) Select task and serttings**

![studio_8]({{https://github.com/wlslwlsl/wlslwlsl.github.io}}/assets/AutoML/s8.png){:.aligncenter}

- 추가 구성 설정 보기 : 메트릭, 종료기준, 유효성 검사, 동시성

- 기능화 설정 : 학습에 맞게 데이터를 준비하기 위해 데이터 세트에 대해 수행되는 작업을 식별


**3) 실험 및 모델 살펴보기**

만들면 실험이 시작되고 실험 섹션으로 가면 확인이 가능하다.

![studio_9]({{https://github.com/wlslwlsl/wlslwlsl.github.io}}/assets/AutoML/s9.png){:.aligncenter}

- **모델** 탭으로 이동하여 테스트한 알고리즘(모델) 확인이 가능

- 기본적으로 모델은 완료되면 메트릭 점수를 기준으로 정렬

- 완료된 **알고리즘 이름**을 선택하면 성능 세부 정보 조회가 가능

- **세부 정보** 및 **메트릭** 탭으로 이동하여 선택한 모델의 속성, 메트릭 및 성능 차트 확인 가능

![studio_10]({{https://github.com/wlslwlsl/wlslwlsl.github.io}}/assets/AutoML/s10.png){:.aligncenter}

- 모델을 선택한 후 세부정보, 메트릭 등을 통해 확인이 가능

![studio_11]({{https://github.com/wlslwlsl/wlslwlsl.github.io}}/assets/AutoML/s11.png){:.aligncenter}

- 확대 화살표를 통해 상세하게 볼 수 있음


## 배포

웹 서비스로 배포가 가능

→ 새 데이터를 예측하고자 할 때 유용


## 리소스 삭제

- Azure Portal의 맨 왼쪽에서 **리소스 그룹**을 선택

- 목록에서 만든 리소스 그룹을 선택

- **리소스 그룹 삭제**를 선택