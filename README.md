# TIL

`배움 기록소`

# 22.11

<details>
<summary>22.11.16</summary>
<div markdown="1">

**머신러닝, 딥러닝 스터디 OT**

</div>
</details>

# 22.10

<details>
<summary>22.10.18</summary>
<div markdown="1">

**네이버 지도 맛집 스크래핑**

* 프로젝트 팀 TL님께서 공유해주신 코드를 통해 네이버 지도 맛집 스크래핑 시도
* 35% 정도 수행

</div>
</details>

<details>
<summary>22.10.17</summary>
<div markdown="1">

**텍스트 분석**
* 통계 수업에 배웠던 코드 활용해서 리뷰 텍스트 분석
    <details>
    <summary>텍스트 분석 코드</summary>
    <div makrkdown="1">

    ```python
    import pandas as pd
    import numpy as np
    import matplotlib.pyplot as plt
    import re
    import urllib.request
    from konlpy.tag import Okt ## konlpy.tag 한국 형태소 분석기
    from tqdm import tqdm
    from tensorflow.keras.preprocessing.text import Tokenizer
    from tensorflow.keras.preprocessing.sequence import pad_sequences

    df = pd.read_excel('소금빵맛집_스윗솔트_리뷰200.xlsx')

    from sklearn.feature_extraction.text import CountVectorizer
    cv = CountVectorizer(stop_words='english', max_features=2000)
    dtm = cv.fit_transform(df.bread)

    word_count = pd.DataFrame({
    '단어': cv.get_feature_names_out(),
    '빈도': dtm.sum(axis=0).flat
    })

    word_count.sort_values('빈도', ascending=False).head(35)
    ```
* 오류 발생  
테이블에 빈 행이 생겼더니 `AttributeError: 'int' object has no attribute 'lower' in TFIDF and CountVectorizer` 에러 발생
* 생각보다 리뷰 데이터는 빵의 특성을 잘 보여주지 않는다는 것을 깨달음...  
대부분 맛 평가를 '맛있다'로 퉁치고 상세하게 설명하지 않음
    </div>
    </details>


<details>
<summary> 22.10.16</summary>
<div markdown="1">       

**네이버 지도 스크래핑**
* ifame으로 네이버 지도에서 검색어를 검색했을 때 나오는 결과창만을 뽑아냄
* 검색 출력 창이 스크롤되지 않는 문제 발생
* 타사이트에서는 제대로 스크롤되나 네이버 플레이스 검색 출력값 창에서만 불가

    <details>
    <summary> 실패 코드 </summary>
    <div markdown="1"> 
        
    ```python
    from selenium import webdriver
    from bs4 import BeautifulSoup
    from selenium.webdriver.chrome.service import Service
    from webdriver_manager.chrome import ChromeDriverManager
    from selenium.webdriver.common.by import By # import 문 추가
    import pandas as pd
    import time 

    chrome_options = webdriver.ChromeOptions()
    driver = webdriver.Chrome(service=Service(ChromeDriverManager().install()), options=chrome_options)

    driver.implicitly_wait(3)
    # Selenium을 통해 실제 크롬창에서 접속한 것과 동일하게 해당 URL내용을 가져옴
    driver.get("희망 url")

    last_height = driver.execute_script("return document.body.scrollHeight")
 
    while True:
        driver.execute_script("window.scrollTo(0, document.body.scrollHeight)")
        time.sleep(2)
        new_height = driver.execute_script("return document.body.scrollHeight")
        if new_height == last_height:
            break
        last_height = new_height
        html = driver.page_source
    ```
        
    </div>
    </details>

</div>
</details>

<details>
<summary>22.10.11</summary>
<div markdown="1">       

**GALQ 자격증 취득^^**

**K-평균 군집분석 (K-Means cluster)** 
* 사이킷런(sklearn) 활용해서 어떤 식으로 사용하는지
* https://planharry.tistory.com/43 참고

</div>
</details>

<details>
<summary>22.10.09 </summary>
<div markdown="1">       

**Pandas로 데이터셋에 원하는 컬럼의 문자열 추출 개수 세기**
* Velog에 코드 정리한 거 올려주기 https://velog.io/@dbdb26/Pandas-특정-문자열-추출-후-개수-세기

</div>
</details>

<details>
<summary>22.10.07</summary>
<div markdown="1">       

**깃 오류잡기 (성공)**
* 다시 처음부터 깃 레포지토리와 vscode 연결.
무언가 꼬여서 안될 때는 처음부터 다시해보는 것이 방법일 수 있음

**파이썬 복습**
* 어수웅 강사님 강의 필기본 다시 보면서 클래스 복습

</div>
</details>

<details>
<summary>22.10.05</summary>
<div markdown="1">       

**깃 연결 오류잡기(1차 시도 실패)**
* vscode와의 연결 오류 찾으려했으나 실패 -> 이번 주 안으로 해결 도전

**포토폴리오 제작 위한 경험정리**
* 포토폴리오 레퍼런스 수집
* 경험정리 작성

</div>
</details>

# 22.09

<details>
<summary>22.09.30</summary>
<div markdown="1">       

# TIL 시작

**공간분석 공모전 폭주 기관차 332 팀 회고**
* KPT 회고를 통해 팀의 유지할 점, 개선할 점 작성
* 팀 워크스페이스에 정리

**도메인**
* 관심 도메인 탐색


</div>
</details>


