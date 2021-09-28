## `config`

- git  설정
  - 기본 에디터 : `vim` => `vscode`로 변경 (커밋 시, vscode를 통해 커밋 메세지 작성)

```bash
$ git config --global core.editor "code --wait"
```

## `.gitignore` 

> git으로 관리하지 않을 파일 목록들

```bash
# 특정 파일
data.csv
# 특정 폴더
secret/
# 특정 확장자 (*)
```

- 일반적인 개발 환경에서 필수적으로 등록하는 예시

  - OS, IDE(eclipse) / Text editor(vs code), 특정 언어나 프레임워크에서 생성되는 파일

    - ex) 임시파일 혹은 실행에 필요한 파일들

    - https://gitignore.io/

      - 예시) `windows`, `Java`, `Eclipse` 

        ```bash
        # User-specific stuff
        .idea/**/workspace.xml
        .idea/**/tasks.xml
        .idea/**/usage.statistics.xml
        .idea/**/dictionaries
        .idea/**/shelf
        ```

    - github gitignore도 존재한다.

## `git clone`

> 새로운 프로젝트를 시작할 때, 타인의 github 저장소를 복제하여 시작하고자 하는 경우

- git init으로 원격저장소를 만들 필요가 없어지고, 복제된 git 저장소에서 이어서 작업



## push error

### 에러 상황

> 로컬 작업을 github으로 push할 때, github와, 로컬 git과의 commit이 일치하지 않는 경우(충돌)

### 해결

#### 1. pull

```bash
$ git pull origin master
```

- branch 병합(merge)이 발생함. (merge commit)
- 다시 push 하여, 원격 저장소(github)에 동기화

#### 2. push

- pull 명령어로 병합한 master branch를 원격저장소에 push한다.