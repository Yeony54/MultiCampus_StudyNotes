GitHub

## GitHub 기본 예시



---







**브랜치 생성**

```bash
$ git checkout -b fix-mnist
```

작업내용을 대표하는 키워드로 Branch명을 생성하는것을 추천

제일 처음 생성할때 `-b` 키워드를 추가하면 생성이 된다.



**브랜치 이동하기**

```bash
$ git checkout master
```

`fix-mnist` 브랜치에서 `master`브랜치로 이동된다.



**브랜치 삭제하기**

```bash
$ git branch -D fix-mnist
```

`-D` 키워드로 삭제할 수 있다.



**브랜치 예시**

```bash
# fix-mnist 브랜치 생성
$ git checkout -b fix-mnist

# fix-mnist 브랜치에서 "hello.txt" 생성
$ touch "hello.txt"

# "hello.txt"의 commit 만들기
$ git add hi.txt
$ git commit -m "add txt"

# master branch로 이동
$ git checkout master

# master branch에서 "hello.txt" 여부 확인 
$ ls

# fix-mnist로 이동해서 "hello.txt" 여부 확인
$ git checkout fix-mnist
$ ls

```





---



**diff 예시**

```bash
# 편집기로 mnist/main.py 파일 수정
$ nano mnist/main.py

# 소스파일 수정한 내용 확인하기
$ git diff
```







 





