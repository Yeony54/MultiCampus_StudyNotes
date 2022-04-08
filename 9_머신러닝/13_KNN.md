

Machine learning

# Machine learning : KNN



KNN (K-Nearest Neighbors) 최근접이웃

예측하고싶은값 에서부터 데이터들 사이의 거리를 측정해서 가장가까운 값을 찾는다.

KNN은 2개의 hyperparameter가 있다

- K : 몇개의 이웃을 찾을것인가
- 거리측정방식
  - 유클리디안
  - 맨하튼
  - 마할라노비스 (분산, 공분산)

K=1 일때 어느정도 성능을 보장한다. 대부분 자연데이터는 주변 데이터와 유사하기 때문이다.

반드시 정규화를 진행하고 해야한다.

모든 데이터에 대해 거리를 계산하기 때문에 시간이 오래 걸린다는 단점이 있다.

### 예제

#### KNN 구현

```python
# 간단하게 KNN 구현에 대해서 알아보아요
# BMI 예제(multinomial classification)를 대상으로 KNN의 결과와
# Logistic Regression의 결과를 비교해보아요

import numpy as np
import pandas as pd
from sklearn.neighbors import KNeighborsClassifier
from sklearn.linear_model import LogisticRegression
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import MinMaxScaler

# Raw Data Loading
df = pd.read_csv('./data/bmi.csv', skiprows=3)
# display(df.head())

# Data Split
train_x_data, test_x_data, train_t_data, test_t_data =\
train_test_split(df[['height', 'weight']],
                 df['label'],
                 test_size=0.3,
                 random_state=1,
                 stratify=df['label'])

# 결측치, 이상치 없어요
# 정규화 진행해요
scaler = MinMaxScaler()
scaler.fit(train_x_data)
norm_train_x_data = scaler.transform(train_x_data)
norm_test_x_data = scaler.transform(test_x_data)

# LogisticRegression 구현
model = LogisticRegression()
model.fit(norm_train_x_data, train_t_data)
acc = model.score(norm_test_x_data, test_t_data)
print(f'LogisticRegression의 Accuracy : {acc}') # 0.9851666666666666

# KNN으로 구현
knn_classifier = KNeighborsClassifier(n_neighbors=3)
knn_classifier.fit(norm_train_x_data, train_t_data)
acc = knn_classifier.score(norm_test_x_data, test_t_data)
print(f'KNN의 Accuracy : {acc}') # 0.9985
```

#### Ozone 

```python
%reset
# Ozone량 예측 Linear Regression 구현(Tensorflow 2.x)
# 데이터 전처리 포함해요
import numpy as np
import pandas as pd
from scipy import stats
from sklearn.neighbors import KNeighborsRegressor
from sklearn.preprocessing import MinMaxScaler
import warnings

warnings.filterwarnings(action='ignore')
```

```python
# Raw Data Loading
df = pd.read_csv('./data/ozone.csv')
# display(df)
x_data = df[['Solar.R', 'Wind', 'Temp']]
t_data = df['Ozone']
```

```python
# 1. 먼저 독립변수에 대한 Missing Value를 찾아서 median으로 imputation

for col in x_data.columns:
    col_median = np.nanmedian(x_data[col])
    x_data[col].loc[x_data[col].isnull()] = col_median
    
# x_data.isnull().sum()

# 2. 독립변수에 대한 이상치를 검출한 후 이상치를 제외한 나머지값들의 mean으로 이상치를 대체

zscore_threshold = 2.0

for col in x_data.columns:
    outlier = x_data[col][np.abs(stats.zscore(x_data[col])) > zscore_threshold]
    col_mean = np.mean(x_data.loc[~x_data[col].isin(outlier), col])
    x_data.loc[x_data[col].isin(outlier), col] = col_mean

# 3. 종속변수에 대한 이상치를 검출한 후 이상치를 제외한 나머지값들의 mean으로 이상치를 대체

outlier = t_data[np.abs(stats.zscore(t_data)) > zscore_threshold]
col_mean = np.mean(~t_data.isin(outlier))
t_data[t_data.isin(outlier)] = col_mean

# 4. 정규화 진행
scaler_x = MinMaxScaler()
scaler_t = MinMaxScaler()

scaler_x.fit(x_data)
scaler_t.fit(t_data.values.reshape(-1,1)) # scaler는 2차원으로 사용해야해요

norm_x_data = scaler_x.transform(x_data.values)
norm_t_data = scaler_t.transform(t_data.values.reshape(-1,1)).ravel()

# 5. 종속변수의 Missing Value는 KNN을 이용해서 예측값을 사용합니다
# 종속변수가 nan이 아닌 독립변수들과 종속변수들을 추출(KNN을 학습하기 위해)
norm_train_x_data = norm_x_data[~np.isnan(norm_t_data)]
norm_train_t_data = norm_t_data[~np.isnan(norm_t_data)]

# 모델 생성
knn_regressor = KNeighborsRegressor(n_neighbors=2)
knn_regressor.fit(norm_train_x_data, norm_train_t_data)

# 종속변수가 Missing Value인 독립변수들을 입력으로 넣어서 값을 예측
knn_predict = knn_regressor.predict(norm_x_data[np.isnan(norm_t_data)])
norm_t_data[np.isnan(norm_t_data)] = knn_predict
```

```python
# 최종적인 우리 데이터는
# norm_x_data
# norm_t_data

# 이제 데이터가 준비되었으니.. sklearn 구현과 tensorflow 2.x 으로 구현할거에요

from sklearn.linear_model import LinearRegression
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Flatten, Dense
from tensorflow.keras.optimizers import SGD

test_data = np.array([[330, 15, 80]])

# sklearn 구현
model = LinearRegression()
model.fit(norm_x_data, norm_t_data)
result = model.predict(scaler_x.transform(test_data))

print(f'sklearn 예측값 : {scaler_t.inverse_transform(result.reshape(-1,1))}')

# Tensorflow 2.x 구현
keras_model = Sequential()

keras_model.add(Flatten(input_shape=(3,))) # input layer
keras_model.add(Dense(units=1,
                      activation='linear')) # output layer

keras_model.compile(optimizer=SGD(learning_rate=1e-2),
                    loss='mse')

keras_model.fit(norm_x_data,
                norm_t_data,
                epochs=5000,
                verbose=0)

result = keras_model.predict(scaler_x.transform(test_data))

print(f'tensorflow 예측값 : {scaler_t.inverse_transform(result.reshape(-1,1))}')
```

#### Titanic

```python
%reset
# Logistic Regression
# binary classification을 sklearn과 tensorflow 2.x로 구현해보아요
# 사용할 데이터는 titanic 데이터(Kaggle)

import numpy as np
import pandas as pd
import tensorflow as tf
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Flatten, Dense
from tensorflow.keras.optimizers import SGD
from sklearn.preprocessing import MinMaxScaler
from sklearn.model_selection import train_test_split

from sklearn.linear_model import LogisticRegression

import warnings

warnings.filterwarnings(action='ignore')

# 결측치 처리는 해야해요, 
# 단, 실제 데이터이기 때문에 이상치가 계산으로 검출된다 하더라도 해당 값을 그냥 사용할거에요
```

```python
# Raw Data Loading
df = pd.read_csv('./data/titanic/train.csv')

# 필요없는 column(feature)삭제처리
df = df.drop(['PassengerId','Name','Ticket','Fare','Cabin'], 
             axis=1,
             inplace=False)

# 컬럼을 보고 하나로 합칠 수 있는 컬럼은 하나로 합쳐줘요
df['Famlily'] = df['SibSp']+df['Parch']
df = df.drop(['SibSp', 'Parch'], axis=1, inplace=False)
# display(df.head())

# 결측치 처리
# df.isnull().sum()

# 'Embarked' feature는 결측치가 2개예요
df['Embarked'] = df['Embarked'].fillna('Q')

# 'Age' column의 결측치는 평균값으로 대체
df['Age'] = df['Age'].fillna(df['Age'].mean())

#####################################################33

gender_string = {'male':0, 'female':1 }
df['Sex'] = df['Sex'].map(gender_string)

embarked_string = {'S':0, 'C':1, 'Q':2 }
df['Embarked'] = df['Embarked'].map(embarked_string)

def age_category(age):
    if((age>=0)&(age<25)):
        return 0
    elif((age>=25)&(age<50)):
        return 1
    else: 
        return 2

df['Age'] = df['Age'].map(age_category)

df.head()

df.isnull().sum()
```

```python
# Data Split
train_x_data, test_x_data, train_t_data, test_t_data = \
train_test_split(df.drop('Survived', axis=1, inplace=False),
                 df['Survived'],
                 test_size=0.3,
                 random_state=1,
                 stratify=df['Survived'])
# Normalization
scaler = MinMaxScaler()
scaler.fit(train_x_data)
norm_train_x_data = scaler.transform(train_x_data)
norm_test_x_data = scaler.transform(test_x_data)
```

```python
# sklearn 구현

model = LogisticRegression()
model.fit(norm_train_x_data, train_t_data)
sklearn_result = model.score(norm_test_x_data, test_t_data)
print(f'sklearn 정확도 {sklearn_result}')
```

```python
# tensorflow 구현

keras_model = Sequential()
keras_model.add(Flatten(input_shape=(5,)))
keras_model.add(Dense(units=1,
                      activation='sigmoid'))
keras_model.compile(optimizer=SGD(learning_rate=1e-2),
                    loss='binary_crossentropy',
                    metrics=['accuracy'])
keras_model.fit(norm_train_x_data,
                train_t_data,
                epochs=1000,
                verbose=0)
keras_result = keras_model.evaluate(norm_test_x_data, test_t_data)
print(f'TF.x 정확도 : {keras_result}')
```

