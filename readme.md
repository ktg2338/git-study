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
# 이렇게 #를 사용해서 주석
# 모든 file.c
file.c
# 최상위 폴더의 file.c
/file.c
# 모든 .c 확장자 파일
*.c
# .c 확장자지만 무시하지 않을 파일
!not_ignore_this.c
# logs란 이름의 파일 또는 폴더와 그 내용들
logs
# logs란 이름의 폴더와 그 내용들
logs/
# logs 폴더 바로 안의 debug.log와 .c 파일들
logs/debug.log
logs/*.c
# logs 폴더 바로 안, 또는 그 안의 다른 폴더(들) 안의 debug.log
logs/**/debug.log

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
 
 Branch: 분기된 가지 (다른 차원)
프로젝트를 하나 이상의 모습으로 관리해야 할 때

예) 실배포용, 테스트서버용, 새로운 시도용
여러 작업들이 각각 독립되어 진행될 때

예) 신기능 1, 신기능 2, 코드개선, 긴급수정...
각각의 차원에서 작업한 뒤 확정된 것을 메인 차원에 통합


