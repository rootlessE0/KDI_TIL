```bash

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice
$ git init
Initialized empty Git repository in C:/Users/user/Desktop/branch_practice/.git/

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (master)
$ touch README.md

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (master)
$ git add .

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (master)
$ git commit -m 'Init'
[master (root-commit) 1531de9] Init
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README.md

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (master)
$ git log --oneline
1531de9 (HEAD -> master) Init

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (master)
$ git branch feature/test

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (master)
$ git branch
  feature/test
* master

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (master)
$ ^C

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (master)
$ ^C

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (master)
$ git checkout feature/test
Switched to branch 'feature/test'

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (feature/test)
$ ^C

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (feature/test)
$ touch test.txt

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (feature/test)
$ git add .

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (feature/test)
$ git commit -m 'Complete test page'
[feature/test 474671b] Complete test page
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test.txt

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (feature/test)
$ git log --oneline
474671b (HEAD -> feature/test) Complete test page
1531de9 (master) Init

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (feature/test)
$ git checkout master
Switched to branch 'master'

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (master)
$ ^C

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (master)
$ git merge feature/test
Updating 1531de9..474671b
Fast-forward
 test.txt | 0
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test.txt

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (master)
$ git log --oneline
474671b (HEAD -> master, feature/test) Complete test page
1531de9 Init

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (master)
$ git branch -d feature/test
Deleted branch feature/test (was 474671b).

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (master)
$ git checkout -b feature/main
Switched to a new branch 'feature/main'

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (feature/main)
$ touch main.txt

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (feature/main)
$ git add .

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (feature/main)
$ git commit -m 'Complete main'
[feature/main 968cd10] Complete main
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 main.txt

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (feature/main)
$ git log --oneline
968cd10 (HEAD -> feature/main) Complete main
474671b (master) Complete test page
1531de9 Init
user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (master)
$ touch hotfix.txt

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (master)
$ git add .

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (master)
$ git commit -m 'Hotfix'
[master 730d875] Hotfix
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 hotfix.txt

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (master)
$ git log --oneline
730d875 (HEAD -> master) Hotfix
474671b Complete test page
1531de9 Init

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (master)
$ git merge feature/main
Merge made by the 'recursive' strategy.
 main.txt | 0
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 main.txt

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (master)
$ git log --oneline
22fa089 (HEAD -> master) Merge branch 'feature/main'
730d875 Hotfix
968cd10 (feature/main) Complete main
474671b Complete test page
1531de9 Init

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (master)
$ git log --oneline --graph
*   22fa089 (HEAD -> master) Merge branch 'feature/main'
|\
| * 968cd10 (feature/main) Complete main
* | 730d875 Hotfix
|/
* 474671b Complete test page
* 1531de9 Init

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (master)
$ git branch -d feature/main
Deleted branch feature/main (was 968cd10).

user@DESKTOP-9GVGJPQ MINGW64 ~/Desktop/branch_practice (master)

```

