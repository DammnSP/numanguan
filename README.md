💞 키워드와 사주팔자를 통한 데이팅 앱 프로젝트[NUMANGUAN]

[NUMANGUAN 바로가기](Site 주소)

[팀 노션 바로가기](Site 주소) 

### 목차

<hr>

[0. 팀 소개](#0.-팀-소개)

[1. 서비스 소개](#1.-서비스-소개)

[2. 기술스택](#2.-기술스택)

[3. 데이터 분석 과정](#3.-데이터-분석-과정)

[4. 아키텍처 상세](#4.-아키텍처-상세)

[5. 레이아웃 및 디자인](#5.-레이아웃-및-디자인)

<hr>
## 0. 팀 소개

![team_all](https://user-images.githubusercontent.com/87697789/133199767-a79c700f-d1dc-4f9d-9167-4aedb3a782f5.png)

* **팀장** 서유리 : 이미지 데이터분석 / 앱구현 / 디자인
* 팀원 성수현 : 프로그램 통합관리 / 이미지 데이터분석 / 서버구성 및 관리 
* 팀원 한솔 : 프로젝트 설계 / 텍스트 데이터분석/ 웹구현

## 1. 서비스 소개

> 딥러닝을 기반으로 고객의 짝을 찾아주는 데이팅앱 서비스

흥미로운 키워드와 사주팔자에 대한 정보를 통해 2040 누구나 사용하기에 부담스럽지 않고, 짝을 찾는 재미를 주는 앱 서비스입니다. 

[앱구현 : NUMANGUAN 사이트 맨 앞부분 넣기]

### 1.1. 타겟 고객군

* **2040 누구나**

  상대방의 외모(이미지)와 성격(텍스트)와 같은 다양한 정보를 바탕으로 짝을 찾고 싶은 2040

### 1.2. 주요 기능

#### 1.2.1. 상대방의 외모(이미지와) 성격(텍스트)에 따른 정보제공

1. 자신의 이미지와 관련된 키워드에 따른 상대방의 외모와 성격에 대한 정보를 알 수 있습니다.

[앱구현 : 결과와면 중 이미지와 키워드 관련 사진넣기]

#### 1.2.2. 추천 알고리즘

1. **1000개**의 영화 상세 정보를 열람할 수 있습니다.

[앱구현 : 추천 알고리즘 관련 사진 넣기]

## 2. 기술 스택

### 2.1. 데이터 수집 및 처리

> 이미지 데이터

* Selenium
: 웹앱을 테스트하는데 이용하는 프레임 워크

* BeatifulSoup
: HTML정보로 부터 원하는 데이터를 가져오기 쉽게, 비슷한 분류의 데이터별로 나누어주는(parsing) 파이썬 라이브러리

* Keras (Tendorflow)
: 딥러닝 모델을 빌드하고 학습시키기 위한 Tendorflow의 상위수준 API

* OpenCV (land mark 얼굴요소)
: 사람 얼굴의 특징점을 찍어내는 방법

* Vision API
: 정면 얼굴추출

> 텍스트 데이터

> 추천 알고리즘

### 2.2. 백엔드

* Python 3.6.8

* FastAPI
  
  <img src = "https://user-images.githubusercontent.com/87697789/133209834-80b424b2-1742-4682-b520-7758bb332237.png" width="30%" height="40%">

  > 현대적이고, 빠르며(고성능), 파이썬 표준 타입 힌트에 기초한 Python3.6+의 API를 빌드하기 위한 웹 프레임워크입니다.

  1. 빠름 (Starlette과 Pydantic 덕분에) NodeJS 및 Go와 대등할 정도로 매우 높은 성능 (사용가능한 가장 빠른 파이썬 프레임워크 중 하나)
  2. 빠른 코드 작성 : 약 200%에서 300%까지 기능 개발 속도 증가
  3. 적은 버그 : 사람(개발자)에 의한 에러 약 40% 감소
  4. 표준 기반 : API에 대한 (완전히 호환되는) 개방형 표준기반

* Mariadb

 <img src="https://user-images.githubusercontent.com/87697789/133231494-29b79afe-c8e4-4c51-a799-bf4d5e948d7d.png" width="30%" height="40%">
 
 > 오픈 소스의 관계형 데이터베이스 관리 시스템(RDBMS)이다.

### 2.3. 프론트엔드

* HTML/CSS/JS

### 2.4. 배포

* AWS EC2
* Docker

### 2.4. 프로젝트 관리

* Git
* Google driver

## 3. 데이터 수집 및 분석 과정

### 3.1. 이미지 데이터 

#### 3.1.1. 이미지 데이터 수집

- 이미지 데이터 수집은 구글을 기반으로 연예인의 이름이 저장된 엑셀파일을 불러온후 크롤링을 시행하였습니다. 
- 추가적으로 부족한 이미지 데이터는 "증명사진" and "여권사진" 검색어를 통해 이미지를 가져왔습니다.

다음은 이미지 데이터 수집을 위해 크롤링한 코드 예시입니다.

```python

# 라이브러리 불러오기
from selenium import webdriver
from selenium.webdriver.common.keys import Keys
import time
import urllib
import time

# 구글이미지 검색해서 해당 사진 가져오기
driver = webdriver.Chrome()
driver.get("https://www.google.co.kr/imghp?hl=ko&authuser=0&ogbl")
for j in name[0:2100]:
    elem = driver.find_element_by_name("q")
    elem.clear()
    elem.send_keys(j)
    elem.send_keys(Keys.RETURN)

    images = driver.find_elements_by_css_selector(".rg_i.Q4LuWd")

    count = 1

    for i in images[1:11]: # 1번과 2번 사진이 공통된 사진이므로, 2번 부터 실행
        try:
            i.click()
            time.sleep(1)
            img_url = driver.find_element_by_css_selector(".n3VNCb").get_attribute("src")
            urllib.request.urlretrieve(img_url, j + str(count) + ".jpg")
            count = count + 1
        except:
            pass
    
driver.close() # 창 닫기
```

#### 3.1.2. 이미지 데이터 전처리 및 군집화

- 정확도를 높히기 위해 크롤링한 이미지들의 정면 이미지를 추출하였습니다.
- 추출한 이미지에 원하는 레이블을 달아주기 위해 KMeans 군집화 방법을 사용하였습니다.

다음은 이미지 데이터 전처리 및 군집화에 대한 코드 예시입니다.

```python
from sklearn.cluster import KMeans

# train set으로 KMeans 학습
clf = KMeans(n_clusters = 13)
clf.fit(man_train_encodings)

# 13개의 class로 나뉘었는지 확인
np.unique(clf.labels_)
```

#### 3.1.3. 이미지 데이터 모델링

- 레이블을 달아준 데이터를 통해 학습 및 테스트를 진행하였습니다. (train:validation:test = 8:1:1).
- 레이블이 13개이므로 출력층을 구성하였습니다. (softmax).

다음은 이미지 데이터 모델링에 대한 코드 예시입니다.

```python
import matplotlib.pyplot as plt
from keras import models
from keras import layers

model = models.Sequential()

# hidden layer에 합성곱과 맥스 풀링 설정
model.add(layers.Conv2D(256, (3, 3), activation='relu', input_shape=(150, 150, 3)))
model.add(layers.MaxPooling2D(2, 2))
model.add(layers.Conv2D(128, (3, 3), activation='relu'))
model.add(layers.MaxPooling2D(2, 2))
model.add(layers.Conv2D(64, (3, 3), activation='relu'))
model.add(layers.MaxPooling2D(2, 2))


# 1차원으로 변환
model.add(layers.Flatten())

# 입력 데이터에 50%의 노드를 무작위로 사용하지 않게 막는다.
model.add(layers.Dropout(0.5))

# 결과얻기
# class를 13개로 정하였으므로 softmax 설정
model.add(layers.Dense(512, activation='relu'))
model.add(layers.Dense(13, activation='softmax'))
```

### 3.2. 텍스트 데이터 

#### 3.2.1. 텍스트 데이터 수집

- 텍스트 데이터 수집은 신한생명 사이트의 사주팔자의 내용을 기반으로 크롤링을 시행하였습니다. 

다음은 텍스트 데이터 수집을 위해 크롤링한 코드 예시입니다.

```python
```

## 4. 아키텍처 상세

![아키텍처 상세](https://user-images.githubusercontent.com/87697789/133373513-891ea78a-582e-484a-a31c-6c02882b48a2.png)


## 5. 레이아웃 및 디자인


