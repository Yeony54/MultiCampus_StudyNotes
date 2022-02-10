GitHub

## GitHub 기본

- Git, GitHub?
- Git 기본용어
- GitHub 기본 명령어
- GitHub 프로젝트 협업 참여 시나리오



---



#### Git, GitHub?



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



#### Git 기본용어



**커맨드라인(Command Line)** 깃 명령어를 사용할 때 사용하는 컴퓨터 프로그램. 맥에선 터미널이라고 한다. 

**저장소(Repository)** 프로젝트의 디렉토리나 저장공간. 로컬 폴더가 될 수도 있고, 깃허브나 다른 온라인 호스트의 저장공간이 될 수도 있다.

**커밋(Commit)** 커밋을 하게되면, 그시점의 나의 저장소를 저장하여 체크포인트를 가질 수 있다.

**브랜치(Branch)** 여러 사람이 프로젝트에서 작업할 때, 원본을 유지하면서 다른 공간에서 나의 작업을 할 수 있는 기능이다. 작업을 끝낸 후 브랜치를 다시 **Merge** 하여 통합시켜야한다.



---



#### GitHub 명령어



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



**diff** : git에서 관리되는 것들 중 가장 최신의 변경 내용을 보여준다. 파일의 어떤 내용이 변경되었는지 차이점을 비교할 수 있다. 

**show** : commit의 정보를 확인하는 명령어



**git init** 기본 폴더에서는 git 명령어를 사용할 수 없다. 폴더에서 `git init`를 실행시키면 `.git`파일이 생기고 그 이후 git 명령어를 입력할 수 있게 된다.

**git config** 'configure'의 줄인말로 처음에 깃을 설정할때 많이 사용한다. 아래 명령어는 사용자 이름, 이메일을 입력하는 방법이다.

```bash
$ git config --global user.name "Gim Chulsu"
$ git config --global user.email gcs1234@gmail.com
```

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
```

**git branch** 협업하여 프로젝트를 만들 때 원본과 다른 공간에서 작업할 수 있는 기능

**git checkout** branch를 만들어 checkout 명령어를 통해 branch를 이동할 수 있다.

**git merge** branch등을 통해 각각 나누어져 있는 프로젝트 소스들을 하나로 병합하는 기능

**git push** 로컬에서 작업한 내용을 깃허브에 올릴 때 사용하는 명령어

**git pull** 로컬에서 GitHub의 작업을 시작할때 혹은 최신 내용을 업데이트 할때 GitHub에서 프로젝트의 내용을 다운로드 하는 명령어

**git remote** GitHub등 로컬이 아닌 원격 저장소에 저장을 할 때 사용하는 주소 관리 명령어

**git log** git의 history 조회

**git shortlog** `git log`는 Git의 history 내의 commit 내역을 모두 보여준다. shortlog는 commit 메세지만 추려서 보여준다.  



---



#### GitHub 프로젝트 협업 참여 시나리오

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



**오픈소스에서 가장 개발을 많이 한사람 검색**

- `git shortlog -s -n | nl`
- `git shortlog -s -n --no-merges | nl`
- `git shortlog -s -n --no-merges -- mnist/ | nl`
- `git shortlog -s -n --no-merges --after=2019-01-01 -- mnist/ | nl`

`-s` 는 개수를 요약하고, `-n`은 rank를 매겨 정렬해준다.

`-s -n`대신 `-sn`으로 사용 가능하다.

`nl`은 line number를 명시하여 rank를 출력한다.

`-- [파일명]`을 사용하여 그 파일 내의 통계를 내볼 수 있다.

`--after=[연월일]`, `--before=[연월일]`을 사용하여 일자 제한을 줄 수 있다. 



**소스파일 수정내역 commit 개수 검색**

- `git log --oneline | wc -l`
- `git log --oneline -- mnist/ | wc -l`
- `git log --oneline --no-merges --after=2019-01-01 -- mnist/ | wc -l`











****







**참고**

Git, GitHub : [hyefa.log](https://velog.io/@gpwls320/Git-%EC%9A%A9%EC%96%B4-%EB%AA%85%EB%A0%B9%EC%96%B4)

