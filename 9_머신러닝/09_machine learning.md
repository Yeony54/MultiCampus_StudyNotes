Machine learning

# Machine learning



### 01. ML 개요

AI (Artificial Inteligence) 란?

\- 사람의 사고능력을 구현한 프로그램(시스템) 즉 인공지능을 말한다.

\- Strong AI, Weak AI로 나누어진다.



- Rule Based Program

  `Data` → `Program` → `solution`

  데이터를 프로그램에 넣어 해답을 찾는 방식

  

- Machine Learning

  `Data & solution` → `Program` → `Rule`

  데이터와 해답을 같이 넣어서 규칙성을 찾는 방식

  이 규칙을 사용해 미지의 데이터를 예측한다.



- Machine Learning이 잘 되게 하려면
  - 데이터가 많아야 한다.
  - 데이터가 양질의 데이터여야 한다.



- Machine Learning의 필요성

  Rule based programming은 조건에 따라 동작하는 프로그램이다.

  우리의 생활속에서 해결해야 하는 문제중에 조건이 너무 많아서 그 조건을 일일히 다 구현하지 못하는 경우가 있다.

  예를들어 자율주행, spam fillter, 바둑 등의 문제를 해결하기 위해 나온 개념이 machine learning이다. ("1959 " 아서 사무엘)



###  02. ML 종류

- AI (Artificial Intelligence)

  \- 가장 포괄적인 개념으로, 인간이 가지는 학습능력, 추출능력을 컴퓨터로 구현한것을 뜻한다.

- machine learning

  \- AI를 구현하기 위한 하나의 방법론

  \- 데이터를 기반으로 특성과 패턴을 파악한 후 그 결과(model)을 이용해 미지의 데이터에 대한 추정치를 계산하는 프로그램

  <table>
      <tr>
      	<th colspan='2' style="text-align:center;"
              bgcolor="#F5F5F5">기법</th>
      </tr>
      <tr>
      	<td bgcolor="#FFFFFF">● Regression (회귀)</td>
          <td bgcolor="#FFFFFF">● KNN (K-Nearest Neighbor)</td>
      </tr>
      <tr>
      	<td bgcolor="#FFFFFF">● SVM (Support Vector Machine)</td>
          <td bgcolor="#FFFFFF">● Neural Network (신경망)</td>
      </tr>
      <tr>
      	<td bgcolor="#FFFFFF">● Decision Tree, Random Forest</td>
          <td bgcolor="#FFFFFF">● Clustering (K-Means, DBScan)</td>
      </tr>
      <tr>
      	<td bgcolor="#FFFFFF">● Native Bayes</td>
          <td bgcolor="#FFFFFF">● Reinforcement Learning (강화학습)</td>
      </tr>
  </table>
  
  
  
- Deep learning

  \- Machine Learning의 한 분야인 "Neural Network"(신경망)을 이용해 학습하는 구조와 알고리즘을 지칭

  <table>
      <tr>
      	<th colspan='2' style="text-align:center;"
              bgcolor="#F5F5F5">기법</th>
      </tr>
      <tr>
      	<td bgcolor="#FFFFFF">● CNN</td>
          <td bgcolor="#FFFFFF">● DNN</td>
      </tr>
      <tr>
      	<td bgcolor="#FFFFFF">● RNN(LSTM)</td>
          <td bgcolor="#FFFFFF">● GNN</td>
      </tr>
  </table>

  \- Deep learning(Neural Network)을 제외한 machine learning 알고리즘은 정형 데이터 처리에 조금 더 적합하며, Deep learning보다 시간이 덜걸린다.

  \- Deep learning(Neural Network)은 비정형 데이터처리에 적합하며 시간이 오래걸리는특징이 있다. (이미지, 소리, 대용량 text 언어) 등 인지에 관련된 데이터 처리에 적합하다.



### 03. ML Type

Machine Learning 분류

- 지도학습 (supervised Learning)
- 비지도학습 (unsupervised Learning)
- 준지도학습 (semisupervised Learning)
- 강화학습 (Reinforcement Learning)

##### A. 지도학습 (supervised Learning)

> `Data(입력값) x`+`Data의Label(해답,정답) t` = `Training Data Set(학습데이터셋)`

지도학습은 입력값과 그에대한 정답을 함께 데이터셋으로 만들어서 입력한다.

- 지도학습은 어떤 종류의 미래값을 예측할까?

  \- Regression (회귀) : 예측값이 연속적인 수치값으로 나오는경우

  ​	예) 국가별 주식 데이터 값 예측

  \- Classification (분류) : 예측값이 어느 분류에 속하는가로 나오는 경우

  ​	예) 국가별 주식 데이터 값 오를지 내릴지 2진분류

  ​	예) 학교 등급 예측 A, B, C, D, ...

##### B. 비지도학습 (unsupervised Learning)

비지도학습은 지도학습과는 다르게 입력에 Label이 들어가 있지 않다.

입력값을 넣으면 유사한것들끼리 묶여서 Clustering(군집화) 된다.

##### C. 준지도학습 (semisupervised Learning)

준지도학습은 지도학습과 비지도학습의 중간단계이다.

예를 들어 구글 사진 분류가 여기에 해당된다.

전체 데이터를 Clustering 후 일부 데이터의 Label을 가지고 Label이 지정되지 않은 데이터의 Label을 지정해준다.

##### D. 강화학습 (Reinforcement Learning)

현재 상태에서 어떻게 하는것이 최적인가에 대해 Action, Reword 개념을 이용해 최상의 policy (정책)을 세운다. 예로 바둑이 이에 해당한다.



### 04. ML Porcess

##### ① 문제파악

- Domain 분석

##### ② EDA (탐색적 data 분석)

- 데이터 수집 : 내부 데이터 및 외부 데이터 활용 여부
- 결측치, 이상치 확인
- 분포확인, 변수간의 상관관계 확인

##### ③ 데이터의 pre-processing

##### ④ 모델 학습

- python 구현 (순수 python)
- tensorflow 구현
- scikit - learn

##### ⑤ prediction

- 평가방법도 여러가지이다.



















