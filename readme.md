깃 기본 브랜치 생성<br/>
<br/>
git config --global user.name "(본인 이름)"<br/>
git config --global user.email "(본인 이메일)"<br/>
<br/>
확인 명령어<br/>
git config --global user.name<br/>
git config --global user.email<br/>
<br/>
기본 브랜치명 변경<br/>
git config --global init.defaultBranch main<br/>
<br/>
깃 프로젝트 관리 시작<br/>
해당폴더->깃바쉬-><br/>
git init<br/>
<br/>
폴더에 숨김모드로 .git 폴더 생성 확인<br/>
🛑 이 폴더를 지우면 Git 관리내역이 삭제됩니다. (현 파일들은 유지)<br/>
<br/>
깃 상태확인<br/>
git status<br/>
추적하지 않는(untracked) 파일: Git의 관리에 들어간 적 없는 파일<br/>
<br/>
소스트리 : gui로 되어있어 직관적이다. 특히 브랜치들을 볼때 , 명령어를 잘모를땐 쓰기 편하다.<br/>
<br/>
Git의 관리에서 특정 파일/폴더를 배제해야 할 경우<br/>
  a. 포함할 필요가 없을 때<br/>
자동으로 생성 또는 다운로드되는 파일들 (빌드 결과물, 라이브러리)<br/>
  b. 포함하지 말아야 할 때<br/>
보안상 민감한 정보를 담은 파일<br/>
.gitignore 파일을 사용해서 배제할 요소들을 지정할 수 있습니다.<br/>
.gitignore 형식<br/>

![image](https://user-images.githubusercontent.com/69129562/207556796-6e5da2cd-447e-429c-a3a9-934b283b9eab.png)
<br/>
파일 하나 담기<br/>
git add tigers.yaml<br/>
모든 파일 담기 -> working directory -> staging area<br/>
git add .<br/>
<br/>
타임캡슐 묻기(깃에 업로드 전에 1차 저장) - staging area -> local repo<br/>
git commit<br/>
커밋 메시지까지 함께 작성하기<br/>
git commit -m "FIRST COMMIT"<br/>
지난 커밋 내역 확인<br/>
git log<br/>
<br/>
add와 commit 한꺼번에<br/>
git commit -am "(메시지)"<br/>
<br/>
Git에서 과거로 돌아가는 두 방식<br/>
reset : 원하는 시점으로 돌아간 뒤 이후 내역들을 지웁니다.<br/>
git reset --hard (돌아갈 커밋 해시)<br/>
reset 하기 전 시점으로 복원해보기<br/>
git reset --hard<br/>
<br/>
revert : 되돌리기 원하는 시점의 커밋을 거꾸로 실행합니다.<br/>
git revert (되돌릴 커밋 해시)<br/>
<br/>
🛑커밋해버리지 않고 revert하기<br/>
git revert --no-commit (되돌릴  커밋 해시)<br/>
 -원하는 다른 작업을 추가한 다음 함께 커밋<br/>
 -취소하려면 git reset --hard<br/>
 <br/>
 ![image](https://user-images.githubusercontent.com/69129562/207556684-a38d9936-dcd8-4d95-8179-586efe6c0c49.png)
<br/>
 Branch: 분기된 가지 (다른 차원)<br/>
프로젝트를 하나 이상의 모습으로 관리해야 할 때<br/>
<br/>
예) 실배포용, 테스트서버용, 새로운 시도용<br/>
여러 작업들이 각각 독립되어 진행될 때<br/>
<br/>
예) 신기능 1, 신기능 2, 코드개선, 긴급수정...<br/>
각각의 차원에서 작업한 뒤 확정된 것을 메인 차원에 통합<br/>
<br/>
add-coach란 이름의 브랜치 생성<br/>
git branch add-coach<br/>
<br/>
브랜치 목록 확인<br/>
git branch<br/>
<br/>
add-coach 브랜치로 이동<br/>
git switch add-coach<br/>
<br/>
브랜치 생성과 동시에 이동하기<br/>
git switch -c new-teams<br/>
<br/>
브랜치 삭제하기<br/>
git branch -d (삭제할 브랜치명)<br/>
<br/>
지워질 브랜치에만 있는 내용의 커밋이 있을 경우<br/>
즉 다른 브랜치로 가져오지 않은 내용이 있는 브랜치를 지울 때는
-d 대신 -D(대문자)로 강제 삭제해야 합니다.<br/>
git branch -D (강제삭제할 브랜치명)<br/>
<br/>
브랜치 이름 바꾸기<br/>
git branch -m (기존 브랜치명) (새 브랜치명)<br/>
<br/>
여러 브랜치 내역을 보고싶을땐 소스트리를 이용하자.<br/>
<br/>

서로 다른 브랜치를 합치는 두 방식<br/>
merge : 두 브랜치를 한 커밋에 이어붙입니다.<br/>
<br/>
브랜치 사용내역을 남길 필요가 있을 때 적합한 방식입니다.<br/>
다른 형태의 merge에 대해서도 이후 다루게 될 것입니다.<br/>
rebase : 브랜치를 다른 브랜치에 이어붙입니다.<br/>
<br/>
한 줄로 깔끔히 정리된 내역을 유지하기 원할 때 적합합니다.<br/>
이미 팀원과 공유된 커밋들에 대해서는 사용하지 않는 것이 좋습니다.<br/>
<br/>
add-coach 브랜치를 main 브랜치로 merge<br/>

1. merge로 합치기<br/>
main 브랜치로 이동<br/>
아래의 명령어로 병합<br/>
git merge add-coach<br/>
:wq로 자동입력된 커밋 메시지 저장하여 마무리<br/>
<br/>
merge는 reset으로 되돌리기 가능<br/>
merge도 하나의 커밋<br/>
merge하기 전 해당 브랜치의 마지막 시점으로<br/>
<br/>
병합된 브랜치는 삭제<br/>
삭제 전 소스트리에서 add-coach 위치 확인<br/>
git branch -d add-coach<br/>
<br/>
2. rebase로 합치기<br/>
new-teams 브랜치를 main 브랜치로 rebase<br/>
new-teams 브랜치로 이동<br/>
🛑 merge때와는 반대!<br/>
아래의 명령어로 병합<br/>
git rebase main<br/>
소스트리에서 상태 확인<br/>
main 브랜치는 뒤쳐져 있는 상황<br/>
main 브랜치로 이동 후 아래 명령어로 new-teams의 시점으로 fast-forward<br/>
git merge new-teams<br/>
new-teams 브랜치 삭제<br/>
<br/>
브랜치 간 충돌<br/>
파일의 같은 위치에 다른 내용이 입력된 상황<br/>
1. merge 충돌 해결하기<br/>
오류 메시지와 git status 확인<br/>
당장 충돌 해결이 어려울 경우 아래 명령어로 merge 중단<br/>
git merge --abort<br/>
해결 가능 시 충돌 부분을 수정한 뒤 git add ., git commit으로 병합 완료<br/>
<br/>
2. rebase 충돌 해결하기<br/>
오류 메시지와 git status 확인<br/>
git rebase --abort<br/>
해결 가능 시<br/>
충돌 부분을 수정한 뒤 git add .<br/>
아래 명령어로 계속<br/>
git rebase --continue<br/>
충돌이 모두 해결될 때까지 반복<br/>
<br/>

원격 저장소 사용하기 (깃헙)<br/>
<br/>
1. 로컬에 원격 저장소 추가 후 푸시<br/>
git remote add origin (원격 저장소 주소) <br/>
로컬의 Git 저장소에 원격 저장소로의 연결 추가<br/>
원격 저장소 이름에 흔히 origin 사용. 다른 것으로 수정 가능<br/>
git branch -M main<br/>
git push -u origin main <br/>
로컬 저장소의 커밋 내역들 원격으로 push(업로드)<br/>
<br/>
원격 목록 보기<br/>
git remote<br/>
<br/>
원격 지우기 (로컬 프로젝트와의 연결만 없애는 것. GitHub의 레포지토리는 지워지지 않음)<br/>
git remote remove (origin 등 원격 이름)<br/>
<br/>
Git clone: Git 관리내역 포함 다운로드<br/>
터미널이나 Git Bash에서 대상 폴더 이동 후<br/>
git clone (원격 저장소 주소)<br/>
<br/>
1. 원격으로 커밋 밀어올리기(push)<br/>
git push<br/>
2. 원격의 커밋 당겨오기(pull)<br/>
git pull<br/>
<br/>
pull 할 것이 있을 때 push를 하면?<br/>
로컬에서 Leopards의 manager를 Dooli로 수정<br/>
GitHub에서 Leopards의 coach를 Lupi로 수정<br/>
push 해보기<br/>
원격에 먼저 적용된 새 버전이 있으므로 적용 불가<br/>
pull 해서 원격의 버전을 받아온 다음 push 가능<br/>
<br/>
push 할 것이 있을 시 pull 하는 두 가지 방법<br/>
git pull --no-rebase    -> merge 방식<br/>
git pull --rebase    -> rebase 방식<br/>
수행후 push<br/>
<br/>
1. 로컬에서 브랜치 만들어 원격에 push 해보기<br/>
git push 바로 하면 대상을 명시하라는 메시지 나타남<br/>
아래 명령어로 원격의 브랜치 명시 및 기본설정<br/>
git push -u origin from-local<br/>
브랜치 목록 살펴보기<br/>
git branch --all<br/>
<br/>
2. 원격의 브랜치 로컬에 받아오기<br/>
아래 명령어로 원격의 변경사항 확인<br/>
git fetch<br/>
아래 명령어로 로컬에 같은 이름의 브랜치를 생성하여 연결하고 switch<br/>
git switch -t origin/from-remote<br/>
원격의 브랜치 삭제<br/>
git push (원격 이름) --delete (원격의 브랜치명)<br/>
<br/>
![image](https://user-images.githubusercontent.com/69129562/207843100-bd011e50-1550-4231-99f8-d164c05116ed.png)
<br/>
commit되어 레포지토리에 들어간 후 수정사항이 발생하면 tracked 파일로써 스테이징을 기다리게 됩니다.<br/>
<br/>
Working directory<br/>
untracked: Add된 적 없는 파일, ignore 된 파일<br/>
tracked: Add된 적 있고 변경내역이 있는 파일<br/>
git add 명령어로 Staging area로 이동<br/>
<br/>
Staging area<br/>
커밋을 위한 준비 단계<br/>
예시: 작업을 위해 선택된 파일들<br/>
git commit 명령어로 repository로 이동<br/>
<br/>
Repository<br/>
.git directory라고도 불림<br/>
커밋된 상태<br/>
<br/>
git rm<br/>
tigers.yaml를 삭제해본 뒤 git status로 살펴보기<br/>
<br/>
파일의 삭제가 working directory에 있음<br/>
git reset --hard로 복원<br/>

git rm tigers.yaml로 삭제하고 git status로 살펴보기<br/>
<br/>
파일의 삭제가 Staging area에 있음<br/>
git reset --hard로 복원<br/>
 rm 명령을 실행하면 워킹 디렉터리의 해당 파일을 삭제 후에 파일이 삭제 되었다는 내역을 Staging Area에 추가하는 것입니다.<br/>
 이때의 tigers.yaml은 deleted 상태이면서 Staged 상태입니다.
<br/>
git mv<br/>
tigers.yaml를 zzamtigers.yaml로 이름변경 뒤 git status로 살펴보기<br/>
복원 후 git mv tigers.yaml zzamtigers.yaml로 실행 뒤 비교<br/>
<br/>
파일을 staging area에서 working directory로<br/>
git restore --staged (파일명)<br/>
--staged를 빼면 working directory에서도 제거<br/>
예전: git reset HEAD (파일명)<br/>
<br/>
reset의 세 가지 옵션<br/>
--soft: repository에서 staging area로 이동<br/>
--mixed (default): repository에서 working directory로 이동<br/>
--hard: 수정사항 완전히 삭제<br/>
<br/>
![image](https://user-images.githubusercontent.com/69129562/207845247-d9c7afeb-59f7-43f0-b6ef-70e4c9ff713c.png)
<br/>
Git의 HEAD<br/>
현재 속한 브랜치의 가장 최신 커밋<br/>
switch로 브랜치 이동해보기<br/>
main과 delta-branch<br/>
<br/>
checkout으로 앞뒤 이동해보기<br/>
git checkout HEAD^<br/>
^ 또는 ~: 갯수만큼 이전으로 이동<br/>
git checkout HEAD^^^, git checkout HEAD~5<br/>
커밋 해시를 사용해서도 이동 가능<br/>
git checkout (커밋해시)<br/>
git checkout - : (이동을) 한 단계 되돌리기<br/>
git reset HEAD(원하는 단계) (옵션)<br/>
<br/>
fetch와 pull의 차이<br/>
fetch: 원격 저장소의 최신 커밋을 로컬로 가져오기만 함<br/>
pull: 원격 저장소의 최신 커밋을 로컬로 가져와 merge 또는 rebase<br/>
원격의 새 브랜치 확인<br/>
git checkout origin/(브랜치명)<br/>
git switch -t origin/(브랜치명)<br/>
<br/>
global 설정과 local 설정
config를 --global과 함께 지정하면 전역으로 설정됩니다.
특정 프로젝트만의 user.name과 user.email 지정해보기
현재 모든 설정값 보기
git config (global) --list
기본 에디터 수정
git config --global core.editor "code --wait"

1. 내용 확인하며 hunk별로 스테이징하기
깃의 변경사항 단위를 hunk라고 합니다.
아래 명령어로 hunk별 스테이징 진행
git add -p
옵션 설명을 보려면 ?입력 후 엔터
y 또는 n로 각 헝크 선택
2. 변경사항을 확인하고 커밋하기
git commit -v

커밋하기 애매한 변화 치워두기
1. 아래 명령어로 치워두기
git stash
2. 원하는 시점, 브랜치에서 다시 적용
git stash pop
3. 원하는 것만 stash 해보기
git stash -p
4. 메시지와 함께 스태시
git stash -m 'Add Stash3'
스태시 목록 보기
git stash list.

커밋 메시지 변경
git commit --amend
커밋 메시지 한 줄로 변경
git commit --amend -m 'Add members to Panthers and Pumas'

git rebase -i (대상 바로 이전 커밋)
과거 커밋 내역을 다양한 방법으로 수정 가능

![image](https://user-images.githubusercontent.com/69129562/207854109-4132ecdb-8fa6-4a9e-91f0-7bfbbcbc1cbf.png)

git clean -> Git에서 추적하지 않는 파일들 삭제

![image](https://user-images.githubusercontent.com/69129562/207868533-97b20dfe-499e-4246-a4f7-b34b6db123d3.png)

git restore -> 특정 파일을 지정된 상태로 복구
파일을 수정하고 아래 명령어들 사용해보기
git restore (파일명)
-워킹 디렉토리의 특정 파일 복구
-파일명 자리에 . : 모든 파일 복구

변경상태를 스테이지에서 워킹 디렉토리로 돌려놓기
git restore --staged (파일명)

파일을 특정 커밋의 상태로 되돌리기
git restore --source=(헤드 또는 커밋 해시) 파일명

git reflog
reset으로 사라진 커밋을 복구
reflog는 프로젝트가 위치한 커밋이 바뀔 때마다 기록되는 내역을 보여주고
이를 사용하여 reset하기 이전 시점으로 프로젝트를 복구할 수 있습니다.

커밋에 태그 달아보기
lightweight -	특정 커밋을 가리키는 용도
annotated	 - 작성자 정보와 날짜, 메시지, GPG 서명 포함 가능
마지막 커밋에 태그 달기 (lightweight)
git tag v2.0.0
현존하는 태그 확인
git tag
원하는 태그의 내용 확인
git show v2.0.0
태그 삭제
git tag -d v2.0.0
마지막 커밋에 태그 달기 (annotated)
git tag -a v2.0.0
입력 후 메시지 작성 또는
git tag v2.0.0 -m '자진모리 버전' - (-m 태그가 -a 태그 암시)
원하는 커밋에 태그 달기
git tag (태그명) (커밋 해시) -m (메시지)
원하는 패턴으로 필터링하기
git tag -l 'v1.*'
원하는 버전으로 체크아웃
git checkout v1.2.1

원격에 태그 동기화
특정 태그 원격에 올리기
git push (원격명) (태그명)
특정 태그 원격에서 삭제
git push --delete (원격명) (태그명)
로컬의 모든 태그 원격에 올리기
git push --tags

![image](https://user-images.githubusercontent.com/69129562/207874810-7fa383cf-27a1-423e-b78f-1732583b99b1.png)
cherry-pick 명령어는 특정한 commit 하나만 콕 찝어서 현재 HEAD가 가리키는 branch에 추가할 수 있게 해준다.
Cherry 커밋 main 브랜치로 가져오기
main 브랜치에서 실행
git cherry-pick (체리의 해시)
다른 브랜치에서 파생된 브랜치 옮겨붙이기
rebase --onto 옵션 사용
fruit 브랜치에서 파생된 citrus 브랜치를 main 브랜치로 옮겨붙이기
git rebase --onto (도착 브랜치) (출발 브랜치) (이동할 브랜치) -> git rebase --onto main fruit citrus
rebase --onto를 되돌리려면?

![image](https://user-images.githubusercontent.com/69129562/207876493-ebc45b58-9413-4fb3-82e7-c4f61653917a.png)

reset은 브랜치별로 이뤄지므로, rebase --onto로 영향을 받은
모든 브랜치들에서 하나하나 리셋을 진행해주어야 합니다.
혹은 다시 옮겨붙이는 방법도 있죠.
현재 이번 실습으로 변화가 일어난 브랜치는
main(패스트포워드 됨)과 citrus 이 둘입니다.
1. main 브랜치
main은 그리로 옮겨붙여진 citrus로 fastforward된 것이 마지막 액션이므로
reflog의 기록상에서 그 이전 기록으로 reset --hard를 하면 됩니다.
lemon과 lime이 추가되기 전으로 돌아가는거죠.
2. citrus 브랜치
방법 A
그리고 citrus 브랜치는 해당 브랜치가 옮겨지기 전 마지막 커밋인
commit: Lime 부분을 reflog에서 찾아 그리로 reset --hard하면 됩니다.
방법 B
다른 방법으로는, 다시 rebase --onto를 사용해서
citrus의 커밋들을 main으로부터 도로
fruit브랜치의 orange 부분으로 옮기는 것입니다.
그러러면 orange 커밋으로 checkout 한 다음
그곳에서 새 브랜치를 만들고 (temp라 가정하죠)
git rebase --onto temp main citrus
위 명령어로 citrus의 두 커밋들을 해당 위치로 옮겨붙인 뒤
temp 브랜치는 삭제해주시면 됩니다.

다른 커밋들을 하나로 묶어 가져오기
merge --squash 옵션 사용
root 브랜치의 마디들을 하나로 묶어 main 브랜치로 가져오기
git merge --squash (대상 브랜치)
일반 merge : A와 B 두 브랜치를 한 곳으로 이어붙임

![image](https://user-images.githubusercontent.com/69129562/207878949-b9e5cac8-e0b5-4c75-bd8b-b4c37fc9559f.png)


merge --squash : B 브랜치의 마디들을 복사해다가 한 마디로 모아 A 브랜치에 붙임 (staged 상태로)

![image](https://user-images.githubusercontent.com/69129562/207879298-9ddcff5e-9b7d-4069-9175-6bf0fb35c8b7.png)

각 커밋마다의 변경사항 함께 보기
git log -p
최근 n개 커밋만 보기
git log -(갯수)
통계와 함께 보기
git log --stat
한 줄로 보기
git log --oneline
변경사항 내 단어 검색
git log -S (검색어)
커밋 메시지로 검색
git log --grep (검색어)
자주 사용되는 그래프 로그 보기
git log --all --decorate --oneline --graph
--all : 모든 브랜치 보기
--graph : 그래프 표현
--decorate : 브랜치, 태그 등 모든 레퍼런스 표시

워킹 디렉토리의 변경사항 확인
git diff
파일명만 확인
git diff --name-only
스테이지의 확인
git diff --staged
커밋간의 차이 확인
git diff (커밋1) (커밋2)
-커밋 해시 또는 HEAD 번호로
-현재 커밋과 비교하려면 이전 커밋만 명시
브랜치간의 차이 확인
git diff (브랜치1) (브랜치2)

파일의 부분별로 작성자 확인하기
git blame (파일명)
특정 부분 지정해서 작성자 확인하기
git blame -L (시작줄) (끝줄, 또는 +줄수) (파일명)

git bisect
이진 탐색 알고리즘으로 문제의 발생 시점을 찾아냅니다.
이진 탐색 시작
git bisect start
오류발생 지점임을 표시
git bisect bad
의심 지점으로 이동
git checkout (해당 커밋 해시)
오류 발생 않을 시 양호함 표시
git bisect good
원인을 찾을 때까지 반복
git bisect good/bad
이진 탐색 종료
git bisect reset

Git Hooks
Git상의 이벤트마다 자동으로 실행될 스크립트를 지정합니다.
📁 Git Hooks 폴더 보기
프로젝트 폴더 내 .git > hooks 폴더 확인
파일 끝에 .sample을 없애면 훅 실행파일이 됨

서브모듈
프로젝트 폴더 안에 또 다른 프로젝트가 포함될 때 사용
여러 프로젝트에 사용되는 공통모듈일 때 유용

![image](https://user-images.githubusercontent.com/69129562/207890893-4d101f3c-d705-481d-8417-bd21db889748.png)

main-project에 서브모듈로 submodule 프로젝트 추가
main-project 디렉토리상 터미널에서 아래 명령어 실행
git submodule add (submodule의 GitHub 레포지토리 주소) (하위폴더명, 없을 시 생략)
-프로젝트 폴더 내 submodule폴더와 .gitmodules 파일 확인
-스테이지된 변경사항 확인 뒤 커밋
-양쪽 모두 수정사항 만든 뒤 main-project에서 git status로 확인
-submodule의 변경사항은 포함되지 않음 확인
-main-project에서 변경사항 커밋 뒤 푸시
-submodule에서 변경사항 커밋 뒤 푸시
-main-project에서 상태 확인
-main-project에서 커밋, 푸시 뒤 GitHub에서 확인

서브모듈 업데이트
1. main-project 새로운 곳에 clone하기 -> 이런 프로젝트를 Clone 하면 기본적으로 서브모듈 디렉토리는 빈 디렉토리이다.
2. 아래 명령어들로 서브모듈 init 후 클론
git submodule init (특정 서브모듈 지정시 해당 이름)
git submodule update
3. GitHub에서 submodule에 수정사항 커밋
main-project에서 아래 명령어로 업데이트
git submodule update --remote
서브모듈 안에 또 서브모듈이 있을 시: --recursive 추가

13 1

