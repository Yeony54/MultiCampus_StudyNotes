**👉0425**

Data EDA, Data 이해하기



**👉0426**

AWS 환경 설정



**👉0427**

dacon 폴더생성, 정규화 코드 [link](https://dacon.io/competitions/official/235894/codeshare/4750?page=1&dtype=recent)

공부 : <span style="color:red">TFRecord</span>를 사용한 Data Argumentation

- riverdeer:TFRecord 파일 읽고 쓰기 [link](https://velog.io/@riverdeer/TFRecord-%ED%8C%8C%EC%9D%BC-%EC%9D%BD%EA%B3%A0-%EC%93%B0%EA%B8%B0)
- glob : [link](https://wikidocs.net/83)

공부 : <span style="color:red">f1-score</span>로 accuracy측정



1. 88개 label로 분류
   - 각데이터 증식(10개씩) 후 TFRecord로 저장
   - 88개 label 분류 모델
2. 15개 label로 분류 후 각 state로 분류



**👉0428**

<span style="color:red">AWS GPU 설정</span>

[link1](https://rdmkyg.blogspot.com/2021/05/ubuntu-cuda-python.html), [link2](https://hengbokhan.tistory.com/75)

- gpu 설치 (콘솔)
  $ conda install tensorflow-gpu

  gpu 확인 (콘솔)
  $ nvcc -V
  $ nvidia-smi

- jupyter 새로시작
  jupyter에서 gpu 설정되었는지 확인하는 코드

  ```python
  #----------------------------------
  import tensorflow as tf
  from tensorflow.python.client import device_lib
  device_lib.list_local_devices()
  #-----------------------------------
  tf.test.is_gpu_available()
  ```



<span style="color:red">multinomial 이미지 학습</span>

[link1](https://keraskorea.github.io/posts/2018-10-24-little_data_powerful_model/) : 정규화, Augmentation, CNN, transfer learning, fine tuning 등 학습한 내용 잘 설명되어있음

[link2:Data-Science](https://velog.io/@robert-lee/Tensorflow-Keras-Multi-Class-Classification-%EC%9D%84-%EA%B5%AC%ED%98%84%ED%95%B4%EB%B3%B4%EC%9E%90) : multinomial (3)개 분류 코드

[link3:모델두개합치기](https://www.facebook.com/groups/TensorFlowKR/permalink/675251819482546/?comment_id=675256699482058&reply_comment_id=675269169480811)



**👉0502**

TFRecord



**👉0503**

TFRecord 어렵다 ㅠㅠ 포기

[link1](https://limjun92.github.io/assets/TensorFlow%202.0%ED%8A%9C%ED%86%A0%EB%A6%AC%EC%96%BC/3.%20%EB%8D%B0%EC%9D%B4%ED%84%B0%20%EB%A1%9C%EB%93%9C%20%EB%B0%8F%20%EC%82%AC%EC%A0%84%20%EC%B2%98%EB%A6%AC/%5B%ED%8A%9C%ED%86%A0%EB%A6%AC%EC%96%BC8%5D%20TFRecord%EC%99%80%20tf.Example/) : TFRecord, tf.Example 튜토리얼8

[link2](https://dacon.io/codeshare/1731) : Dacon TFRecord 튜토리얼 

[link3](https://velog.io/@springkim/tfrecord-%EC%95%95%EC%B6%95-%EC%98%B5%EC%85%98-%EA%B4%80%EB%A0%A8) : TFRecord 압축옵션

[link4](https://engineer-mole.tistory.com/206) : multiple 예제 TFRecord

> Error : module 'tensorflow' has no attribute 'python_io' => 지금은 사용하지 않는것
>
> Error : corrupted record at 0



<span style="color:red">데이터 증식</span>



F1-Score

[link](https://blog.naver.com/PostView.nhn?blogId=wideeyed&logNo=221531940245) : 정리자료



**👉0504**

EfficientNet으로 학습

**Error** : ResourceExhaustedError

GPU메모리 오류

**Error** : InvalidArgumentError

[link1](https://www.kaggle.com/questions-and-answers/170273) : kaggle, 같은 issue

**Weight 설정**

[link](https://ryanclaire.blogspot.com/2020/08/keras-weights.html00) : weight 가져오기, 설정하기, 저장하기 방법

**Git 정리** [link](https://github.com/zalandoresearch/fashion-mnist) : MNIST Git 정리잘되어있음 따라서 Git 작성해보기

[cat-dog 정리 git](https://github.com/KerasKorea/KEKOxTutorial/blob/master/27_little_data_powerful_model.md)

[model 만들기 정리, 설명](https://tykimos.tistory.com/13)



**👉0505**

**Error** : InvalidArgumentError

[link](https://luvbb.tistory.com/5) : one-hot encoding 추가해서 해결 (이미지가아님)

참고 코드 

[link1](https://wikidocs.net/73910) : 가위바위보 multinomial 

[link2](https://velog.io/@robert-lee/Tensorflow-Keras-Multi-Class-Classification-%EC%9D%84-%EA%B5%AC%ED%98%84%ED%95%B4%EB%B3%B4%EC%9E%90) : 개고양이판다 multinomial : one-hot



**👉0507**

[link](https://www.kaggle.com/code/archisha26/imagedatagenerator-efficientnet-b0/notebook) : ImageDataGenerator + EfficientNet-B0 kaggle 예제

> EfficientNetB4는 어떻게 해야 동결을 풀수 있는지 모르겠음
>
> 동력하고 한번 돌리고 동결풀고 다시한번 돌리려고 함

[link](https://www.tensorflow.org/tutorials/keras/save_and_load?hl=ko) : checkpoint 불러오기

[link](https://www.cognex.com/ko-kr/blogs/deep-learning/research/anomaly-detection-overview-1-introduction-anomaly-detection) : 이상치탐색 방법론

