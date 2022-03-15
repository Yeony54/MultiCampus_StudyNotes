머신러닝

# Machine learning

### 00. 기본 설정

새로운 가상환경만들기

```powershell
# 생성되어있는 가상환경 확인
> conda info --envs	

# 가상환경 생성
> conda create -n machine python=3.8 openssl

# 가상환경 실행
> conda activate machine

# jupyter notebook 설치
> conda install nb_conda          

# jupyter notebook 실행
> jupyter notebook

# 환경설정
# home>.jupyter>jupyter_notebook_config.py
# 393번째 라인 주석해제 
# c.NotebookApp.notebook_dir = '/jupyter_home' 변경
> jupyter notebook --generate-config

# jupyter_home에서 jupyter notebook에서 실행되어야 한다.
```

jupyter notebook 새로운 파일생성

new > 가상환경으로 만들기 > 이름바꾸기 > 학습하기

---

### 01. Data Handling : Numpy

대부분의 데이터는 가공되지 않은 raw 데이터이다.

데이터는 잘 정리된 데이터든, 정리되지 않은 데이터든 결과가 나온다.

얻은 데이터를 잘 가공해서 유의미한 결과를 얻어야 한다.

pandas, numpy를 사용하여 데이터를 가공한다.

#### A. Numpy

Numpy는 수치계산을 용이하게 하기 위한 python module이다.

대용량의 다차원 배열과 matrix(행렬)연산을 쉽게 할 수 있다.

Numerical Python => Numpy

#### B. ndarray

Numpy는 단 하나의 자료구조를 제공한다 => ndarray(n-dimesional array)

darray 는 python의 list와 상당히 유사하다.

ndarray는 차원의 개념이 있다. (파이썬의 list는 차원의 개념이 없다.)

list는 여러 다른 타입의 데이터가 저장될 수 있지만, ndarray는 같은 데이터 타입만 저장된다.

Numpy 는 외장 module이기 때문에 설치해서 사용해야 한다.

```powershell
# 가상환경 실행
> conda activate machine

# numpy 설치
> conda install numpy
```

#### C. matplotlib

많은 숫자들을 한눈에 볼 수 있게 그려주는 graph library

```powershell
# matplotlib 설치
> conda install matplotlib
```

---

### 02. Numpy

#### **A. 1차원 배열**

```python
import numpy as np

# python list
a = [1, 2, 3, 4]   # a = [1, 2, 3, 4, True, 'Hello'] 가능
print(a)           # [1, 2, 3, 4]
print(type(a))     # <class 'list'>

# Numpy의 ndarray
arr = np.array([1, 2, 3, 4])
print(arr)         # [1 2 3 4] => 1차원
print(type(arr))   # <class 'numpy.ndarray'>
print(arr.dtype)   # int32 : arr의 type을 조회
```

list는 컴마(,)로 구분되지만, ndarray는 빈칸으로 구분된다.

```python
arr = np.array([1, 2.3, 3, 4])
print(arr.dtype)   # float64

arr = np.array([1, 2, 3, 4, 'Hello'])
print(arr.dtype)   # <U32
```

>  ndarray는 요소의 데이터 타입을 이용해서 dtype을 설정한다.

ndarray는 같은 데이터 타입이어야 하기 때문에 내부적으로 모두 같은 데이터 타입으로 바꾸어 준다.

정수를 실수, 문자열로 바꾸어서 표현해 준것을 확인할 수 있다.

👀 정수냐, 실수냐에 따라서도 분석 결과값이 달라지기 때문에, 주의가 필요하다.

#### **B. 다차원 배열**

```python
# 중첩 리스트
my_list = [[1, 2, 3], [4, 5, 6]]
print(my_list)          # [[1, 2, 3], [4, 5, 6]]
print(my_list[1][1])    # 5

# ndarray
arr = np.array([[1, 2, 3], [4, 5, 6]])
print(arr)              # [[1 2 3] 
                        # [4 5 6]]
print(arr[1, 1])     	# 5 (추천)
print(arr[1][1])        # 5 (똑같이 나오지만 위에것을 추천)
```

list와 달리 ndarray에서는 2차원으로 출력된것을 확인할 수 있다.

행과 열을 찾아 사용하는 것이기 때문에 list에서 사용하는 방식도 사용 가능하지만, ndarray 만의 방식을 사용하는 것을 추천한다.

#### **C. dtype 지정하여 ndarray 생성**

```python
arr = np.array([[1, 2, 3], [4, 5, 6]])
print(arr.dtype)        # int32

arr = np.array([[1, 2, 3], [4, 5, 6]],
              dtype=np.float64)
print(arr.dtype)       	# float64
```

dtype은 자동으로 생성되지만, 사용자가 데이터타입을 지정해서 생성할 수 있다.

#### **D. ndarray의 차원 관련 속성**

```python
my_list = [1, 2, 3, 4]
arr = np.array(my_list)
print(arr)        # [1 2 3 4]
print(arr.dtype)  # int32
print(arr.ndim)   # 1
print(arr.shape)  # (4, )
    
my_list = [[1, 2, 3], [4, 5, 6]]
arr = np.array(my_list)
print(arr.ndim)   # 2
print(arr.shape)  # (2, 3)
```

**dtype** : ndarray의 data type을 알려준다.

**ndim** : ndarray의 차원수를 숫자로 알려준다.

**shape** : 차원과 요소수를 tuple로 알려준다.

1차원의 예제를 보면, tuple안에 요소가 1개, 그리고 그 값이 요소의 개수이므로 `(4, ) `가 결과로 나온다.

👀 요소가 하나인 튜플은 `(n, )`로 표기한다.

**(2, 2, 3)형태의 ndarray 만들어보기**

```python
my_list = [[[1,2,3],
            [1,2,3]],
           [[1,2,3],
            [1,2,3]]]
arr = np.array(my_list)
print(arr.shape)  # (2, 2, 3)
```

2차원이 2개이면 3차원이 된다.

```python
arr = np.array([1.2, 2.3, 3, 4, 5.7])
print(arr.dtype)     # float64

new_arr = arr.astype(np.int32)
print(new_arr)       # [1 2 3 4 5]

new_arr = arr.astype(np.str_)
print(new_arr)       # ['1.2' '2.3' '3.0' '4.0' '5.7']
```

**astype** : 내가 원하는 데이터 타입으로 변경

#### E. ndarray를 만드는 함수

```python
my_list = [1, 2, 3]
arr = np.array(my_list) # list를 이용해서 ndarray를 생성

arr = np.zeros((3,4))
print(arr)

arr = np.ones((3,4))
print(arr) 

arr = np.empty(((2,3,3)))
print(arr)

arr = np.full((2,3), 
              7, 
              dtype=np.float64)
print(arr)
```

**zeros** : 주어진 shape에 대한 ndarray를 생성하고 0으로 채운다

**ones** : 주어진 shape에 대한 ndarray를 생성하고 1로 채운다.

**empty** : 주어진 shpae에 대한 ndarray를 생성하고 값을 채우지 않는다.
안에 쓰레기 값이 들어갈 수 있다. but 상대적으로 ndarray를 빠르게 생성할 수 있다.

**full** : 주어진 shpae에 대한 ndarray를 생성하고 지정한 값을 채운다.

👀인자가 많은 경우에는 내려쓰는것이 가독성이 좋다.

```python
arr = np.array([[1, 2, 3], [4, 5, 6]],
                dtype=np.int32)
print(arr)		# [[1 2 3]
 				#  [4 5 6]]

new_arr = np.zeros_like(arr)
print(new_arr)	# [[0 0 0]
 				#  [0 0 0]]
```

**__like** : 인자의 shape을 모방해서 함수를 수행한다.

```python
# python의 range
a = range(1,10)
print(a)           # range(1, 10)

# numpy 의 arange
arr = np.arange(1,10)
print(arr)         # [1 2 3 4 5 6 7 8 9]

arr = np.arange(1.3, 10.1, 2)
print(arr)         # [1.3 3.3 5.3 7.3 9.3]
```

**arange** : python의 range와 비슷한 기능을 가진다.

python의 range는 의미만을 갖는다.

하지만 numpy의 arange는 실제 값을 가진 ndarray가 생성된다.

```python
arr = np.linspace(0, 10, 11)
print(arr)     # [ 0.  1.  2.  3.  4.  5.  6.  7.  8.  9. 10.]

arr = np.linspace(0, 10, 6)
print(arr)     # [ 0.  2.  4.  6.  8. 10.]
```

**np.linspace(start, stop, num)**

균일한 간격의 데이터를 생성해서 ndarray를 만들어내는 함수

start : 시작숫자, stop : 끝숫자 → 둘다포함

num : 그 안에 균일한 간격으로 몇개의 숫자가 들어갈지를 나타낸다.

원소의 간격은 `(stop-start)/(num-1)`로 계산한다.

#### F. ndarray를 만드는 함수 : 난수

👀 난수를 마음대로 뽑으면 편향이 생겨 좋지 않기 때문에, 골고루 뽑는 방법을 사용한다.

random값을 이용해서 ndarray를 만들어내는 방법

```python
import numpy as np
import matplotlib.pyplot as plt

mean = 50
std = 2

arr = np.random.normal(mean, std, (100000,))
plt.hist(arr, bins=100)
plt.show()
```

**np.random.normal()** : ndarray를 만들어 그안의 데이터는 난수로 채운다.

평균, 표준편차 값을 입력받아 **정규분포 실수 표본을 추출**한다.

```python
arr = np.random.rand(100000)
plt.hist(arr, bins=100)
plt.show()
```

**np.random.rand()** : ndarray를 만들어 그 데이터는 난수로 채운다.

`[0,1)` 0부터 1사이 (0은 포함, 1은 불포함)의 실수형 난수를 **균등분포에서 추출**한 후 ndarray 생성

normal 에서 처럼 평균, 표준편차를 필요로 하지 않고, `[0,1)` 사이의 값을 추출한다.

```python
arr = np.random.randn(100000)
plt.hist(arr, bins=100)
plt.show()
```

**np.random.randn()** : ndarray를 만들어 그 안에 데이터는 난수로 채운다.

표준정규분포 : 정규분포에서 평균은 0으로 고정되어 있고, 표준편차가 1인 정규분포를 말한다.

randn() 함수는 **표준 정규분포에서 난수를 추출**한다.

```python
np.random.randint(1, 100, (100000,))
plt.hist(arr, bins=100)
plt.show()
```

**np.random.randint()** : ndarray를 만들어 그 안에 데이터는 난수로 채운다.

low, high 값을 입력받아 **균등분포에서 정수형 난수를 추출**한다.

👀 이친구만 정수형 난수를 추출하고 나머지는 실수형 난수를 추출한다.

![image-20220315135107217](../../../../AppData/Roaming/Typora/typora-user-images/image-20220315135107217.png)