깃 기본 브랜치 생성

git config --global user.name "(본인 이름)"
git config --global user.email "(본인 이메일)"

확인 명령어
git config --global user.name
git config --global user.email

기본 브랜치명 변경
git config --global init.defaultBranch main

깃 프로젝트 관리 시작
해당폴더->깃바쉬->
git init

폴더에 숨김모드로 .git 폴더 생성 확인
🛑 이 폴더를 지우면 Git 관리내역이 삭제됩니다. (현 파일들은 유지)

깃 상태확인
git status
추적하지 않는(untracked) 파일: Git의 관리에 들어간 적 없는 파일

소스트리 : gui로 되어있어 직관적이다. 특히 브랜치들을 볼때 , 명령어를 잘모를땐 쓰기 편하다.

Git의 관리에서 특정 파일/폴더를 배제해야 할 경우
  a. 포함할 필요가 없을 때
자동으로 생성 또는 다운로드되는 파일들 (빌드 결과물, 라이브러리)
  b. 포함하지 말아야 할 때
보안상 민감한 정보를 담은 파일
.gitignore 파일을 사용해서 배제할 요소들을 지정할 수 있습니다.

.gitignore 형식

![image](https://user-images.githubusercontent.com/69129562/207556796-6e5da2cd-447e-429c-a3a9-934b283b9eab.png)

파일 하나 담기
git add tigers.yaml
모든 파일 담기
git add .

타임캡슐 묻기(깃에 업로드 전에 1차 저장)
git commit
커밋 메시지까지 함께 작성하기
git commit -m "FIRST COMMIT"
지난 커밋 내역 확인
git log

add와 commit 한꺼번에
git commit -am "(메시지)"

Git에서 과거로 돌아가는 두 방식
reset : 원하는 시점으로 돌아간 뒤 이후 내역들을 지웁니다.
git reset --hard (돌아갈 커밋 해시)
reset 하기 전 시점으로 복원해보기
git reset --hard

revert : 되돌리기 원하는 시점의 커밋을 거꾸로 실행합니다.
git revert (되돌릴 커밋 해시)

🛑커밋해버리지 않고 revert하기
git revert --no-commit (되돌릴  커밋 해시)
 -원하는 다른 작업을 추가한 다음 함께 커밋
 -취소하려면 git reset --hard
 
 ![image](https://user-images.githubusercontent.com/69129562/207556684-a38d9936-dcd8-4d95-8179-586efe6c0c49.png)

 Branch: 분기된 가지 (다른 차원)
프로젝트를 하나 이상의 모습으로 관리해야 할 때

예) 실배포용, 테스트서버용, 새로운 시도용
여러 작업들이 각각 독립되어 진행될 때

예) 신기능 1, 신기능 2, 코드개선, 긴급수정...
각각의 차원에서 작업한 뒤 확정된 것을 메인 차원에 통합

add-coach란 이름의 브랜치 생성
git branch add-coach

브랜치 목록 확인
git branch

add-coach 브랜치로 이동
git switch add-coach

브랜치 생성과 동시에 이동하기
git switch -c new-teams

브랜치 삭제하기
git branch -d (삭제할 브랜치명)

지워질 브랜치에만 있는 내용의 커밋이 있을 경우
즉 다른 브랜치로 가져오지 않은 내용이 있는 브랜치를 지울 때는
-d 대신 -D(대문자)로 강제 삭제해야 합니다.
git branch -D (강제삭제할 브랜치명)

브랜치 이름 바꾸기
git branch -m (기존 브랜치명) (새 브랜치명)

여러 브랜치 내역을 보고싶을땐 소스트리를 이용하자.

git branch -m (기존 브랜치명) (새 브랜치명)

서로 다른 브랜치를 합치는 두 방식
merge : 두 브랜치를 한 커밋에 이어붙입니다.

브랜치 사용내역을 남길 필요가 있을 때 적합한 방식입니다.
다른 형태의 merge에 대해서도 이후 다루게 될 것입니다.
rebase : 브랜치를 다른 브랜치에 이어붙입니다.

한 줄로 깔끔히 정리된 내역을 유지하기 원할 때 적합합니다.
이미 팀원과 공유된 커밋들에 대해서는 사용하지 않는 것이 좋습니다.

add-coach 브랜치를 main 브랜치로 merge

1. merge로 합치기
main 브랜치로 이동
아래의 명령어로 병합
git merge add-coach
:wq로 자동입력된 커밋 메시지 저장하여 마무리

merge는 reset으로 되돌리기 가능
merge도 하나의 커밋
merge하기 전 해당 브랜치의 마지막 시점으로

병합된 브랜치는 삭제
삭제 전 소스트리에서 add-coach 위치 확인
git branch -d add-coach

2. rebase로 합치기
new-teams 브랜치를 main 브랜치로 rebase
new-teams 브랜치로 이동
🛑 merge때와는 반대!
아래의 명령어로 병합
git rebase main
소스트리에서 상태 확인
main 브랜치는 뒤쳐져 있는 상황
main 브랜치로 이동 후 아래 명령어로 new-teams의 시점으로 fast-forward
git merge new-teams
new-teams 브랜치 삭제

브랜치 간 충돌
파일의 같은 위치에 다른 내용이 입력된 상황
1. merge 충돌 해결하기
오류 메시지와 git status 확인
당장 충돌 해결이 어려울 경우 아래 명령어로 merge 중단
git merge --abort
해결 가능 시 충돌 부분을 수정한 뒤 git add ., git commit으로 병합 완료

2. rebase 충돌 해결하기
오류 메시지와 git status 확인
git rebase --abort
해결 가능 시
충돌 부분을 수정한 뒤 git add .
아래 명령어로 계속
git rebase --continue
충돌이 모두 해결될 때까지 반복


원격 저장소 사용하기 (깃헙)

1. 로컬에 원격 저장소 추가 후 푸시
git remote add origin (원격 저장소 주소) 
로컬의 Git 저장소에 원격 저장소로의 연결 추가
원격 저장소 이름에 흔히 origin 사용. 다른 것으로 수정 가능
git branch -M main
git push -u origin main 
로컬 저장소의 커밋 내역들 원격으로 push(업로드)

원격 목록 보기
git remote

원격 지우기 (로컬 프로젝트와의 연결만 없애는 것. GitHub의 레포지토리는 지워지지 않음)
git remote remove (origin 등 원격 이름)

Git clone: Git 관리내역 포함 다운로드
터미널이나 Git Bash에서 대상 폴더 이동 후
git clone (원격 저장소 주소)

4강. push와 pull
