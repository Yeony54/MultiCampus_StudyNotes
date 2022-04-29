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

