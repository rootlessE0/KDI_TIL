# Gitignore

> git으로 관리하지 않을 파일/폴더/특정확장자
>
> ![image-20201223093014640](C:%5CUsers%5Cuser%5CDesktop%5CTIL%5Cgit%5Cmd-images%5Cimage-20201223093014640.png)

```bash
data.csv # 특정 파일
*.png # 특정 확장자
secret/ # 특정 폴더
!profile.png # 모든 png는 빼고, profile.png는 넣고! (!는 not)
```

* `.gitignore`
  * 메모장에서 편집 금지!



* gitignore 파일은 vim, visual studio code에서 수정 가능하다.

* 모든 bmp 파일, data.csv, secret 폴더를 숨긴다.

* 이력을 모두 지우고 싶다면 .git 폴더를 날리면...

* OS(Windows/mac), 개발환경(IDE(통합개발환경; eclipse, pycharm), text editor), 특정 언어에서 발생하는 파일/폴더들

  * [gitignoreio](https://www.toptal.com/developers/gitignore) : 각 운영체제, 개발환경 별 제외해도 되는 언어 검색하는 사이트

    ex) 맥에서 파이썬 주피터 노트북을 머신러닝 한다.