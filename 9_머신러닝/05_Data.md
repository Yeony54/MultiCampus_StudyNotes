Machine learning

# Pandas Data Preprocessing

데이터 분석, machine learning, deep learning을 할 때에는 데이터의양, 품질이 중요하다.



### 01. 데이터 전처리 종류

- missing value (결측치)
- Outline (이상치)
- 중복데이터
- Data의 단위처리
- 정규화



### 02. Missing Value

- **Missing Value**(결치값)이란? DataFrame안에 누락된 값을 의미한다.
  <small>데이터 입력시 실수로 누락된 값이나, 파일 변환 시 처리 문제로 누락된 것이 예이다.</small>
- 누락된 값은 `NaN`으로 표시된다.
- Missing Value를 처리하는 방법에는 삭제, 대체등의 방법이 있다.

데이터를 가지고 처음해야하는것은 Missing Value가 존재하는지 확인하는 일이다.

결치값이 많으면 계산하는데 좋지않은 영향을 주기 때문에, 이를 처리해서 `NaN`이 없는 데이터를 먼저 만들어야 한다.



#### A. NaN값 찾는 방법

NaN값 찾는방법은 여러가지가 있다.

- df.info()

  info를 통해 `NaN` 제외 통계된 값을 보고 데이터가 얼마나 정돈되었는지 확인할 수 있다.

- value_counts()

  ```python
  df['deck'].value_counts(dropna=False)
  ```

  value_count의 속성 `dropna`를 False로 하여 NaN값을 같이 세어줄 수 있다.

- isnull()

  ```python
  df.isnull().sum(axis=0)
  ```

  isnull을 사용해 `NaN`값의 True값을 더해서 구할 수 있다.

- for문을 통해 column별 `NaN`값 count값 출력하기

  ```python
  missing_df = df.isnull()
  for col in missing_df.columns:
      missing_value = missing_df[col].value_counts()
      try:
          print(col, ' :', missing_value[True])
      except:
          print(col, ' :',0)
  ```





### B. NaN 값 처리 방법

`NaN` 값을 찾은 다음에는 `NaN`이 있는 행, 열을 삭제할것인지, 유지할것인지 판단해야한다.

분석에 유의미한 column은 최대한 유지해야하고, 그 반대는 삭제를 선택하면 된다.



🛸 **삭제**

만약 데이터가 충분히 많고, 결측값이 전체의 3~4% 이내 일때, 삭제를 하는 방법을 사용해 볼 수 있다.

심플하고, 다른 데이터에 영향을 끼치지도 않지만, 보통 데이터를 확보하는 과정에서 데이터가 부족하니 잘 선택해야한다.

- df.drop()

  ```python
  df2 = df.drop('deck', axis=1, inplace=False)
  ```

  `axis` 속성을 사용해서 행, 열을 삭제할 수 있다.

  `inplace` 속성을 사용해서 대체할 것인지 아닌지 설정할 수 있다.

- thresh 사용

  ```python
  thresh_df = df.dropna(axis=1, thresh = 500, inplace=False)
  ```

  `thresh`는 threshold로, 이 이상의 값을 가질 때 삭제할 수 있는 속성이다.

  위의예시에서는 컬럼 중, `NaN`값이 500개 이상일 시 삭제하도록 하였다.

- subset에 대해 결치값이 있는 행 삭제

  ```python
  result_df = df.dropna(subset=['age'], axis=0, how='any')
  ```

  `subset`을 사용해 열을 정해주고, 그 열 중에서 `NaN`값을 가진 행을 삭제하도록 하였다.

  



🛸 **대체**

대체의 종류로는 평균, 중위, 최대, 최소, 빈도 등이 있으며, 머신러닝 기법으로 값을 예측해서 채우는 방법이 있다.

방법은 분석하는 데이터를보고 때에 맞게 사용해야한다.

- 평균값으로 대체

  ```python
  mean_age = df['age'].mean()
  df['age'].fillna(mean_age, inplace=True)
  ```

  'age'컬럼의 `NaN`값을 평균값으로 대체해주었다.

- 빈도를 보고 대체

  여러가지 데이터 분포를 보았을 때, 데이터 특성상 서로 이웃하고 있는 데이터는 유사성을 가질 확률이 높다. 즉, 자기 주변의 데이터와 비슷한 경향을 가지기 때문에 `NaN`값을 그 값으로 대체해 준다.

  ```python
  df['embarked'].fillna(method='ffill', inplace=True)
  # df['embarked'].fillna(method='bfill', inplace=True)
  ```

  `method` 의 `'ffill'`속성은 `NaN`의 Front 값을 사용하여 값을 채우겠다는 속성이다.
  반대로 `'bfill'`속성은 Back 값을 사용하여 값을 채우겠다는 속성이다.



### 03. Outline

이상치는 데이터에서 있으면 안되는 튀는 값을 말한다.

> 예시)
>
> 사람의 키는 보통 2미터 아래의 값인데, 3미터 데이터 값은 이상치라고 할 수 있다.

그럼 이 이상치의 기준을 어떻게 정할것인지를 정해야 하기 때문에, 데이터에 대한 도메인 전문가가 필요하다.





### 04. Duplicate

중복되는 값 중에서는 의미가 있는 중복도 있고, 그냥 중복된 데이터가 존재하는것일 수도 있다.

```python
# duplicate 예시
import numpy as np
import pandas as pd

df = pd.DataFrame({'c1':['a', 'a', 'b', 'a','b'],
                   'c2': [1, 1, 1, 2, 2],
                   'c3': [1, 1, 2, 2, 2]})
```



- duplicated()

  ```python
  df.duplicated()
  ```

- Series에서 duplicate 값 찾기

  ```python
  df['c2'].duplicated()
  ```

- drop_duplicates() - 모든 컬럼을 비교

  ```python
  df.drop_duplicates()
  ```

  drop_duplicates() 함수로 duplicate된 값을 모두 삭제할 수 있다.

- drop_duplicates() - 특정 컬럼만을 비교

  ```python
  df.drop_duplicates(subset=['c2','c3'])
  ```

  `subset`에 설정된 column에서의 duplicate된 값을 삭제할 수 있다.





### 05. Data Type

Data를 Import하고 dtypes를 보면, 내가 생각했던것과 다르게 자료형이 들어간 경우가 있다.

```python
df = pd.read_csv('./data/auto-mpg.csv', header=None)
df.columns = ['mpg', 'cylinders', 'displacement', 'horsepower',
              'weight','acceleration','year','origin','name']
```







#### A. 데이터 타입 변경

#### B. 범주형 데이터

나이처럼 연속적인 데이터는 범주형 데이터로 처리하는게 훨씬 효율적인 경우가 있다.

> 예시)
>
> 0~13세 : 어린이
>
> 14~19세 : 청소년
>
> 20~40세 : 청년 

코드로 구현하기 위해 구간분할 이라는것을 알아야 한다.

🛸 **구간분할**

구간분할이란 연속적인 데이터를 일정한 구간으로 나누는 것이다.

>    \|-------(bin1)---------\|---------(bin2)---------\|----------(bin3)---------\|
>
> 경계1                     경계2                          경계3                         경계4
>
> 👉 경계 4개로 구간 3개가 만들어지는것을 확인할 수 있다.

이를 코드로 만들어보면

```python
```

🛸 **One-Hot Encoding**

구간분할을 한 데이터의 카테고리명은 우리가 알기 쉬운 언어로 잘 구분되어있다.

하지만 이것은 사람이 봤을 때의 이야기이고, 컴퓨터가 계산하기에는 적합하지 않다.

그래서 컴퓨터가 인식할 수 있는 형태로 바꾸는 방법 중 하나가 One-Hot Encoding이다.

dummy variable(더미변수) 를 주어 해당 특성의 유무를 0과 1로 표현하는 것이다.

```python
```



### 06. Normalization

정규화는 숫자 데이터의 상대적인 차이를 없애기 위해 필요하다.

DataFrame의 각 열이 가지고 있는 숫자 데이터의 상대적인 차이 때문에 머신러닝의 결과가 달라질 수 있다.

> 예시)
>
> 부동산 데이터 🏡
>
> 지은 연수가 1년인것과 40년인것 & 가격이 1억인것, 40억인것
>
> 사람이 생각하기에는 둘다 중요한 변수이지만, 컴퓨터가 생각할 때에는 큰 수에더 비중을 두게 될 수 있다.

숫자의 상대적인 크기 차이를 제거하기 위한 방법에는 표준화, Min-Max scaling 등이 있다.

🛸 **표준화 (Standardization)**

정규분포 z-score

🛸 **Min-Max Scaling**

Min-Max Scaling 공식
$$
x_{scaled} = {x - x_{min} \over x_{max}-x_{min}}
$$
min-max 공식을 사용하여 각 열을 정규화 해줄 수 있다.

하지만 min-max scaling은 이상치가 존재하면 취약한 단점이 있다.





### 07. 실습

Seaborn에서 제공하는 Titanic 데이터와 이전실습에 썼던 mpg 데이터를 실습에 사용한다.

Pandas는 그래프도구를 내장하고 있는데, 이 기능들은 matplotlib으로부터 차용된 것이다.

그래서 Pandas의 그래프도구를 사용하는 것 보다 matplotlib 사용법을 배워보는것이 좋다.

```python
# Seaborn 다운로드
> conda install seaborn
```

```python
#Seaborn 선언
import seaborn as sns
```

Seaborn도 다른 module처럼 자주쓰는 약어가 있다.



#### A. Data Loading

```python
import numpy as np
import pandas as pd
import seaborn as sns

# titanic data set loading
df = sns.load_dataset('titanic')
```











