jupyter notebook --ip=0.0.0.0 --no-browser --port=8912

http://3.114.181.173:8912/ 로 접속



복사 : cp -r cat_dog kaggle_cat_dog

삭제 : rm -r kaggle_cat_dog 



(AWS tqdm 쓸수있게하는거 설치)

conda install tqdm

conda install -c conda-forge ipywidgets

jupyter nbextension enable --py widgetsnbextension --sys-prefix

=> jupyter notebook 다시 실행