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



### commit 취소

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



### push 취소

1. commit 되돌린다. 

   ```shell
   $ git reset HEAD^
   ```

2. 되돌려진 상태에서 다시 commit 한다.

   ```shell
   $ git commit -m ""
   ```

3. 강제로 푸시한다. 

   -  -f 옵션
     –force 옵션과 동일하다.
   -  +[branch name]
     해당 branch를 강제로 push한다.
     

## Git Commit Message 규칙

#### 부정문 `Don't`을 사용한다. 

Not use가 아닌 Don't use 이다.

#### 오타 수정은  Correct misspelled text가 아니다.

Fix typo이다. 



