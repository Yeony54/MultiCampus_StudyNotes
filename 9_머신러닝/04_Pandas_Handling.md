Machine learning

# Pandas Data Handling

DataFrame에 접근하는 방법을 알아보자

```python
my_dict = {'이름':['홍길동','아이유','김연아','신사임당'],
           '학과':['철학','수학','컴퓨터','국어국문'],
           '학년':[1, 2, 3, 4],
           '학점':[1.4, 2.5, 3.6, 4.0]}

df = pd.DataFrame(my_dict,
                 columns=['학과','이름','학점','학년'],
                 index=['one', 'two','three','four'])
display(df)
```

이전에 배운 dataframe 생성 방법으로 example 데이터를 생성하였다.

### 01. Column

1. Column 추출

   ```python
   print(df['이름'])
   ```

   컬럼명으로 indexing하면 하나의 컬럼을 추출할 수 있다.

   하나의 column을 추출하면 view로 추출된다.

   indexing을 하면 view가 생성되어 데이터가 공유된다.

2. Column의 view

   ```python
   my_name = df['이름']
   print(my_name)
   
   my_name['one']='강감찬'
   print(my_name)
   
   display(df)
   ```

   하나의 column을 추출하면 view가 생성되어 데이터가 공유되기 때문에 조심해야한다.

   예시처럼 값을 수정했을 때, 원본값이 달라지는것을 확인할 수 있다.

   원본값을 그대로 유지하고싶다면, .copy() 로 복사본을 만들어 사용할 수 있다.

3. 두개 이상의 column 추출

   ```python
   display(df[['이름','학년']])
   ```

   이전에 배웠던 Fancy Indexin 방법으로 추출하면 결과가 DataFrame으로 나온다

4. 특정 Column 값 수정

   ```python
   df['학년'] = 1        # broadcasting
   df['학년'] = [1, 2, 4, 4]
   display(df)
   ```

   DataFrame 또한 ndarray 방식이기 때문에, 숫자 하나를 입력하면 broadcasting 방식으로 계산한다.

5. Column 값 추가

   ```python
   df['나이'] = [20,22,30,25]
   display(df)
   ```

   새로운 컬럼 이름을 입력하고, 데이터를 추가한다.

6. 연산을 사용해 Column 추가

   ```python
   #  모든 사람의 학점을 20% 증가시켜서 '조정학점' 컬럼으로 저장
   df['조정학점'] = df['학점'] * 1.2
   display(df)
   ```

   이 연산도 또한 broadcasting 방식으로 계산된다.

7. Column 삭제

   ```python
   df.drop('학점', axis=1, inplace=True)
   display(df)
   ```

   **drop()**은 행이나 열을 삭제할 때 사용한다. 

   그렇기 때문에 행인지 열인지 알려주어야 한다.

### 02. Row

1. Row 추가

   ```python
   # 새로운 row 추가
   df.loc['five'] = ['영어영문','강감찬',3.7,1]
   df.loc['five',:] = ['영어영문','강감찬',3.7,1]
   ```

   row를 추가할 때에는 df.loc을 사용하여 추가할 수 있다.

   ```python
   # NaN값 발생
   df.loc['six',['학과','이름']]= ['물리학과','이순신']
   ```

   **NaN(Not a Number)** : 결치값(값이 없는 것을 나타내는 것을 의미)

   👀 실수를 입력하면 원래 정수였던 컬럼이 실수로 바뀌게 된다.
   내부적인 요인으로 정수를 입력해도 실수로 들어가는데, 뭔지는 잘모르겠다

2. Row 삭제

   ```python
   # row 삭제
   display(df.drop('three', axis=0, inplace=False))
   ```



### 03. Indexing

#### A. 기존 indexing

이전에 했던 indexing으로 DataFrame을 handling해보자

1. Column indexing

   ```python
   print(df['이름']) 						# Series
   # print(df['이름':'학년']) 				   # Error 
   display(df[['이름', '학과', '학년']]) 	  # DataFrame - Fancy indexing
   ```

   하나의 column 명을 주었을 때에는 Seires의 형태로 나오게 된다.

   컬럼에 대한 slicing은 Error가난다.

   Fancy indexing이 가능하다.

2. Row indexing

   A) 숫자 index로 indexing

   ```python
   # print(df[0]) 			# Error 
   display(df[0:2]) 		# slicing
   # display(df[[0,2]]) 	# Error
   ```

   숫자 index로는 slicing은 가능하지만 단일 indexing, Fancy indexing은 하지 못한다.

   B) 지정 index로 indexing

   ```python
   # print(df['one'])				# Error
   display(df['one':'three']) 		# slicing은 가능
   # display(df[['one','three']])  # Error
   ```

   마찬가지로 slicing은 가능하지만 단일 indexing, Fancy indexing은 하지 못한다.

#### B. loc, iloc indexing

원래하던 df[ ] 방법의 indexing으로는 한계가 있는것이 많다.

그래서 기존 indexing은 column indexing 에 사용하고, row indexing은 다른걸로 사용한다.

👉 대신 df.loc[ ] 을 사용해서 indexing을 할 수 있다.

이 방법은 row, column 모두 indexing할 수 있다.

pandas에는 loc, iloc 두가지가 있다.

1. loc

   - DataFrame의 행이나 컬럼에 label이나 boolean array로 접근한다.
   - location의 약어로, 인간이 읽을 수 있는 label 값으로 데이터에 접근하는 것이다.

2. iloc

   - DataFrame의 행이나 컬럼에 인덱스 값으로 접근
   - integer location의 약어로, 컴퓨터가 읽을 수 있는 indexing 값으로 데이터에 접근하는 것이다.

3. df.loc[ ] 예시

   ```python
   # 단일 row 추출
   print(df.loc['one'])				# Series
   
   # slicing
   display(df.loc['one':'three']) 		# Dataframe
   
   # Fancy indexing
   display(df.loc[['one','three']]) 	# Dataframe
   ```

   단일 추출을 할 때에는 column 명이 index로, one이 value로 만들어진 series가 추출된다.

4. df.iloc[ ] 예시

   ```python
   # 단일 row 추출
   print(df.iloc[0])
   
   # slicing
   display(df.iloc[0:3])
   
   # Fancy indexing
   display(df.iloc[[0,3]])
   ```

5. row , column indexing 동시에

   ```python
   display(df.loc['two':'three','학과':'이름'])
   display(df.loc['two':'three','학과'])
   display(df.loc['two':'three',['학년','이름']])
   ```

   다양하게 활용해 볼 수 있다.

#### C. Boolean indexing

Boolean indexing은 True, False로 이루어진 Boolean mask를 사용해서 indexing을 하는 방법이다.

```python
# Boolean indexing 예시

my_dict = {'이름':['홍길동','아이유','김연아','신사임당'],
           '학과':['철학','수학','컴퓨터','국어국문'],
           '학년':[1, 2, 3, 4],
           '학점':[1.4, 2.5, 3.6, 4.0]}

df = pd.DataFrame(my_dict,
                 columns=['학과','이름','학점','학년'],
                 index=['one', 'two','three','four'])
display(df)


# 학점이 3.0 이상인 학생의 학과와 이름을 출력하세요

display(df.loc[df['학점']>=3.0,['학과','이름']])
df[df['학점']>=3.0][['학과','이름']]
```



### 04. DataFrame 함수

1. head(), tail()

   DataFrame 안의 데이터를 앞, 뒤에서 5개(기본)를 추출

   ```python
   head(3) # 앞에서 3개 추출
   ```

2. shape()

   DataFrame의 shape를 출력

3. info()

   DataFrame의 기본정보 출력

4. count()

   Series로 count 결과를 return

5. value_counts()

   series에 대해서 unique value 의 개수를 알려준다.

   ```python
   df['origin'].value_counts()
   ```

   > ❓ Nan 값이 있으면 어떻게 동작하는가
   >
   > 기본적으로 NaN 값을 포함해서 계산한다.
   >
   > 옵션을 주어 NaN을 제외하고 수행 가능
   >
   > ```python
   > print(df['origin'].value_counts(dropna=True))
   > ```

6. unique()

   Series에 대해서 unique한 값을 알려줌

   ```python
   print(df['origin'].unique())
   ```

7. isin()

   Boolean mask를 만들기위해서 많이 사용한다.

   ```python
   df[df['origin'].isin([3])]
   df.loc[df['origin'].isin([3]),:]
   ```

### 05. 정렬

```python
import numpy as np
import pandas as pd

# 난수의 재현성 확보
np.random.seed(1)
df = pd.DataFrame(np.random.randint(0,10,(6,4)),
                  columns=['A','B','C','D'],
                  index=pd.date_range('20220101', periods=6))
display(df)
```

numpy를 사용하여 random한 정수를 사용한 DataFrame을 만들어주었다.

정렬을 해보기 전에 섞는 방법부터 알아본다.

#### A. permutation()

numpy에 이미 shuffle이라는 섞는 함수가 있다.

하지만 shuffle은 원본데이터를 변경하기 때문에, mutable operation을 지원하지 않는 DataFrame index 에서 사용할 수 없다.

즉, DataFrame에서는 index 자체를 변경할 수 없기 때문에 shuffle을 못쓴다는 말이다.

그래서 여기서는 permutation을 쓴다.

```python
random_index = np.random.permutation(df.index)
```

이 함수는 섞을 때 원본을 변경하지 않고 복사본을 만든다.

#### B. reindex()

reindex()는 index를 원하는대로 재설정하는 함수이다.

```python
df2 = df.reindex(index=random_index,
                 columns=['B', 'A', 'D', 'C'])
```

permutation으로 섞었던 index대로 index를 설정하고, columns는 임의로 설정해 주었다.

#### C. sort_index()

index기반으로 정렬시키는 방법이다.

```python
display(df2.sort_index(axis=1, ascending=True)) # 컬럼을 정렬
display(df2.sort_index(axis=0, ascending=True)) # 행을 정렬
```

axis를 설정해주어 컬럼을 변경할지, 행을 변경할지 결정할 수 있다.

#### D. sort_values()

value 기반으로 정렬시키는 방법이다.

```python
display(df2.sort_values(by=['B'], ascending=True)) # 특정 컬럼의 값으로 행을 정렬
```

by 속성을 사용하여 그 컬럼 내의 value를 기준으로 정렬시킨다.







