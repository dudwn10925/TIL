## CLI

- `GUI(Graphic User Interface)` : 그래픽을 통해 사용자와 컴퓨터가 상호작용하는 방식
- `CLI(Command Line Interface)` : 터미널을 통해 사용자와 컴퓨터가 상호작용하는 방식



## Command

- `pwd` : 현 위치 반환
- `cd ..` : 상위폴더로 이동, `cd ../..`
- `ls -al` : view list
- `mkdir` : make directory
- `touch` : make file
- `vi` : make file or modify file
  - `i` key 입력 : 파일 수정 
  - `Esc` + `:` + `wq` + `Enter` : 수정 완료
- `rm` : remove file
- `rm -r` : remove directory
- `mv` : 파일을 폴더로 이동 or 파일 이름 변경
- `code .` : vscode 열기
- `start .` : directory 열기



## 단축키

- `ctrl` + `a` : 커서 맨앞으로 이동
- `ctrl` + `e` : 커서 맨뒤로 이동
- `ctrl` + `w` : 커서 앞의 단어 삭제
- `ctrl` + `l` : clear는 아니지만 화면을 위로 올림
- `ctrl` + `insert` : copy
- `shitf` + `insert` : paste



## Git & GitHub

1. `Git` : 분산버전관리시스템 (히스토리 관리, 백업과 협업이 가능)

   분산버전관리시스템 < ------ > 중앙집중시스템

   - 누가 commit 기록을 남겼는지 확인, 최초 한 번만 설정(컴퓨터 1대)

     `git config --global user.name "name"`

     `git config --global user.email "email"`

   - 로컬저장소(git)

     - working directory : 사용자의 일반적인 작업이 일어나는 곳

     - staging area : commit을 위한 파일 및 폴더가 추가되는 곳

     - repository : staging area에 있던 파일 및 폴더의 변경사항을 저장하는 곳

       ![git_work](git/src=http%253A%252F%252Fblogfiles.naver.net%252FMjAxOTAyMjdfMjgg%252FMDAxNTUxMjI1MzEyOTE0.9g9R2dJrqgPVZ00cHGKxs_JETES6BCum8XxWMzl1yBUg.IxtC5sAMAf-PboVDCCCXXLrRgVlH9rkdRQ2DJrm0yUYg.PNG.gmkjh74%252F1.png&type=sc960_832)

       ---

       

   - command

     `git init` : 현재 작업 중인 directory를 Git으로 관리, '.git'파일 생성

     `git remote add <원격 저장소 name> <github repository address>` : 원격저장소 등록

     `git add` : working directory -> staging area

     `git status` : 'git add'가 잘 되었는지 확인

     `git commit -m "~"` : staging area -> repository, 저장소에 저장(^) 

     실제 폴더와 working directory에 존재

     `git log --oneline` : 'git commit -m "~"'이 잘 되었는지 확인

     `git push -u <원격 저장소 name> master` : 원격저장소에 업로드, 이후부터 `git push`만 입력

   - repository name(GitHub) = directory name

   - `vi .gitignore`

     - '.gitignore'에 쓰는 파일들은 무시하고 원격저장소에 업로드
     - '.git'과 같은 선상에 존재
     - 반드시 'git add' 전에 작성
     - `gitignore.io` : 자신의 개발 환경에 맞는 것을 찾아 복붙

2. `GitHub` : Git 기반의 repository, 원격저장소



## git pull

- `git clone <원격 저장소 주소>` : 해당 github에 push된 파일 및 폴더 복제,

​																'git init'과 'git remote add'는 이미 수행된 상태, `.`을 추가하면 바로 복제

- `git pull <원격 저장소 name> master` : 원격저장소에서 가져오기



## ex)

- 파일 트리에서

  ![파일트리](git/Root-Directory.png)

  **만약 ROOT를 git저장소로 생성하였다면(ROOT 폴더 내에 .git이 있음) MEDIA를 git저장소로 생성할 수 없음**

- 분산버전관리시스템(Git)에서

  <image입력>

- 'git commit'의 message를 title + content로 주고자 할 때

  `git commit` --> `i` 입력 --> `title` 입력 --> `Enter` * 2 --> `content` 작성 --> `Esc` + `:` + `wq` + `Enter`