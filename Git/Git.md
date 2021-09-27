# Git 기초

### Git 저장소 생성시키기

```bash
$ git init
Initialized empty Git repository in C:/Users/student/Desktop/test/.git/
```

- 폴더 내에 `.git`저장소가 생성이 되며, CLI(**Command-line interface**) 환경에서 master branch가 생긴다.

- `branch`란 독립된 작업을 수행하기 위한 개념이다. branch는 서로 다른 브랜치의 영향받지 않기 때문에, 여러 작업을 동시에 할 수 있음.

  다른 branch와 병합하여 하나의 branch로 만들 수도 있다.

  이런 식으로 여러 사람이 작업 시, 독립적으로 특정 작업을 수행하며, branch 단위로 작업 기록을 남기게 된다.

- `master`란 Git이 처음 저장소를 만들 때 생성되는 branch이다. 메인 branch이며, 배포와 관련된 작업을 관리하는 branch이다.

### 버전 관리하기

> 프로젝트 폴더 내에서 파일 및 폴더의 변경사항을 버전으로 기록한다.

###  **`add`**

```bash
$ git add <file> 
$ git add .             # 현재 디렉토리
$ git add a.txt b.txt   # 특정 파일
$ git add my_folder/    # 특정 폴더
$ git add *.md          # 특정 확장자
```

### `status` 살펴보기

```bash
$ touch README.md
$ git status
On branch master

No commits yet
# 트래킹 X 파일들(한번도 버전관리에 되지 않은 파일) ex) 파일 생성..
# Working Directory(첫번째통!)
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        README.md

nothing added to commit but untracked files present (use "git add" to track)
```

```bash
$ git add .
$ git status
On branch master

No commits yet
# 커밋될 변경사항들
# Staging Area (staged 상태인 파일들)
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   README.md

```

### `commit`

> 작업 공간에 있는 작업물들을 버전으로 만든다.

```bash
$ git commit # 메시지 편집 창(기본 Vim)
$ git commit -m '메시지'
[master (root-commit) 53dc80f] Add README.md
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README.md
 
$ git log
commit 53dc80f4be3fa19e749ab6a8558e4b98c8f12717 (HEAD -> master)
Author: edutak <edutak.ssafy@gmail.com>
Date:   Mon Sep 27 15:12:11 2021 +0900

    Add README.md
```

## 상태 명령어

### `status`

> 작업공간에서 작업물들의 여러 상태를 보여준다.

- Untracked : 커밋 완료된 이후 변경점을 발견하지 못함.
- Changes not staged for commit : 커밋 대상이 되지 않은 staging 안된 변경점들 
- Staging area(Changes to be committed) : 커밋될 변경점들

```bash
$ git status
On branch master
nothing to commit, working tree clean
```

### `log`

> 커밋된 이력을 조회한다.

```bash
$ git log # 전체 
commit 53dc80f4be3fa19e749ab6a8558e4b98c8f12717 (HEAD -> master)
Author: edutak <edutak.ssafy@gmail.com>
Date:   Mon Sep 27 15:12:11 2021 +0900

    Add README.md

$ git log -2 # 최근 2개
$ git log --oneline # 간략하게
53dc80f (HEAD -> master) Add README.md

$ git log --oneline -2 # 최근 2개를 간략하게
```

## Github을 이용하여 원격저장소(remote) 관리하기

### 원격저장소 등록하기

```bash
$ git remote add origin https://github.com/username/repository_name.git
```

- `origin` + github 저장소 url을 통해서 특정 url을 등록한다.

- 오류 메시지 : 특정 이름으로 이미 등록된 경우. 에러가 발생
  - url을 변경(`set-url`)하거나 해당 원격저장소를 삭제하고 다시 등록하는 명령어를 사용해서 변경

```bash
# 기존 URL을 잘못 지정
$ git remote add origin https://github.com/username/test.git
error: remote origin already exists. # 덮어쓰기 X
$ git remote rm origin # 삭제
$ git remote add origin https://github.com/username/test.git # 다시
```

### 원격저장소 `push` 하기

> 파일 및 폴더를 업로드하는 것이 아니라 당신의 commit(version)을 push하는 것이다.

```bash
$ git push origin master
```

- `origin`으로 지정된 원격저장소의 `master`로 `push`

- 오류메시지: 커밋 혹은 branch가 없는 경우

  ```bash
  $ git push origin master
  error: src refspec master does not match any
  error: failed to push some refs to 'https://github.com/username/test.git'
  ```

### 자신의 Github의 원격저장소 목록 보기

```bash
$ git remote -v
```

