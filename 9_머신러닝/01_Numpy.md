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

### 01. Data Handling : Numpy

대부분의 데이터는 가공되지 않은 raw 데이터이다.

데이터는 잘 정리된 데이터든, 정리되지 않은 데이터든 결과가 나온다.

얻은 데이터를 잘 가공해서 유의미한 결과를 얻어야 한다.

pandas, numpy를 사용하여 데이터를 가공한다.

##### A. Numpy

Numpy는 수치계산을 용이하게 하기 위한 python module이다.

대용량의 다차원 배열과 matrix(행렬)연산을 쉽게 할 수 있다.

Numerical Python => Numpy

##### B. ndarray

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

### 02. Numpy

**1차원 배열**

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

*--정수냐, 실수냐에 따라서도 분석 결과값이 달라지기 때문에, 주의가 필요하다.--*

**다차원 배열**

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

**dtype 지정하여 ndarray 생성**

```python
arr = np.array([[1, 2, 3], [4, 5, 6]])
print(arr.dtype)        # int32

arr = np.array([[1, 2, 3], [4, 5, 6]],
              dtype=np.float64)
print(arr.dtype)       	# float64
```

dtype은 자동으로 생성되지만, 사용자가 데이터타입을 지정해서 생성할 수 있다.

**ndarray의 차원 관련 속성**

```python
my_list = [1, 2, 3, 4]
arr = np.array(my_list)
print(arr)        # [1 2 3 4]
print(arr.dtype)  # ndarray의 data type => int32
print(arr.ndim)   # ndim은 차원수를 숫자로 알려준다. => 1
print(arr.shape)  # shape은 차원과 요소수를 tuple로 알려준다.
                  # 1차원이니까 tupe안에 요소가 1개, 그리고 그 값이 요소의 개수
                  # (4, ) : 요소가 하나인 튜플
```



