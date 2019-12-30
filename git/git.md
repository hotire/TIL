# Git

## Rebase

```shell
$ git checkout feature
$ git rebase master
```



## 명령어

### add 취소

git reset HEAD [file] 을 통해 파일을 선택해 add를 취소할 수 있다. 

뒤에 파일명이 없으면 add한 파일 전체를 취소한다.



### commit 취소하기

```shell
$ git reset --hard HEAD^
```

commit을 취소하고 해당 파일들은 staged 상태로 워킹 디렉터리에 보존

```shell
$ git reset --mixed HEAD^ // 기본 옵션
$ git reset HEAD^ // 위와 동일
```

commit을 취소하고 해당 파일들은 unstaged 상태로 워킹 디렉터리에 보존

```shell
$ git reset --hard HEAD^
```

commit을 취소하고 해당 파일들은 unstaged 상태로 워킹 디렉터리에서 삭제



### commit message 변경

```shell
$ git commit --amend
```



