# Movie-Trope-Data-Analysis-PCA-K-Means-Clustering-
영화 트룹 데이터 분석 (TF-IDF, PCA, K-Means Clustering 활용)

*Concept
- 각 공포 영화의 트롭들이 서로 유사한 영화끼리 묶이면, 문화성향으로 영화를 분류 할 수 있을 것이다.

*Process
-1. 트롭 사이트에서 Horror Flim 영화들의 트롭들 모두 크롤링
-2. 영화끼리 트롭의 유사도를 알기 위하여 TF-IDF 알고리즘으로 계산하여 매트릭스 생성
-3. 이 매트릭스를 K-Means Clustering 알고리즘으로 군집 시킴

*Base
-1. 트롭이란 무엇인가?
    영화의 스토리텔링 장치를 의미한다.
-2. TF-IDF란 무엇인가?
    https://medium.com/@nsh235482/tf-idf-term-frequency-inverse-document-frequency-algorithm-55f64714880d 참조
-3. 차원의 저주란 무엇인가?
    https://datascienceschool.net/view-notebook/f10aad8a34a4489697933f77c5d58e3a/ 참조
-4. K-Means Clustering이란 무엇인가?
    https://medium.com/@nsh235482/k-means-clustering-6ab85a2a32ad 참조

*Details
-1. 트롭 사이트에서 Horror Flim에 있는 영화들의 URL을 수집하여 트롭들을 모두 크롤링하였다. (현재 코드에서는 빠져있음)
-2. TF-IDF 매트릭스를 만들기 전에 전처리를 해주기 위하여 각 영화의 모든 트롭들을 토큰화하고, 불용어를 제거하였다. 
    그 후에 전처리를 하였는데, 전처리 기법은 Lemmatization 음소 표기법을 사용하였다.
    (Lemmatization 음소 표기법 설명)
-3. TfidfVectorizer를 사용하여 TF-IDF 방식으로 단어의 가중치를 조정한 BOW 벡터를 만들고, fit을 해서 매트릭스를 생성하였다.
-4. 계산된 매트릭스를 Numpy 배열로 변환시켰다.
-5. 토큰화된 트롭 말뭉치가 총 9771개로 차원의 저주를 해소하기 위해 Numpy배열을 주성분분석(PCA)으로 차원을 축소 시켰다.
    주성분 수를 결정하기 위하여 주성분 수를 임의로 6개로 주고, Scree Plot을 보았다.
    꺾이는 지점이 Component가 2인 지점으로 확인되어, 주성분 수를 2개로 결정하였다.
-6. PCA로 차원 축소한 Matrix를 K-Means Clustering 알고리즘을 적용하여 군집시켜보았다.
    군집 개수가 적당한지 알아보기 위하여 Scree Plot을 그렸는데, 꺾이는 지점이 3이었기 때문에 군집 개수는 3으로 정하였다.
-7. 이를 시각화하여 군집이 제대로 됐는지 알아본다.

*Result
-결과적으로는 군집이 한쪽으로 쏠린 경향이 있어 분류가 잘 되는지 보기 어려웠음.
