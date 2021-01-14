# Git 기초 문법

> Git은 분산형 버전관리시스템(DVCS)이다.

## Git 사전 준비

1. 윈도우 :  [git bash](https://gitforwindows.org/)를 설치한다.
2. 로컬 설정

```bash
$ git config --global user.name '____'
$ git config --global user.email '____'
```

* 처음 git을 설치하면, commit을 하는 작성자(author)를 설정해야 한다.

* email 정보는 github에 등록된 이메일을 설정하는 것을 추천

* 설정된 내용을 확인하기 위해서는 아래의 명령어를 입력한다.

  ```bash
  $ git config --global -l
  user.name=edutak
  user.email=edutak.ssafy@gmail.com
  ```
  * 오프라인 강의장에서 하는 경우 반드시 체크

## 기초 흐름

> 작업 => add => commit
>
> 작업이 끝나면, 커밋할 파일을 모아서(add), 커밋한다.(버전을 기록한다.)

### 0. 저장소 설정

```bash
$ git init
Initialized empty Git repository in C:/Users/i/Desktop/정리/.git/
(master) $
```

* git 저장소로 활용하기 위해서는 위의 명령어를 활용한다.
  * `.git` 폴더가 생성
  * `(master)` 로 현재 작업중인 브랜치 확인

### 1. `add`

> 커밋을 위한 파일 목록(staging area)

```bash
$ git add .     # 현재 디렉토리 
$ git add a.txt # 특정 파일
$ git add a.txt b.txt # 여러 파일
$ git add md-images/ # 특정 폴더
```

* 실습

```bash
$ touch test.txt
```

* add 전 모습

  ```bash
  $ git status
  On branch master
  
  No commits yet
  # 트래킹이 되지 않는 파일 : WD O
  Untracked files:
    # git add 명령어를 사용!
    # 커밋이 될 것에 포함시키기 위하여..
    (use "git add <file>..." to include in what will be committed)
          test.txt
  # 맨 마지막 줄 : 총 정리..
  # nothing added to commit / 커밋하기 위해 추가된 것 X : staging area X
  # untracked files present : WD O
  nothing added to commit but untracked files present (use "git add" to track)
  ```

* add 후 모습

  ```bash
  $ git add .
  $ git status
  On branch master
  
  No commits yet
  # 커밋이 될 변경사항 : SA O
  Changes to be committed:
    (use "git rm --cached <file>..." to unstage)
    		# 새 파일 : test.txt
          new file:   test.txt
  ```

### 2. `commit`

> 버전을 기록 (스냅샷)

```bash
$ git commit -m '커밋 메시지'
[master (root-commit) 93fff17] 커밋메시지
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test.txt
```

* 커밋 메시지는 현재 작업의 내용을 알 수 있도록 명확하게 작성한다.

* 커밋 이력을 확인하기 위해서는 아래의 명령어를 활용한다.

  ```bash
  $ git log
  commit 93fff1719414946bab471e8f9de13a44909fd0ca (HEAD -> master)
  Author: edutak <edutak.ssafy@gmail.com>
  Date:   Tue Dec 22 14:35:50 2020 +0900
  
      커밋메시지
  ```

  * 추가 옵션

    ```bash
    $ git log -1
    $ git log --oneline
    93fff17 (HEAD -> master) 커밋메시지
    $ git log --oneline -1
    ```

## 상태 확인

> git 저장소의 현재 상태는 status로 확인하는 습관을 가지자.

```bash
$ git status
```







