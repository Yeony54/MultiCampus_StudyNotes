Machine learning

# Pandas

### 00. 기본 설정

```powershell
# 가상환경 실행
> conda activate machine

# pandas 설치
> conda install pandas
```

<br>

---

<br>

### 01.Pandas

Pandas의 자료구조에는 Series와 Dataframe이 있다.

- Series : 1차원 자료구조로 같은 data type만 저장이 가능하다
- Dataframe : 2차원 자료구조로 Series의 집합이다.

```python
import numpy as np
import pandas as pd
```

pandas도 numpy처럼 관용적으로 쓰는 alias가 있다.

<br>

---

<br>

### 02. Series

#### A. Series 생성

Series의 특징으로 index를 변경할 수 있다는 점이 있다.

만약 index를 지정해서 Series를 만들면 숫자 index는 내부에 숨어있는채로 남게 된다!<br>

```python
# ndarray
arr = np.array([1, 2, 3, 4, 5], dtype=np.float64)
print(arr)

# series
s = pd.Series([1, 2, 3, 4, 5], dtype=np.float64)
print(s)         # index와 value가 같이 출력
print(s.values)  # [1. 2. 3. 4. 5.] ndarray
print(s.index)   # RangeIndex(start=0, stop=5, step=1) => pandas의 객체
```

**.values** 속성으로 series의 값을 출력할 수 있다.

**.index** 속성으로 출력하면 pandas의 객체로 Index가 만들어진 것을 확인할 수 있다.<br><br>

#### B. Series 생성 : index 속성

```python
s = pd.Series([1, 2, 3, 4, 5],
             dtype=np.float64,
             index=['c', 'b', 'a', 'k', 'hello'])
print(s)
print(s[0])   		# 숫자 index
print(s['c']) 		# 지정 index
# print(s[100]) 	# Error
# print(s['haha']) 	# Error
```

Series의 index를 문자와 문자열로 지정해서 만들었다. 

숫자는 내부적으로 남아있기 때문에 숫자 index로도 접근이 가능하다.<br>

❓ 만약 index를 숫자로 지정해주면 어떻게 될까

```python
s = pd.Series([1, 2, 3, 4, 5],
             dtype=np.float64,
             index=[0, 2, 100, 6, 9])

print(s)
print(s[0])  
# print(s[1]) 		# Error
print(s[100])		# 3.0
```

이번에는 Series의 index를 숫자로 만들어주었다.

👀 index를 숫자로 지정해주게 되면 원래 있던 숫자 index가 사라져서 오류가 난다.<br>

❓ 같은 index가 존재하면 어떻게 될까?

```python
s = pd.Series([1, 2, 3, 4, 5],
             dtype=np.float64,
             index=['c', 'b', 'c', 'k', 'm'])

print(s)
print(s['c']) 
```

Series의 index에 중복되는 값을 지정해주었다.

중복되는 값으로 index에 접근 할 때 오류는 생기지 않는다.

하지만 여러개의 값에 접근하기 때문에 Series로 출력된다.

일반적으로 index는 unique한 값을 사용하는것이 원칙이니 같은 index가 없도록 주의하자.<br><br>

#### C. slicing

indexing은 ndarray나 list와 비슷하게 사용한다.

하지만 slicing을 사용할 때에는 주의해야 한다.<br>

```python
s = pd.Series([1, 2, 3, 4, 5],
             dtype=np.float64,
             index=['c', 'b', 'c', 'k', 'm'])

print(s)
print(s[0:3])  		# 숫자 index를 이용한 slicing
print(s['c':'k']) 	# 지정 index를 이용한 slicing
```

Seires의 0번째부터 3번째 까지를 출력하고 싶다.

숫자 index를 사용할 때에는 이전에 slicing을 했을 때 처럼 사용이 가능하다.

하지만 지정 index를 사용할 때에는 그 index까지 포함해서 나오기 때문에 주의해야 한다.<br>

```python
# 짝수만 뽑아내는 Boolean indexing
print(s[s % 2 == 0])

# Fancy indexing
print(s[[0, 2]])
```

ndarray로 구성되어 있기 때문에 Boolean indexing, Fancy indexing이 모두 가능하다.<br>

```python
# Series를  만드는 또 다른 방법
# dictionary를 이용해서 Series를 생성

my_dict = {'서울': 1000,
           '인천': 500,
           '제주': 100}

s = pd.Series(my_dict)
print(s)
```

<br>

#### D. Series 예제

📄 **예제 1**

A 공장의 2020년 1월 1일 부터 10일간 생산량을 Series로 저장

생산량은 평균이 50이고 표준편차가 5인 정규분포에서 랜덤하게 생성(정수), index는 날짜

> 정규분포에서 랜덤하게 추출할 것이기 때문에 numpy를 사용
>
> 날짜를 쓰는것은 까다롭기 때문에 제공하는 module로 사용

```python
import numpy as np
import pandas as pd
from datetime import datetime, timedelta

start_day = datetime(2020, 1, 1)

# list comprehension
# my_list = [tmp for tmp in range(100)]
my_list = [int(x) for x in np.random.normal(50, 5, (10,))]

s1 = pd.Series(my_list,
             index=[start_day + timedelta(days=x) for x in range(10)])
```

**datetime**을 사용하여 start_day를 생성해준다.

**list comprehension** : list 생성 시 for, if문을 사용하여 생성할 수 있다.
정규분포에서 10개의 랜덤한 값을 추출하여 list를 만들어준다.

**Series**의 속성으로 위에서 만든 list를 주고, index로 start_day comprehension을 부여해 준다.
여기서 **timedelta**는 datetime 변수에 1일씩 증가시켜주는 module이다.<br>

📄 **예제 2**

B 공장의 2020년 1월 5일 부터 10일간 생산량을 Series로 저장

생산량은 평균이 70이고 표준편차가 8인 정규분포에서 랜덤하게 생성(정수), index는 날짜

A공장과 B공장의 일일 생산 합을 구하자

> A 공장의 생산량을 랜덤하게 생산했던것과 같이 B를 생성하고, 더해본다.

```python
import numpy as np
import pandas as pd
from datetime import datetime, timedelta

start_day_A = datetime(2020, 1, 1)
start_day_B = datetime(2020, 1, 5)

s1 = pd.Series([int(x) for x in np.random.normal(50, 5, (10,))],
             index=[start_day_A + timedelta(days=x) for x in range(10)])

s2 = pd.Series([int(x) for x in np.random.normal(70, 8, (10,))],
             index=[start_day_B + timedelta(days=x) for x in range(10)])

print(s1+s2)
```

Series는 index를 기반으로 연산이 수행되기 때문에 자동으로 날짜별로 합계가 나온것을 확인할 수 있다.

이때, 1월 1일부터 1월 4일까지의 합은 NaN으로 출력이 되는데, 이는 B공장이 그 날짜에 대한 생산량을 가지고 있지 않기 때문이다.

이처럼 두개가 동시에 데이터를 갖고있지 않은 데이터는 NaN으로 연산이 불가능하다고 출력된다.<br><br>

---

<br>

### 03. Dataframe 기본

Dataframe은 Series의 집합이라고 볼 수 있다.

Series의 특징은 같은 data type만 저장이 가능하다는 것이다.

그래서 하나의 열 즉 Series의 데이터는 같은 data type만 저장이 가능하며, 다양한 Series들이 모여 DataFrame을 만들 수 있다.<br>

```python
import numpy as np
import pandas as pd

my_dict = {'이름': ['홍길동', '아이유', '김연아', '신사임당'],
           '학년': [4, 3, 2, 1],
           '학점': [1.5, 2.4, 3.9, 3.2]}

df = pd.DataFrame(my_dict)
display(df)

print(df.shape) # (4, 3)
print(df.values) # 2차원 ndarray
print(df.size) # DataFrame안의 요소 개수 => 12
print(df.ndim) # 2
print(df.index) # 행 index, RangeIndex(start=0, stop=4, step=1)
print(df.columns) # 열 index, Index(['이름', '학년', '학점'], dtype='object')
```

> series 는 print 대신 display()를 사용하여 정돈된 테이블을 출력할 수 있다.

**shape** : DataFrame의 shape속성을 출력해준다.

**values** : my_dict로 삽입했던 데이터를 2차원 ndarray로 출력해준다.

**size** : DataFrame안의 총 요소 개수를 출력해준다.

**ndim** : DataFrame의 차원 개수를 출력해준다.

**index** : 행 index를 출력해 준다.

**columns** : 열 index를 출력해준다.<br>

```python
df.index.name = '학번'
df.columns.name = '학생정보'
display(df)
```

index와 columns의 name 속성에 접근하여 name을 설정해 줄 수 있다.<br>

```python
# DataFrame의 column명과 index명을 변경

new_df = df.rename(columns={'이름':'학생이름',
                           '학점':'평균평점'},
                  index={0:'one'},
                  inplace=False)
display(new_df)
```

**rename( )** : 각 column명, index명을 바꿔줄 수 있다. dictionary 형태로 전달해준다.

여기서 **inplace** 는 원본에 저장할지 안할지를 작성하는 속성이다.

inplace = True 이면 원본에 저장하고 복사본을 만들지 않는다.
inplace = False 이면 원본에 저장하지 않고, 복사본으로 만든다.<br>

```python
# DataFrame의 특정 column을 index로 설정

my_dict = {'이름': ['홍길동', '아이유', '김연아', '신사임당'],
          '학년': [4, 3, 2, 1],
          '학점': [1.5, 2.4, 3.9, 3.2]}

df = pd.DataFrame(my_dict)
display(df)

new_df = df.set_index('이름',
                     inplace=False)
display(new_df)
```

set_index를 사용하면 특정 column을 사용해서 index로 만들 수 있다.<br><br>











