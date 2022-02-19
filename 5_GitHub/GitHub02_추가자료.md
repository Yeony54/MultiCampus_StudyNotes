GitHub

## GitHub 명령어 추가 자료

- git diff



---



**git diff**

파일의 어떤 내용이 변경되었는지 차이점을 비교할 수 있다.

Working Directory와 Staging Area간의 비교도 가능하고 

commit간의 비교, branch간의 비교도 가능하다.

1. commit된 파일상태와 현재 수정중인 상태 비교

   `git diff`

2. commit된 파일 상태와 add된 파일 상태 비교

   `git diff --staged`

3. commit간의 상태 비교하기 - commit hash 이용

   `git diff [비교할 commit 해쉬 1] [비교할 commit 해쉬 2]` 

4. commit간의 상태 비교하기 - HEAD 이용

   ex. `git diff HEAD HEAD^`

   가장 최근 커밋과 그 전의 커밋을 비교한다.

5. branch간의 상태 비교하기 - HEAD 이용

   `git diff [비교할 branch1] [비교할 branch2]`



**git show**

해당 커밋들에 어떤 수정사항이 있었는지 커밋 정보를 확인하기 위해 사용되어진다.

1. `git show` 현재 브랜치의 가장 최근 커밋 정보를 확인

2. `git show [커밋해시값]` 특정 커밋 정보를 확인

3. `git show HEAD` HEAD 포인터가 가리키는 커밋 정보를 확인

4. `git show [커밋해시값 또는 HEAD^]`

   ^ 표시개수만큼의 이전 값을 표시

   `~숫자`로 숫자를 명시할 수 있다. `HEAD~1`은 HEAD 첫번째 값을 의미













**참고한 자료**

diff, show : [swhan9404.log](https://velog.io/@swhan9404/git-rebase-diff-show)

