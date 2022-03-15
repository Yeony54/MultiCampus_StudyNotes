GitHub

## GitHub 기본

- Git, GitHub?
- Git 기본용어
- GitHub 기본 명령어
- GitHub 프로젝트 협업 참여 시나리오



---



### Git, GitHub?



**Git이란?**

Git은 프로젝트의 변경을 관리하는 버전 분산 관리 시스템이다.



**GitHub이란?**

GitHub은 Git을 다른사람들이 볼 수 있도록 정보교환이 이루어지는 일종의 서버라고 불릴수 있다.



**Git, GitHub을 쓰는 이유**

IT 업계에서 하나의 프로그램을 만들기 위해 여러사람이 투입되어 작업을 하게된다.

협업으로 작업하며 프로젝트를 만들 때, 프로젝트가 겹쳐쓰지 않게 관리한다.

또한, 작업의 기록을 남길 수 있어, 수정 및 보완 등의 이력을 추적할 수 있다.

이는 작업하는 사람들과의 협업을 용이하게 한다.



---



### Git 기본용어



**커맨드라인(Command Line)** 깃 명령어를 사용할 때 사용하는 컴퓨터 프로그램. 맥에선 터미널이라고 한다. 

**저장소(Repository)** 프로젝트의 디렉토리나 저장공간. 로컬 폴더가 될 수도 있고, 깃허브나 다른 온라인 호스트의 저장공간이 될 수도 있다.

**커밋(Commit)** 커밋을 하게되면, 그시점의 나의 저장소를 저장하여 체크포인트를 가질 수 있다.

**브랜치(Branch)** 여러 사람이 프로젝트에서 작업할 때, 원본을 유지하면서 다른 공간에서 나의 작업을 할 수 있는 기능이다. 작업을 끝낸 후 브랜치를 다시 **Merge** 하여 통합시켜야한다.



---



### Git 설정



```bash
# GitHub ID/PW 캐싱데이터 삭제 (삭제 시 문제없음)
# 다른(사람) GitHub 계정과의 충돌 방지
$ git config --global --unset credential.helper
$ git config --system --unset credential.helper

# GitHub 계정 이메일 주소 및 본인 영문이름
# 소스코드 파일 수정내역(commit) 저자(author) 정보
$ git config --global user.name "Gim Chulsu"
$ git config --global user.email gcs1234@gmail.com
```



```bash
# Git 편집기
# 원하는 편집기 설정 가능 (vim, emacs, nano, notepad 등)
$ git config --global core.editor nano

# nano 편집기 사용 시 설치 필요
$ sudo apt install -y nano  ( commit 메세지 에디터 )
```



```bash
# 잘 설치되었는지 확인
$ git config -list
```





---



### GitHub 명령어



**pwd** (print working directory) : 현재 경로 확인

**ls** (list segments) : 폴더 내용 확인

**touch** hello.c : hello.c라는 빈파일 생성

**mv** hello.c hello1.c : 파일명 변경 or 경로 이동

**rm** hello1.c : 파일 제거

**cd** (change directory) : 디렉토리 위치 변경

- cd .. : 상위 폴더로 위치 변경
- cd workspace/ : workspace로 위치 변경

**clear** : 화면 정리

터미널창이 응답하지 않을 때 **Ctrl+C** 연타로 종료 가능하다.

다른 입력창 등은 **q** 입력으로 종료할 수 있다.



**git diff** : git에서 관리되는 것들 중 가장 최신의 변경 내용을 보여준다. 파일의 어떤 내용이 변경되었는지 차이점을 비교할 수 있다. 

```bash
# 편집기로 mnist/main.py 파일 수정
$ nano mnist/main.py

# 소스파일 수정한 내용 확인하기
$ git diff
```

**git show** : commit의 정보를 확인하는 명령어



**git init** 기본 폴더에서는 git 명령어를 사용할 수 없다. 폴더에서 `git init`를 실행시키면 `.git`파일이 생기고 그 이후 git 명령어를 입력할 수 있게 된다.

**git config** 'configure'의 줄인말로 처음에 깃을 설정할때 많이 사용한다.

**git help** 명령어를 잊어버렸을때 명령어를 열거해 준다. -h나 man의 형태로도 사용한다.

**git status** 저장소 상태를 체크하는 명령어이다. 저장소를 공유할 준비가 되어있는지, 커밋이 필요한 변경사항이 있는지, 현재 어떤 브랜ㄴ치에서 작업하고 있는지 등을 볼 수 있다.

**git add** 이 명령은 저장소에 새 파일을 추가하는 명령어가 아니다. 이 명령어를 통해 깃이 새 파일들을 관리하게 한다.

``` bash
$ git add {file name}
$ git add .     # all의 의미를 가짐
```

**git commit** 깃의 가장 중요한 명령어, 변경사항을 저장하고 체크포인트를 만든다.

```bash
$ git commit -m "commit 문구"
$ git commit -sm "commit 문구"	 # 서명이 commit message안에 포함된다.
$ git commit --amend			  # 최신 commit 수정하기
```

**git branch** 협업하여 프로젝트를 만들 때 원본과 다른 공간에서 작업할 수 있는 기능

**git checkout** branch를 만들어 checkout 명령어를 통해 branch를 이동할 수 있다.

**git merge** branch등을 통해 각각 나누어져 있는 프로젝트 소스들을 하나로 병합하는 기능

**git push** 로컬에서 작업한 내용을 깃허브에 올릴 때 사용하는 명령어

**git pull** 로컬에서 GitHub의 작업을 시작할때 혹은 최신 내용을 업데이트 할때 GitHub에서 프로젝트의 내용을 다운로드 하는 명령어

**git remote** GitHub등 로컬이 아닌 원격 저장소에 저장을 할 때 사용하는 주소 관리 명령어

```bash
$ git remote add upstream [프로젝트 URL]
$ git remote -v				# 저장된 remote 보여줌
```

**git log** git의 history 조회

**git shortlog** `git log`는 Git의 history 내의 commit 내역을 모두 보여준다. shortlog는 commit 메세지만 추려서 보여준다.  

**git tag** 버전 확인



**git stash** 수정한 내용 잠시 저장(stash) 하기, stash pop으로 저장한 내용 복구

**git checkout** 파일복구 : local git 저장소에서 가져오다, 대출받다를 의미

> stash vs checkout
>
> checkout은 완전히 날려버린다.
>
> stash는 버리고 싶지 않으니 잠깐 임시저장하는느낌

**git reset** add 명령 취소, commit 취소 등

git reflog : 극한적인 복구 / 잘사용하지 않음



**git blame** 소스코드가 어떤 커밋으로 만들어졌는지 확인가능, history 분석

**nano [파일명]** 소스파일 수정 ( ctrl+o : 저장, ctrl+x : 나가기 ) 







---



#### git log 정리

git log : git의 history 조회

- `git log` 커밋 히스토리의 내용 보기
- `git log --oneline` 커밋 히스토리 한줄 씩 보기
- `git log --oneline --no-merges` merge commit 없이 검색
- `git log -p` 커밋메시지와 함께 diff 수정내용까지 보기
- `git log --oneline -- 파일명/`특정 파일에 집중해서 보기
- `git log --oneline --after=2020-01-01 --before=2020-06-30` 기간
- `git log --reverse -- minist/main.py` 거꾸로 보기 => 옛날 소스파일 수정내역 보기



---



### GitHub 프로젝트 협업 참여 시나리오

GitHub에서 공동 프로젝트**(upstream)**를 작업 할때, 공동 프로젝트 폴더에서 작업하지 않는다.

공동 프로젝트를 개인 계정**(origin)**으로 Fork하여 복사하고, 이를 관리하기 위해 clone을 사용하여 로컬(혹은 컨테이너)에 다운로드한다.

작업을 마친 후 push를 통해 작업을 Fork한개인 계정 프로젝트에 업로드한다.

공동 프로젝트 폴더에 Pull-Request를 통해 내가 한 작업을 제출한다.

1. Fork 프로젝트 복사
2. clone 소스코드 다운로드
3. 프로젝트 분석/경향파악
4. commit 코드 수정작업
5. push 작업 업로드 (fork 프로젝트 업로드)
6. Pull-Request 나의작업(commit) 제출



참여 시나리오에 따라 어떤 명령어를 어떻게 사용하는지 예시를 들어가며 설명한다.



---



#### 1. Fork 

<u>*웹 페이지에서 작업*</u>

깃허브 공동 프로젝트 작업은 원본에서 하는것이 아닌, 내 개인계정에 복사하여 작업하게 된다.

이때 프로젝트 원본을 **upstream**, 개인 저장소를 **origin**이라고 명칭하겠다.

GitHub 원본 프로젝트 페이지를 보면 Fork를 찾을 수 있다.

`Frok > 개인계정` 을 순서대로 클릭하면 프로젝트 작업 개인계정에 복사할 수 있다.



#### 2. clone

<u>*여기부터 터미널 (Git에서 작업)*</u>

개인 계정 GitHub에 Fork를 통해 원본이 저장되었다.

로컬(혹은 컨테이너)에 다운로드하여 이 프로젝트의 수정작업을 하게된다.



#### 3. 프로젝트 분석

공동 프로젝트를 작업할 때에는 다른사람들의 작업을 분석하고 경향을 파악해야한다.

commit을 show로 확인해보고, diff로 다른 commit들과의 차이점을 찾아보는 작업의 연속이다.

commit은 작업의 단위로 여겨질 만큼 중요한 것이다.

commit은 history로 저장되어져 과거의 기록을 보고 프로젝트를 분석하며, 수정한 내용이 미래에 검색되어질 수도 있기 때문에 comment 작성 시 정성을 들여야 한다.



분석할 때 많이 사용되는 명령어를 알아보자



**commit ID** : 소스파일 수정내역 고유한 ID (SHA1 해시값)

**Merge Commit** : 병합이 된 것을 알려주는 깡통 Commit, 실제 commit된 것은 없다.

- `git log --oneline --no-merges` merge commit 없이 검색





**오픈소스에서 가장 개발을 많이 한사람 검색**

- `git shortlog -s -n --no-merges --after=2019-01-01 -- mnist/ | nl`

`-s` 는 개수를 요약하고, `-n`은 rank를 매겨 정렬해준다.

`-s -n`대신 `-sn`으로 사용 가능하다.

`nl`은 line number를 명시하여 rank를 출력한다.

`-- [파일명]`을 사용하여 그 파일 내의 통계를 내볼 수 있다.

`--after=[연월일]`, `--before=[연월일]`을 사용하여 일자 제한을 줄 수 있다. 



**소스파일 수정내역 commit 개수 검색**

- `git log --oneline --no-merges --after=2019-01-01 -- mnist/ | wc -l`

`wc`

`-l`



**소스파일 수정내역 수정한 소스파일 개수 검색**

파일 변경이 일어날 때마다 diff가 있는것을 확인할 수 있다.

diff가 있는 문자를 필터링해서 라인개수를 확인하여 수정한 소스파일 개수를 검색한다.

- `git show 6c8e2ba | grep "diff --git"`
- `git show 6c8e2ba | grep "diff --git" | wc -l`







**<<기타>>**

**commit message의 첫단어** 

commit은 기록되는 것이기 때문에 마음대로 작성해서는 안된다. update라는 모호한 말은 No

- Fix : 잘못된것을 고친다
- Improve : 원래 잘 되던것을 개선한다 (10초->5초)
- Add : 없던기능/옵션을 추가할 때
          (함수추가, 클래스추가, 파일추가 리뷰 협업을 위해 Fix, Improve 등으로 표기권장)
- Support : 예) 윈도우외에 리눅스 환경 추가 / x86->ARM
- Refactor : 코드를 재배치, 깔끔하게 정리
- Implement : 구현하다(Add랑 너무 비슷함)
- Correct typo : 오탈자 수정





---



### 코드설명 & 예시



#### Banch

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



#### Rebase : 최신 소스로

오픈소스 Github 최신 소스수정내역(commit)으로 Base 업데이트

1. upstream 의 최신내용을 가져온다

   ```bash
   # upstream 저장소에서 최신 commit history 가져오기
   $ git fetch upstream master
   ```

   pull 은 fetch+merge 형태로 가져온내용을 강제머지 시킨다.

   fetch는 가져오기만 하고 현재 브랜치에 적용은 하지 않음

   upstream/master branch 자동 생성

2.  가져온 내용을 rebase

   ```bash
   # 최신 commit history 기준으로 베이스 갱신 (rebase)
   $ git rebase upstream/master
   ```

3. Fork 저장소 GitHub 수정하기

   ```bash
   # Fork한 저장소(GitHub)도 수정하기 (PR 자동 갱신)
   $ git push --force origin fix-mnist
   ```

   

**rebase 취소**

```bash
$ git rebase --abort
```





---



#### Rebase : 과거 Rewind, 커밋내용 수정

수정내역(commit) 과거시점으로 되감기(rewind)

rebase 기능을 사용해서 한다.

[rebase edit 예시 reference](https://github.com/appkr/blog/blob/master/_posts/2016-04-25-git-rebase.md)

[git rebase 옵션, 예시 reference](https://wormwlrm.github.io/2020/09/03/Git-rebase-with-interactive-option.html)

*협업하는 과정에서 리포지터리에 푸시된 커밋 히스토리를 로컬에서 리베이스하여 다시 푸시하는 일은 지양해야합니다. 왜냐하면 리베이스는 기존의 커밋을 재사용하는 것이 아니라, 내용이 같은 커밋을 새로 만들기 때문입니다.*

*이 때문에 다른 동료의 히스토리를 망칠 수 있고, 특히 `--force`옵션으로 푸시해버린다면 다른 동료의 작업본을 날릴 수 있으니 주의해야합니다.*

```bash
# 수정하고 싶은 부분의 pick을 edit으로 수정 후 편집기 저장, 나가기
$ git rebase -i --root

# 되감은 시점에서 log 확인
$ git log --oneline

# rebase 과정 종료 : 되감은 내용 풀기 (continue)
$ git rebase --continue
```



log에 쌓여있는것들 중 중간에 있는 commit을 바꾸고 싶을 때 사용한다.

base를 건드리려고 rewind를 하지 않는다.



- `-i` 또는 `-interactive` : 대화형으로 실행

- `--root` : 최초 커밋부터 리베이스

- `git rebase -i --root` 으로 대화창 실행 후, 수정하고 싶은 커밋앞의 `pick`을 `edit`혹은 `e`로 바꾸어 저장하면 된다.

  편집하지 않고 종료할 경우 아무런 변경사항 없이 리베이스가 종료된다.

  - `pick`또는 `p` : 해당커밋을 수정하지 않고 그냥 사용하겠다는 명령어

  - `reword`또는 `r` : 커밋 메세지를 수정하기 위한 명령어

  - `edit` 또는 `e` : 커밋 명령어 뿐만 아니라 작업 내용도 수정할 수 있게 하는 명령어

  - `squash`또는 `s`, `fixup`또는 `f` : 해당 커밋을 이전 커밋과 합치는 명령어

    `squash`는 각 커밋들의 메세지가 합쳐지고, `fixup`은 이전의 커밋 메세지만 남긴다.

  - `exec` 또는 `x` : 리베이스 도중에 실행할 쉘 커맨드를 입력할 수 있게 해주는 명령어

  - `break` 또는 `b` : 해당 라인에서 리베이스를 일시중지하는 명령어

    continue로 다시 재개할 수 있다 (잘안쓰임)

  - `drop` 또는 `d` : 해당 커밋을 명시적으로 삭제

  - `merge` 또는 `m` : 머지 커밋을 만들면서 머지하는 명령어



**Git Rebase 취소 : 과거로 rewind**

git reset --hard는 commit을 취소하고 파일을 풀어버리는 역할...?

- **git reflog [브랜치명]**

  잘못 리베이스한 로컬 컴퓨터에서 실행, 리베이스 로그를 보여줌

  그냥 로그를 보는거여서 막쳐봐도 된다.

- **git checkout testBranch**

  commit, push는 잘 생각하고 해야한다. 

  branch를 생성해서 테스트

- **git reset --hard [hash]**

  reflog를 보고, 돌아가고싶은 커밋명(hash)를 기입

  이전커밋이력을 모두 reset 한다.

- **git push -f origin [브랜치명]**

  리셋한 커밋이력을 리모트로 강제 푸시

  -f 명령은 강제푸시



---



#### Reset

reset 너무 어려웡

```bash
# commit 에 쓴 파일을 남기고 commit이 지워짐
# add 파일은 남아있는 상태
$ git reset --soft HEAD~1

# 이상태에서 reset 시 add 취소 (add된 파일을 안된상태로)
$ git reset
```

``` bash
# commit 삭제
$ git reset --hard HEAD~1
```





---



```bash
#강제로 clean
git clean -f 
# 이거도 하라는대로
git restore
```





---



#### Tag

특정 커밋 버전을 마킹한다.

```bash
# ?
$ git fetch --tags

# tag 확인
$ git tag

# 태그 생성
$ git tag v0.12 b2650116

# 태그 삭제
$ git tag -d 0.12
```

```bash
# v0.8 버전 (과거)로 현재 폴더 변경하기
$ git reset --hard v0.8

# 다시 원본 GitHub 프로젝트로 현재 폴더 변경하기
$ git reset --hard origin/master
```







---



### bash 문법

**연산자**

```bash
# 연달아서 코드 사용가능
$ touch hello_3.c && git add hello_3.c && git commit -m "test: add hello_3.c"
```

```bash
$ echo "hi" ; echo "hello" # 앞에거가 오류나도 뒤에거 연달아 실행
$ echo "hi" && echo "hello" # 앞에거 오류나면 에러나고 뒤에거 안함
```



**for문**

```bash
$ for i in {1..3}
do
touch hello_$i.c && git add hello_$i.c && git commit -m "test: add hello_$i.c"
done
```





---



**Unstashed 파일 정리하기**

reset

clear

restore .



---



**참고**

Git, GitHub : [hyefa.log](https://velog.io/@gpwls320/Git-%EC%9A%A9%EC%96%B4-%EB%AA%85%EB%A0%B9%EC%96%B4)

