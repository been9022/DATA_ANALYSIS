# 데이터분석 2주차 정규과제

📌데이터분석 정규과제는 매주 정해진 분량의 『*혼자 공부하는 데이터 분석 with 파이썬*』 을 읽고 학습하는 것입니다. 이번 주는 아래의 **DataAnalysis_2nd_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=s_-VvTLb3gs&list=PLVsNizTWUw7FGzSRCkQrPEEe-ljVXgS7k&index=4
https://www.youtube.com/watch?v=Il6L8OtNFpc&list=PLVsNizTWUw7FGzSRCkQrPEEe-ljVXgS7k&index=5
-->


## DataAnalysis_2nd_TIL

### 2장 데이터 수집하기
#### 01. API 사용하기
#### 02. 웹 스크래핑 사용하기


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~81    | ✅         |
| 2주차 | p.84~151   | ✅         |
| 3주차 | p.154~219  | 🍽️         |
| 4주차 | p.222~279 | 🍽️         |
| 5주차 | p.282~325 | 🍽️         |
| 6주차 | p.328~379 | 🍽️         |
| 7주차 | p.382~430 | 🍽️         |

<br>

<!-- 여기까진 그대로 둬 주세요-->


# 1️⃣ 개념 정리 

## 01. API 사용하기

API와 HTTP

API는 프로그램이 다른 프로그램이나 서버에 데이터를 요청하고 받아오기 위한 방식이다. 웹에서 사용하는 API는 주로 HTTP 통신을 이용한다.

HTTP에서는 클라이언트가 서버에 데이터를 요청하면 서버가 그에 맞는 데이터를 응답한다. 이때 주고받는 데이터는 주로 CSV, JSON, XML 등의 형태로 제공된다.

JSON

JSON은 딕셔너리와 리스트를 조합하여 데이터를 표현하는 형식이다. 파이썬의 딕셔너리 구조와 비슷해서 다루기 편리하다.

import json
import pandas as pd
json.dumps() : 파이썬 객체 → JSON 문자열
json.loads() : JSON 문자열 → 파이썬 객체
pd.read_json() : JSON → 데이터프레임
pd.DataFrame() : 딕셔너리 등의 파이썬 객체 → 데이터프레임
XML

XML은 데이터를 태그로 표현하며, 부모와 자식 요소가 있는 계층적인 구조를 가진다.

import xml.etree.ElementTree as et
import pandas as pd
et.fromstring() : XML 문자열 → 파이썬에서 처리 가능한 객체
.tag : 해당 엘리먼트의 태그 이름 확인
.findtext() : 특정 자식 엘리먼트의 텍스트 가져오기
.findall() : 조건에 맞는 여러 자식 엘리먼트 찾기
pd.read_xml() : XML → 데이터프레임
API를 이용해 데이터 가져오기

데이터를 사용하는 방법에는 CSV·JSON·XML 파일을 직접 다운로드하는 방법과 파이썬에서 API를 호출해 데이터를 받아오는 방법이 있다.

파이썬에서는 requests 패키지를 이용해 API에 요청할 수 있다.

import requests
import pandas as pd

url = 'API 주소'

r = requests.get(url)   # API에 데이터 요청
data = r.json()         # 받은 JSON 데이터를 파이썬 객체로 변환
df = pd.DataFrame(data) # 데이터프레임으로 변환

## 02.웹 스크래핑 사용하기


웹 스크래핑은 웹사이트에서 필요한 정보를 직접 추출하는 방법이다. HTML은 데이터 분석을 위해 만들어진 형식이 아니기 때문에, 가능하다면 웹 스크래핑보다 공개 API가 있는지 먼저 확인하는 것이 좋다.

BeautifulSoup을 이용한 웹 스크래핑 과정

파이썬에서는 주로 requests와 BeautifulSoup을 함께 사용한다.

import requests
from bs4 import BeautifulSoup

전체적인 과정은 웹페이지 요청 → HTML 가져오기 → HTML 분석 → 원하는 태그 찾기 → 필요한 정보 추출 순서로 진행된다.

1. 웹페이지 요청

r = requests.get(url.format(isbn))

requests.get()을 이용해 URL에 접속하고 해당 페이지의 데이터를 가져온다.

2. HTML 파싱

soup = BeautifulSoup(r.text, 'html.parser')

r.text로 가져온 HTML 문자열을 BeautifulSoup을 이용해 분석하기 쉬운 형태로 변환한다.

3. 원하는 HTML 요소 찾기

prd_info = soup.find('a', attrs={'class': 'gd_name'})

.find()를 이용하면 원하는 태그를 찾을 수 있다.
위 코드에서는 a 태그 중 class="gd_name"인 요소를 찾는다.

4. 링크를 이용해 새로운 페이지 접속

r = requests.get(url + prd_info['href'])

찾은 태그의 href 속성에서 링크를 가져와 상세 페이지에 다시 접속한다. 이후 같은 방식으로 HTML을 파싱하고 원하는 정보를 추출하면 된다.

BeautifulSoup의 역할

BeautifulSoup은 HTML 문서를 분석하고 원하는 태그나 텍스트를 쉽게 찾을 수 있게 해주는 파이썬 패키지이다.


# 2️⃣ 수행 인증


<img width="686" height="440" alt="인4" src="https://github.com/user-attachments/assets/4ed8c214-15a0-4ce5-878e-d3a69fd6a41c" />
<img width="930" height="632" alt="인3" src="https://github.com/user-attachments/assets/4119443a-10f1-434d-81e0-d54e01beb492" />
<img width="1277" height="592" alt="인2" src="https://github.com/user-attachments/assets/13db5ae6-0a02-4104-a75c-66aece7529c5" />
<img width="1797" height="662" alt="인1" src="https://github.com/user-attachments/assets/35c4ed59-be18-44b7-a2eb-5d2822b5f29d" />



<br>
<br>

# 3️⃣ 확인 문제

## 문제 1.

> **🧚Q. 다음 중 BeautifulSoup 외에 웹 스크래핑에 사용할 수 있는 파이썬 패키지로 가장 적절한 것은 무엇인가요?**

```
1️⃣ NumPy  
2️⃣ Scrapy  
3️⃣ Matplotlib  
4️⃣ Scikit-learn  
```

```
Scrapy

이유: Scrapy는 웹사이트의 데이터를 자동으로 수집하고 처리할 수 있도록 만들어진 웹 스크래핑 전용 파이썬 패키지이기 때문이다. BeautifulSoup과 마찬가지로 웹에서 필요한 정보를 추출할 때 사용할 수 있다.
```



### 🎉 수고하셨습니다.
