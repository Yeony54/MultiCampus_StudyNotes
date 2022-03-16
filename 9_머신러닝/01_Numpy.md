Machine learning

# Numpy

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

데이터는 잘 정리된 데이터든, 정리되지 않은 데이터든 분석 결과를 나타낼 수 있다.

얻은 데이터를 잘 가공해서 유의미한 결과를 얻어야 한다.

pandas, numpy를 사용하여 데이터를 가공한다.

#### A. Numpy

Numpy는 수치계산을 용이하게 하기 위한 python module이다.

대용량의 다차원배열, 그리고 2차원 matrix 연산을 쉽고 빠르게 할 수 있다.

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

<br>

---

### 02. Numpy : ndarray

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

---

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

---

### 03. Numpy : random ✨

#### A. ndarray를 만드는 함수 : random

👀 난수를 마음대로 뽑으면 편향이 생겨 좋지 않기 때문에, 골고루 뽑는 방법을 사용한다.

random값을 이용해서 ndarray를 만들어내는 방법, 실행할 때마다 값이 바뀐다.

```python
import numpy as np
import matplotlib.pyplot as plt

mean = 50
std = 2

arr = np.random.normal(mean, std, (100000,))
plt.hist(arr, bins=100)
plt.show()
```

**np.random.normal()** : 평균, 표준편차 값을 입력받아 **정규분포 실수 표본을 추출**한다.

```python
arr = np.random.rand(100000)
plt.hist(arr, bins=100)
plt.show()
```

**np.random.rand()** : `[0,1)` 0부터 1사이 (0은 포함, 1은 불포함)의 실수형 난수를 **균등분포에서 추출**한다.

normal 에서 처럼 평균, 표준편차를 필요로 하지 않고, `[0,1)` 사이의 값을 추출한다.

```python
arr = np.random.randn(100000)
plt.hist(arr, bins=100)
plt.show()
```

**np.random.randn()** : randn() 함수는 **표준 정규분포에서 난수를 추출**한다.

표준정규분포 : 정규분포에서 평균은 0으로 고정되어 있고, 표준편차가 1인 정규분포를 말한다.

```python
np.random.randint(1, 100, (100000,))
plt.hist(arr, bins=100)
plt.show()
```

**np.random.randint()** : low, high 값을 입력받아 **균등분포에서 정수형 난수를 추출**한다.

👀 이친구만 정수형 난수를 추출하고 나머지는 실수형 난수를 추출한다.

```python
arr = np.random.random((100000,))
plt.hist(arr, bins=100)
plt.show()
```

**np.random.random()** : [0,1) 사이 **균등분포**에서 실수형 난수를 추출

👀 rand와 다른점은 함수의 인자로 **shape**를 주어준다는 것이다.

---

#### B. 기억해야 하는 random관련 함수

```python
np.random.seed(1)
arr = np.random.randint(1,10,(5,))
print(arr)
```

**seed** : 랜덤값을 도출하는 초기값 설정

랜덤값도 사실은 프로그램 알고리즘에 의해서 추출되는 값이다.

랜덤값의 알고리즘에 넣을 수를 고정하는 역할을 하는것이 seed이다.

랜덤값을 도출하는 초기값을 고정하면 항상 같은 랜덤값을 얻을 수 있어 난수의 재현성을 확보할 수 있다.

seed값을 없애려면 None을 입력하면 된다!!

```python
arr = np.arange(1,10)
print(arr)			# [1 2 3 4 5 6 7 8 9]

new_arr = np.random.shuffle(arr)
print(new_arr)     	# None
print(arr)			# [7 4 1 3 9 8 6 5 2]
```

**shuffle** : 데이터를 순서를 바꾼다.

복사본을 만들지 않고 원본을 바꾸기 때문에 조심해야한다.

```python
arr = np.random.choice(np.array([1, 2, 3, 4, 5, 6]), 3) # replace=True
print(arr)

arr = np.random.choice(np.array([1, 2, 3, 4, 5, 6]), 3, p=[0.1, 0.2, 0.2, 0.5, 0])
print(arr)
```

**sampling** : 여러개 중에 random하게 선택한다.

**np.random.choice(a, size, replace, key)**

- a : 배열(ndarray)

- size : 숫자 (뽑을 숫자)

- replace : True - 한번 뽑은것을 또 뽑는다. , False - 한번뽑은것은 뽑지 않는다.

  ​				아무런 속성도 주지 않는다면 replace = True 이다.

- p : 확률 (각 데이터가 선택될 수 있는 확률)

---

### 04. shape과 관련된 함수 ✨

ndarray의 shape과 관련된 중요한 함수들

```python
arr = np.array([[1, 2, 3, 4, 5, 6], [7, 8, 9, 10, 11, 12]])
print(arr)         # 2차원의 ndarray
print(arr.shape)   # (2, 6)

new_arr = arr.reshape(3, 4)
print(new_arr)

new_arr[0,0] = 100
print(new_arr)
print(arr)         # new_arr에서 바꿨는데 arr에서도 바뀐것을 확인할 수 있다.        
```

**reshape()** : ndarray의 shape을 reshape하여  차원을 바꿀 수 있다.

❗❗ shape을 바꿔서 새로운 ndarray를 만드는 것이아니다.

shape을 바꿔서 원래 ndarray의 데이터를 다르게 보여주는 view를 생성하는 것이다.

그래서 reshape을 한 view에서 변경하게되면, 원본도 변경되는것을 확인할 수 있다.

❕❕ 만약 모양을 바꾸어서 새로운 ndarray를 생성하고 싶으면, **.copy()** 를 이용한다.

```python
new_arr = arr.ravel()
print(new_arr)
```

**ravel()** : 1차원의 view를 만들 수 있다.

reshape() 는 원하는shape의 view를 만들 수 있고, ravel() 은 무조건 1차원의 view를 만든다.

1차원을 만들때에는 계산할 필요 없이 ravel() 을 쓰면 된다~

```python
new_arr = arr.resize(3,5)   # 복사본을 만들지 않는다.
print(new_arr)         		# None
print(arr)
```

**resize()** : reshape와 비슷한 기능을 하면서 약간 다르다.

resize는 복사본을 만들지 않고, 원본을 변경한다. view도 만들지 않는다.

reshape는 요소수가 맞지 않으면 view가 생성되지 않는다. (오류가 난다.)

resize() 는 요소의 개수가 맞지 않아도 수행히 가능하다.  => 데이터의 유실이 일어날 위험이 있다.

---

### 05. Indexing, Slicing

#### A. 기본 Indexing, Slicing

```python
arr = np.arange(10,15,1)   # [10 11 12 13 14]

print(arr[0])    # 10
print(arr[1:3])  # [11 12]
print(arr[1:-1]) # [11 12 13]
```

기본적인 indexing과 기본적인 slicing은 python의 list와 동일하다.

```python
arr = np.arange(0,12).reshape(3,4)
print(arr)

print(arr[1,2])      # 6
print(arr[1])        # [4 5 6 7]
print(arr[1,:])      # [4 5 6 7]
print(arr[1:,2:])    # [[6 7]
                     #   8 9]]
```

1차원에 대한 indexing과 slicing이 다차원으로 확장되었다.

#### B. Bullean , Fancy Indexing ✨

중요한 indexing 방법✨

우선 bullean indexing 전에 ndarray의 연산에 대해서 알아보자.

```python
# python list 연산
list1 = [1, 2, 3]
list2 = [4, 5, 6]
print(list1 + list2) # [1, 2, 3, 4, 5, 6]

# ndarray
arr1 = np.array([1, 2, 3])
arr2 = np.array([4, 5, 6])
print(arr1+arr2) # [5 7 9]

# broadcasting 예시
arr1 = np.array([1, 2, 3])
arr1 + 4   # [4 4 4] 내부적으로 1차원으로 올려서 broadcasting을 한다.
```

python에서 list `+` 연산을 하게 되면 list가 연결된다.

ndarray에서 list 연산을 하게 되면 같은 shape에 대해서만 연산이 가능하다.

ndarray 연산에서 만약 shape를 맞출 수 있으면, 내부적으로 broadcasting이 되어 차원을 맞춰준다.

```python
np.random.seed(1)

arr = np.random.randint(0, 10, (10,))
print(arr) 				# [5 8 9 5 0 0 1 7 6 9]

print(arr + 10)  		# [15 18 19 15 10 10 11 17 16 19]
print(arr % 2)   		# [1 0 1 1 0 0 1 1 0 1]
```

ndarray는 `+`, `-`, `*`, `/ ` 사칙연산을 수행할 수 있다.

```python
print(arr % 2 == 0) 	# [False  True False False ... False]
```

사칙연산에 비교연산자를 추가하여 True와 False로만 이루어진 ndarray를 얻을 수 있다. 
이를 **Boolean mask**라고 표현한다.

```python
my_mask = (arr % 2 == 0)
print(arr[my_mask])  	# [8 0 0 6] 
```

**Bullean indexing** : indexing 방법중 하나로, boolean mask 를 이용해서 indexing 하는 방법이다.

True, False로 이루어진 boolean mask를 조건을 가지고 걸러내는 indexing 방법이다.

❗❗ loop를 돌며 처리하기 힘든 데이터를 다루기 때문에, bullean indexing을 적극활용해야 한다.

```python
arr = np.array([1,2,3,4,5,6])
print(arr)

print(arr[3])  		# 4 => indexing
print(arr[3:]) 		# [4 5 6] => slicing
print(arr[[3, 5]]) 	# [4 6] => fancy indexing
```

**Fancy indexing** : index로 구성된 list를 전달하여 indexing 하는 방법이다.

```python
arr = np.arange(0,12,1).reshape(3,4)
print(arr)
print(arr[0:2, 1:])     # [[1 2 3]
                        # [5 6 7]]
print(arr[0:2, [1,3]])  # [[1 3]
                        # [5 7]]
    
print(arr[[0,1],[1,3]]) 			# [1 7] ?????
print(arr[np.ix_([0,2], [1,3])])	# [1 7]
									# [ 1 11]
```

2차원 배열도 fancy indexing으로 원하는 부분을 자를 수 있다.

하지만, numpy의 내부 구조로 인해 행과 열 모든 차원에 대해서 fancy indexing을 할 수 없는 현상이 일어난다.

이런 경우를 위해 `ix_()` 함수를 제공한다.

이 함수를 사용하면 원하는 indexing을 할 수 있다.

---

### 06. ndarray의 사칙연산

#### A. plus 연산

ndarray 간의 사칙연산을 할 때에는 shape끼리 벡터 연산을 하게 된다.

만약 shape이 다르다면 오류가 생긴다.

하지만 shape이 다를때도 만약  shape을 맞출 수 있으면 연산이 가능하다.

```python
import numpy as np

arr1 = np.array([1, 2, 3])  	# (3,)
arr2 = np.array([4, 5, 6])  	# (3,)
print(arr1 + arr2)          	# [5 7 9]

# arr1 = np.array([1, 2, 3, 4])   # (4,)
# arr2 = np.array([4, 5, 6])  	  # (3,)
# print(arr1 + arr2)          	  # 오류

arr1 = np.array([1, 2, 3, 4])  	# (4,)
print(arr1 + 1)          		# arr1 + [1, 1, 1, 1]
								# [2 3 4 5]
```

아무런 차원이 없는 숫자를 스칼라라고 한다.

스칼라 계산을 하게 되면 broadcasting이 되어 차원을 맞춰주게 된다.

```python
arr1 = np.array([[1, 2, 3],[4, 5, 6]])  # (2, 3)
arr2 = np.array([4, 5, 6])              # broadcasting ([4, 5, 6],[4, 5, 6])
print(arr1 + arr2)      				
```

위의 경우,  arr2가 arr1의 차원에 맞춰 broadcasting이 일어날 수 있다.

#### B. matrix 곱연산

행렬곱 연산의 조건은 앞의 2차원 matrix의 열갯수와 뒤의 2차원 matrix의 행갯수가 같아야 한다.

행렬곱을 사용할 수 있는 함수가 존재한다.

```python
arr1 = np.array([[1, 2, 3], [4, 5, 6]])     # (2, 3)
arr2 = np.array([[4, 5], [6, 7], [8, 9]])   # (3, 2)
# 행렬 곱 연산의 결과는 (2, 2)
print(np.matmul(arr1, arr2))
```

#### C. matrix transpose (전치행렬)

행렬의 행과 열을 바꿔주는 속성

```python
arr = np.array([1, 2, 3], [4, 5, 6])  # (2, 3)
print(arr)

print(arr.T)
```

---

### 07. ndarray의 반복문 ✨

보통 for문을 사용하여 반복문을 사용한다.

ndarray의 경우에는 while문과 iterator를 이용해서 반복처리하는 방식을 선호한다.

iterator에서 객체를 얻어와서 사용할 수 있으며, 객체로부터 index를 추출할 수 있다.

```python
arr = np.array([1, 2, 3, 4, 5]) 	#(5,)
my_iter = np.nditer(arr, flags=['c_index'])

# from tmp in arr:
#     print(tmp)

while not my_iter.finished:
    idx = my_iter.index
    print(arr[idx])
    my_iter.iternext()
```

flags 속성은 `c_index`로 c언어에서쓰는 index 방식이라고 지정해준다.
👀 c언어와 python의 숫자 index 방식이 같다.

my_iter는 각 객체를 가리키고 있으며, 진행하다가 끝까지 도달할 때, `finished` 상태가 된다.

my_iter를 index에 위치시키고, while문 안의 코드를 수행 시킨 뒤, `iternext` 를 사용하여 my_iter를 다음 index로 옮겨주어야 한다. 

> ❓ 그냥 for문을 사용하면 안되나요
>
> 그냥 for문을 사용해도 되지 않냐 생각을 할 수 있는데, 2차원, 3차원으로 올라가게 되면 달라진다.
>
> 속도도 느릴 뿐더러 복잡하기 때문에, 그때는 iterator가 큰 빛을 발휘하게된다.
>
> 또한, for문은 shape을 알 경우에만 사용할 수 있기 때문에, shape을 알지 못하면 쓸 수 없다.

```python
arr = np.array([[1,2,3],[4,5,6]])  #(2.3)

# for tmp1 in range(arr.shape[0]):
#     for tmp2 in range(arr.shape[1]):
#         print(arr[tmp1][tmp2])

my_iter = np.nditer(arr, flags=['multi_index'])

while not my_iter.finished:
    idx = my_iter.multi_index
    print(idx)
    print(arr[idx])
    my_iter.iternext()
```

flags 속성으로 `multi_index`를 주어 다차원 **배열 형태의 index**를 지정해준다.

그 외에는 1차원일 때와 2차원일 때 똑같은 코드로 반복문을 수행할 수 있다.

---

### 08. 집계함수, axis ✨

#### A. 집계함수

```python
arr = np.arange(1, 7, 1).reshape(2,3)
print(arr)      # [[1 2 3]
                # [4 5 6]]
    
print(np.sum(arr))  # 21 => Numpy가 제공하는 함수를 이용
print(arr.sum())    # 21 => ndarray가 가지고 있는 메소드를 이용
print(arr.mean())   # 3.5
print(arr.max())    # 6
print(arr.min())    # 1
print(arr.argmax()) # 5 가장 큰값의 index를 반환해줌
print(arr.std())    # 표준편차 =>1.707825127659933
```

#### B. axis

numpy는 axis를 명시하지 않으면 전체를 대상으로 연산을 수행한다.

axis는 축을 나타내며, 고정되지 않고 내가 사용하는 차원에 따라서 바뀌게 된다.

> 1차원에서는 열 방향이 axis=0이다.
>
> 2차원에서는 행 방향이 axis=0이고, 열방향이 axis=1이다.
>
> 3차원은 면, 행, 열 순서대로 axis가 0, 1, 2가 된다.

```python
arr = np.arange(1, 7, 1).reshape(2,3)
print(arr)      # [[1 2 3]
                # [4 5 6]]
    
print(arr.sum(axis=0)) # [5 7 9]
print(arr.sum(axis=1)) # [ 6 15]
```

---

### 09. Pandas

ndarray의 정렬, 연결, 삭제, CSV 파일 로딩은 일반적으로 ndarray로 이작업을 하지 않는다.

pandas로 이것들을 처리한다~! 이제 pandas 에 대해서 알아보자

pandas의 내부 자료구조는 ndarray로 구성되어 기능을 추가한 series, dataframe가 있다.

---

### 10. 연습문제

문제 : Boolean indexing을 사용하여 matrix 속 10보다 큰 수가 몇개인지 찾기

아래는 정답

```python
import numpy as np

arr = np.arange(1, 17, 1).reshape(4, 4)
print(arr)

# 이 안에 10보다 큰 수는 몇개 있나요? 6개!!
# ?? => Boolean indexing을 이용

print((arr > 10).sum())
```







