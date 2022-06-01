

### 가상환경 준비

```shell
> conda info --envs
> conda create -n machine_TF2_20 python=3.8 openssl
> conda activate machine_TF_20

# 가상환경 삭제
> conda env remove --n 가상환경이름
```



### 소프트웨어 설치

```shell
> conda install numpy pandas matplotlib nb_conda tensorflow
> pip install sklearn
```



- jupyter notebook --generate-config => 환경설정 파일을 만든다.
- mkdir jupyter_home => jupyter_home 폴더를 만든다.
- cd .jupyter => jupyter 폴더로 이동
- vi jupyter_notebook_config.py  => vi를 열고
-  :/notebook_dir  => 찾기
-  앞에 '# ' 지우고 => 지우는 키는 'x'
- 뒤에 경로를 home/lab23/jupyter_home 으로 설정 => 값을 집어넣을 때 i를 눌러야함
-  다 끝나고 저장 => :w- 나가기 => :q





### jupyter notebook 접속

```shell
jupyter notebook --ip=0.0.0.0 --no-browser --port=8912
```

http://3.114.181.173:8912/ 로 접속



### 파일 복사, 삭제

복사 : cp -r cat_dog kaggle_cat_dog

삭제 : rm -r kaggle_cat_dog 



### (AWS tqdm 쓸수있게하는거 설치)

conda install tqdm

conda install -c conda-forge ipywidgets

jupyter nbextension enable --py widgetsnbextension --sys-prefix

=> jupyter notebook 다시 실행