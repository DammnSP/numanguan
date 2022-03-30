# 딥러닝 모델 기반 키워드 추천 프로젝트[NUMANGUAN]

### 목차

<hr>

[0. 팀 소개](#0-팀-소개)

[1. 서비스 소개](#1-서비스-소개)

[2. 기술스택](#2-기술스택)

[3. 데이터 분석 과정](#3-데이터-분석-과정)

[4. 아키텍처 상세](#4-아키텍처-상세)

[5. 레이아웃 및 디자인](#5-레이아웃-및-디자인)

<hr>

## 0. 팀 소개

![team_all](https://user-images.githubusercontent.com/87697789/133199767-a79c700f-d1dc-4f9d-9167-4aedb3a782f5.png)

* **팀장** 서유리 : 이미지 데이터분석 / 앱구현 / 디자인
* 팀원 성수현 : 프로그램 통합관리 / 이미지 데이터분석 / Back-End / 딥러닝 모델 구현
* 팀원 한솔 : 프로젝트 설계 / 텍스트 데이터분석/ 웹구현

## 1. 서비스 소개

> 딥러닝을 기반으로 유명인의 얼굴과 키워드를 추천해주는 서비스

흥미로운 키워드에 대한 정보를 통해 2040 누구나 사용하기에 부담스럽지 않고, 재미를 주는 웹 서비스입니다. 

### 1.1. 타겟 고객군

* **2040 누구나**

  상대방의 외모(이미지)와 성격(텍스트)와 같은 다양한 정보를 찾고 싶은 2040

### 1.2. 주요 기능

#### 1.2.1. 본인의 외모(이미지와) 성격(텍스트)에 따른 정보제공

  자신의 이미지와 관련된 키워드에 대한 정보를 알 수 있습니다.

## 2. 기술 스택

### 2.1. 데이터 수집 및 처리

* Selenium | BeatifulSoup | Keras

<img src = "https://user-images.githubusercontent.com/58734611/160864074-463f93d8-dd61-4dc8-89e1-86ec20279551.png" width="10%" height="10%">    <img src = "https://user-images.githubusercontent.com/58734611/160864398-00cd9de2-2daa-44db-b5a5-83d98c3492ad.png" width="30%" height="40%">   <img src = "https://user-images.githubusercontent.com/58734611/160864529-86c3bc81-cf5a-4bb7-9dd7-4b060544b41c.png" width="30%" height="40%">

* OpenCV : land mark 얼굴요소

<img src = "https://user-images.githubusercontent.com/58734611/160864715-b7a898d1-8dbd-4236-a8ff-e609a56f8202.png" width="30%" height="40%">

* Vision API : 정면얼굴 추출

<img src = "https://user-images.githubusercontent.com/58734611/160865120-32c06404-acb5-4835-bb8e-3ee5cd94bf27.png" width="30%" height="40%">

### 2.2. Back-End

* Python | FastAPI | Oracle

<img src = "https://user-images.githubusercontent.com/58734611/160866042-947a9067-24d7-4cb9-ae1d-7385054e2b23.png" width="30%" height="40%">  <img src = "https://user-images.githubusercontent.com/87697789/133209834-80b424b2-1742-4682-b520-7758bb332237.png" width="40%" height="50%"> <img src="https://user-images.githubusercontent.com/87697789/134466051-b6fa8dc0-3256-4565-b803-87e3f0f5cf80.png" width="20%" height="20%">

### 2.3. Front-End

* BootStrap5

 <img src="https://user-images.githubusercontent.com/58734611/160869035-4c7595d3-c495-4820-8f21-8488eb5ce01d.png" width="30%" height="40%">

### 2.4. 서버

* AWS EC2 (Server) | AWS RDS (DB)

 <img src="https://user-images.githubusercontent.com/58734611/160869276-79fe6ce9-0539-4d03-a44e-0cec29bf3481.png" width="30%" height="40%"> <img src="https://user-images.githubusercontent.com/58734611/160869489-a0c68637-c47a-43ed-a458-92ce5b04799a.png" width="30%" height="40%">

### 2.4. 프로젝트 관리

* GitHub | Google driver

 <img src="https://user-images.githubusercontent.com/58734611/160869906-11765d0b-991d-4e47-a6db-ff5c4edc8578.png" width="30%" height="40%"> <img src="https://user-images.githubusercontent.com/58734611/160869977-ba6de438-0fa2-47bd-a5ee-61ba4ac92ec6.png" width="30%" height="40%">
 
## 3. 데이터 분석 과정

### 3.1. 이미지 데이터 

#### 3.1.1. 데이터 수집

- 이미지 데이터 수집은 구글을 기반으로 연예인의 이름이 저장된 엑셀파일을 불러온후 크롤링을 시행하였습니다. 
- 추가적으로 부족한 이미지 데이터는 "증명사진" and "여권사진" 검색어를 통해 이미지를 가져왔습니다.
- 텍스트 데이터 수집은 신한생명 사이트의 사주팔자의 내용을 기반으로 크롤링을 시행하였습니다.

#### 3.1.2. 이미지 데이터 전처리 및 군집화

- 정확도를 높히기 위해 크롤링한 이미지들의 정면 이미지를 추출하였습니다.
- 추출한 이미지에 원하는 레이블을 달아주기 위해 KMeans 군집화 방법을 사용하였습니다.

#### 3.1.3. 이미지 데이터 모델링

- 레이블을 달아준 데이터를 통해 학습 및 테스트를 진행하였습니다. (train:validation:test = 8:1:1).
- 레이블이 5개이므로 출력층을 구성하였습니다. (softmax).


## 4. 아키텍처 상세

![아키텍처_수정본](https://user-images.githubusercontent.com/87697789/134605443-5b0b065c-4f7f-47ec-ac51-61f9824f6fbf.png)


## 5. 레이아웃 및 디자인

<img src="https://user-images.githubusercontent.com/58734611/160872234-fa2d2587-c0db-4370-be5f-af811e3a78a9.png">  <img src="https://user-images.githubusercontent.com/58734611/160872386-2ce388d0-3082-4de0-8214-45d830cf703b.png">
