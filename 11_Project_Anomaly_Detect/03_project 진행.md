**๐0425**

Data EDA, Data ์ดํดํ๊ธฐ



**๐0426**

AWS ํ๊ฒฝ ์ค์ 



**๐0427**

dacon ํด๋์์ฑ, ์ ๊ทํ ์ฝ๋ [link](https://dacon.io/competitions/official/235894/codeshare/4750?page=1&dtype=recent)

๊ณต๋ถ : <span style="color:red">TFRecord</span>๋ฅผ ์ฌ์ฉํ Data Argumentation

- riverdeer:TFRecord ํ์ผ ์ฝ๊ณ  ์ฐ๊ธฐ [link](https://velog.io/@riverdeer/TFRecord-%ED%8C%8C%EC%9D%BC-%EC%9D%BD%EA%B3%A0-%EC%93%B0%EA%B8%B0)
- glob : [link](https://wikidocs.net/83)

๊ณต๋ถ : <span style="color:red">f1-score</span>๋ก accuracy์ธก์ 



1. 88๊ฐ label๋ก ๋ถ๋ฅ
   - ๊ฐ๋ฐ์ดํฐ ์ฆ์(10๊ฐ์ฉ) ํ TFRecord๋ก ์ ์ฅ
   - 88๊ฐ label ๋ถ๋ฅ ๋ชจ๋ธ
2. 15๊ฐ label๋ก ๋ถ๋ฅ ํ ๊ฐ state๋ก ๋ถ๋ฅ



**๐0428**

<span style="color:red">AWS GPU ์ค์ </span>

[link1](https://rdmkyg.blogspot.com/2021/05/ubuntu-cuda-python.html), [link2](https://hengbokhan.tistory.com/75)

- gpu ์ค์น (์ฝ์)
  $ conda install tensorflow-gpu

  gpu ํ์ธ (์ฝ์)
  $ nvcc -V
  $ nvidia-smi

- jupyter ์๋ก์์
  jupyter์์ gpu ์ค์ ๋์๋์ง ํ์ธํ๋ ์ฝ๋

  ```python
  #----------------------------------
  import tensorflow as tf
  from tensorflow.python.client import device_lib
  device_lib.list_local_devices()
  #-----------------------------------
  tf.test.is_gpu_available()
  ```



<span style="color:red">multinomial ์ด๋ฏธ์ง ํ์ต</span>

[link1](https://keraskorea.github.io/posts/2018-10-24-little_data_powerful_model/) : ์ ๊ทํ, Augmentation, CNN, transfer learning, fine tuning ๋ฑ ํ์ตํ ๋ด์ฉ ์ ์ค๋ช๋์ด์์

[link2:Data-Science](https://velog.io/@robert-lee/Tensorflow-Keras-Multi-Class-Classification-%EC%9D%84-%EA%B5%AC%ED%98%84%ED%95%B4%EB%B3%B4%EC%9E%90) : multinomial (3)๊ฐ ๋ถ๋ฅ ์ฝ๋

[link3:๋ชจ๋ธ๋๊ฐํฉ์น๊ธฐ](https://www.facebook.com/groups/TensorFlowKR/permalink/675251819482546/?comment_id=675256699482058&reply_comment_id=675269169480811)



**๐0502**

TFRecord



**๐0503**

TFRecord ์ด๋ ต๋ค ใ ใ  ํฌ๊ธฐ

[link1](https://limjun92.github.io/assets/TensorFlow%202.0%ED%8A%9C%ED%86%A0%EB%A6%AC%EC%96%BC/3.%20%EB%8D%B0%EC%9D%B4%ED%84%B0%20%EB%A1%9C%EB%93%9C%20%EB%B0%8F%20%EC%82%AC%EC%A0%84%20%EC%B2%98%EB%A6%AC/%5B%ED%8A%9C%ED%86%A0%EB%A6%AC%EC%96%BC8%5D%20TFRecord%EC%99%80%20tf.Example/) : TFRecord, tf.Example ํํ ๋ฆฌ์ผ8

[link2](https://dacon.io/codeshare/1731) : Dacon TFRecord ํํ ๋ฆฌ์ผ 

[link3](https://velog.io/@springkim/tfrecord-%EC%95%95%EC%B6%95-%EC%98%B5%EC%85%98-%EA%B4%80%EB%A0%A8) : TFRecord ์์ถ์ต์

[link4](https://engineer-mole.tistory.com/206) : multiple ์์  TFRecord

> Error : module 'tensorflow' has no attribute 'python_io' => ์ง๊ธ์ ์ฌ์ฉํ์ง ์๋๊ฒ
>
> Error : corrupted record at 0



<span style="color:red">๋ฐ์ดํฐ ์ฆ์</span>



F1-Score

[link](https://blog.naver.com/PostView.nhn?blogId=wideeyed&logNo=221531940245) : ์ ๋ฆฌ์๋ฃ



**๐0504**

EfficientNet์ผ๋ก ํ์ต

**Error** : ResourceExhaustedError

GPU๋ฉ๋ชจ๋ฆฌ ์ค๋ฅ

**Error** : InvalidArgumentError

[link1](https://www.kaggle.com/questions-and-answers/170273) : kaggle, ๊ฐ์ issue

**Weight ์ค์ **

[link](https://ryanclaire.blogspot.com/2020/08/keras-weights.html00) : weight ๊ฐ์ ธ์ค๊ธฐ, ์ค์ ํ๊ธฐ, ์ ์ฅํ๊ธฐ ๋ฐฉ๋ฒ

**Git ์ ๋ฆฌ** [link](https://github.com/zalandoresearch/fashion-mnist) : MNIST Git ์ ๋ฆฌ์๋์ด์์ ๋ฐ๋ผ์ Git ์์ฑํด๋ณด๊ธฐ

[cat-dog ์ ๋ฆฌ git](https://github.com/KerasKorea/KEKOxTutorial/blob/master/27_little_data_powerful_model.md)

[model ๋ง๋ค๊ธฐ ์ ๋ฆฌ, ์ค๋ช](https://tykimos.tistory.com/13)



**๐0505**

**Error** : InvalidArgumentError

[link](https://luvbb.tistory.com/5) : one-hot encoding ์ถ๊ฐํด์ ํด๊ฒฐ (์ด๋ฏธ์ง๊ฐ์๋)

์ฐธ๊ณ  ์ฝ๋ 

[link1](https://wikidocs.net/73910) : ๊ฐ์๋ฐ์๋ณด multinomial 

[link2](https://velog.io/@robert-lee/Tensorflow-Keras-Multi-Class-Classification-%EC%9D%84-%EA%B5%AC%ED%98%84%ED%95%B4%EB%B3%B4%EC%9E%90) : ๊ฐ๊ณ ์์ดํ๋ค multinomial : one-hot



**๐0507**

[link](https://www.kaggle.com/code/archisha26/imagedatagenerator-efficientnet-b0/notebook) : ImageDataGenerator + EfficientNet-B0 kaggle ์์ 

> EfficientNetB4๋ ์ด๋ป๊ฒ ํด์ผ ๋๊ฒฐ์ ํ์ ์๋์ง ๋ชจ๋ฅด๊ฒ ์
>
> ๋๋ ฅํ๊ณ  ํ๋ฒ ๋๋ฆฌ๊ณ  ๋๊ฒฐํ๊ณ  ๋ค์ํ๋ฒ ๋๋ฆฌ๋ ค๊ณ  ํจ

[link](https://www.tensorflow.org/tutorials/keras/save_and_load?hl=ko) : checkpoint ๋ถ๋ฌ์ค๊ธฐ

[link](https://www.cognex.com/ko-kr/blogs/deep-learning/research/anomaly-detection-overview-1-introduction-anomaly-detection) : ์ด์์นํ์ ๋ฐฉ๋ฒ๋ก 

**Error** : ('Keyword argument not understood:', 'keepdims')

> [link](https://discuss.streamlit.io/t/unable-to-load-my-saved-model-using-tensorflow-keras/13026/11) : tensorflow ๋ฒ์  ๋ง์ถฐ์ฃผ์ด์ผ ํ ๊ฒ๊ฐ์

**Error** : 

WARNING:tensorflow:Model was constructed with shape (None, 256, 256, 3) for input KerasTensor(type_spec=TensorSpec(shape=(None, 256, 256, 3), dtype=tf.float32, name='efficientnet-b4_input'), name='efficientnet-b4_input', description="created by layer 'efficientnet-b4_input'"), but it was called on an input with incompatible shape (None, 256, 256). 
WARNING:tensorflow:Model was constructed with shape (None, 256, 256, 3) for input KerasTensor(type_spec=TensorSpec(shape=(None, 256, 256, 3), dtype=tf.float32, name='input_1'), name='input_1', description="created by layer 'input_1'"), but it was called on an input with incompatible shape (None, 256, 256).



**๐0509**

predict ์ ์ด๋ฏธ์ง ์ค๋ฅ [link](https://stackoverflow.com/questions/40119743/convert-a-grayscale-image-to-a-3-channel-image) ํ๋ฐฑ์ด๋ฏธ์ง์ ๊ฒฝ์ฐ ์ฐจ์์๊ฐ ๋ง์ง ์์์ ์ฐจ์์ฌ๋ ค์ค

**Error** : ์ ์ฅ๋ model, ckpt ๋ถ๋ฌ์ค๋๋ฐ ์ค๋ฅ : ใ ใ 

์ด๋ฏธ์ง ํฌ๊ธฐ ํค์์ ๋ชจ๋ธ๋๋ ค๋ณด๊ธฐ (์๋ ์ค์ ๊ฐ ์ฐธ๊ณ )

```python
## image generator ๊ณ ์ 
datagen = ImageDataGenerator(
    rotation_range=80,
    width_shift_range=0.1,
    height_shift_range=0.1,
    zoom_range=0.1,
    horizontal_flip=True,
    vertical_flip=True,
    shear_range = 10,
    fill_mode='constant')
```



**๐0510**

[link1](https://newindow.tistory.com/254) [link2](https://ang-love-chang.tistory.com/120) : ๋ฐ์ดํฐ์์ด ์ถฉ๋ถํ์ง ์์ Fine-Tuning ์์ด ์งํ

[link1-kaggle](https://keras.io/examples/vision/image_classification_efficientnet_fine_tuning/) [link2](https://keep-steady.tistory.com/35) : B4, ์ด๋ฏธ์ง ์ฌ์ด์ฆ 380

[link1](https://kmhana.tistory.com/26), [link2](https://hoya012.github.io/blog/EfficientNet-review/) : efficientNet ๋ผ๋ฌธ์์ฝ

[link](https://www.tensorflow.org/guide/keras/save_and_serialize?hl=en) : tensorflow, custom_objects ์ค์ ๋ฐฉ๋ฒ



-------------------- ๊ฐ ์ -------------------------



**๐0511**

[link](https://tempdev.tistory.com/32) : python cv ์ด๋ฏธ์ง ์ฑ๋ ๋ณ๊ฒฝ

[link](https://deep-learning-study.tistory.com/185) : cv image ๋ณด๊ฐ๋ฒ : INTER_AREA

[link](https://wikidocs.net/57165) : **PyTorch ๋ฅ๋ฌ๋์๋ฌธ** 





**๐0512**

[link](https://pytorch.org/vision/stable/auto_examples/plot_transforms.html#sphx-glr-auto-examples-plot-transforms-py%20%EC%B6%9C%EC%B2%98:%20https://nomalcy.tistory.com/191%20[NOMALCY]) pytorch transform ์ข๋ฅ

[link1](https://twinw.tistory.com/247) [โlink2](https://dbstndi6316.tistory.com/297) : optimizer ์ค๋ช

[link](https://www.programcreek.com/python/example/92673/torch.optim.Adadelta) : optimizer Example

[link](https://d2l.ai/chapter_optimization/adadelta.html) : Adadelta์๋ ํ์ต๋ฅ  ๋งค๊ฐ๋ณ์๊ฐ ์์ต๋๋ค. ๋์  ๋งค๊ฐ๋ณ์ ์์ฒด์ ๋ณํ์จ์ ์ฌ์ฉํ์ฌ ํ์ต๋ฅ ์ ์กฐ์ ํฉ๋๋ค.

[link](https://blog.naver.com/PostView.naver?blogId=sjy5448&logNo=222427780700&parentCategoryNo=153&categoryNo=&viewDate=&isShowPopularPosts=true&from=search) : K-Fold, **Stratified K-Fold**



**optimizer ๋ค๋ฅด๊ฒ ํด์ efficient_b4 ๋๋ ค๋ณด๊ธฐ**

- Adam(ํํธ), RAdam(์ฌ์ฑ), adadelta(์ง์ฐ)(weight_decay o,x)



b4+adadelta ๊ฐ ์ด๋๊น์ง ์ ์ผ ์๋์ด



**metal_nut์ class idx(7) ๋ฅผ ์ฌ์ฉํด flip ๋ฐฉ์ง**



* ์ค๋ฒํผํ์ด ๋๋ฌด๋์๊ฒฝ์ฐ weight_decay ์ฌ๋ฆฌ๊ธฐ
