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

### 2.3. 프론트엔드

* HTML/CSS/JS

  이미지 넣기

  1. HTML 설명
  2. CSS 설명
  3. JS 설명


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

다음은 이미지 데이터 수집을 위해 크롤링한 데이터 예시입니다.

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

- 이미지 데이터 수집은 구글을 기반으로 연예인의 이름이 저장된 엑셀파일을 불러온후 크롤링을 시행하였습니다. 
- 추가적으로 부족한 이미지 데이터는 "증명사진" and "여권사진" 검색어를 통해 이미지를 가져왔습니다.

다음은 이미지 데이터 전처리 및 군집화에 대한 데이터 예시입니다.

```python
from sklearn.cluster import KMeans

# train set으로 KMeans 학습
clf = KMeans(n_clusters = 13)
clf.fit(man_train_encodings)

# 13개의 class로 나뉘었는지 확인
np.unique(clf.labels_)
```

#### 3.1.3. 이미지 데이터 군집화

* 협업필터링을 잠재 요인 모델을 활용해 구현합니다.
* 행렬 인수분해 방법은 모든 항목에 독립적인 고유한 표현식을 갖고 있다고 가정하여 가중치가 적용된 각 속성에 대한 사용자의 강도를 합산하여 근사값(잠재 요인)을 구하는 방식입니다.
* 해당 향수 추천 서비스에서는 향수의 리뷰와 평점을 기반으로 사용자에게 향수를 추천하거나 서비스를 제공합니다.
* 여러 SVD 중 행렬의 대각원소(특이값) 중 상위 t개만 골라내는 truncated SVD를 사용하였습니다.
* 행이 향수의 고유Id, 열이 User인 피봇테이블을 생성합니다.

![pivot](images/p.png)

- 차원축소를 위해 scikit learn의 TruncatedSVD API를 사용합니다. 차원을 12차원으로 축소시켰습니다.

```python
SVD = TruncatedSVD(n_components=12)
SVD_matrix = SVD.fit_transform(review_pivot)
```

- 차원이 축소된 행렬로 모든  쌍에 대한 피어슨 상관계수를 계산합니다.

```python
corr = np.corrcoef(SVD_matrix)
```

- 한 향수의 값이 입력이 되면 상관점수가 0.9 이상 1 미만인 향수 10개가 추천이 됩니다.
- 해당 향수 추천서비스에는 리뷰가 들어있는 향수에 한해서 최대 10개의 추천 향수가 저장되어 있습니다.

다음은 [Basenotes.net](http://www.basenotes.net/)에서 크롤링한 데이터 예시입니다.

```json
// 향수 데이터 예시
{
    "pk": 26120000,
    "model": "perfumes.perfume",
    "fields": {
        "name": "Ambre Canelle",
        "launch_date": "1949-01-01",
        "thumbnail": "http://www.basenotes.net/photos/products/st/26120000.jpg",
        "gender": 0,
        "top_notes": [224, 480],
        "heart_notes": [224, 259, 510, 785],
        "base_notes": [28, 624],
        "seasons": [3, 4],
        "availability": false,
        "brand": 749,
        "categories": [3, 6],
        "price": 169.99
    }
}
```

```json
// 노트 데이터 예시
{
    "pk": 1,
    "model": "perfumes.note",
    "fields": {
        "name": "absinthe",
        "kor_name": "압생트"
    }
}
```

```json
// 리뷰 데이터 예시
{
    "pk": 1,
    "model": "perfumes.review",
    "fields": {
        "content": "This is a grown-up powdery perfume.  Very feminine.  The powdery vibe changes mood as it mellows on the skin.  In the middle there is a smoky-musky, almost bitter vanilla.  Towards the \"end\" a heliotropic floral with a tangy citrus accord.  Sweet Dreams is a good name for this.  It describes it well.\n\r\nLongevity is outstanding.  Sillage is better than moderate.",
        "rate": 7,
        "created_at": "2017-09-02 00:00:00",
        "user": 1,
        "perfume": 26149998
    }
}
```

## 4. 아키텍처 상세

![System architecture](images/system_architecture.png)

## 5. 레이아웃 및 디자인


