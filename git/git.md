# Git

## Rebase

```shell
$ git checkout feature
$ git rebase master
```


### 여러개의 커밋로그를 하나로 묶기

```
git log --pretty=oneline
```
각 커밋을 한 라인으로 보여준다

커밋을 확인한 후 

```
git rebase -i HEAD~3
```
interactive rebase로 3개를 수정한다. 

```
pick 7c65355 Commit1
pick 2639543 Commit2
pick d442427 Commit3
```

```
pick 7c65355 Commit1
squash 2639543 Commit2
squash d442427 Commit3
```
squash로 변경하고 저장(wq)하면 

다른 vi창이 뜨면서 커밋 메시지를 rewrite할 수 있다. 

```
pick 7c65355 Commit
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


### 과거의 push 취소 
```
git log
```
commit 확인한다. 

바꾸려는 이전의 커밋으로 되돌린다. 

```
git rebase --interactive 
```

수정할 커밋에 pick -> edit으로 수정하고 저장한다.

```
commit --amend
```
내용을 수정하고 저장한다. 

```
git rebase --continue
```

```
git push --force
```
강제 푸시한다. 조금 더 안정한 방법으로 누군가 push를 하지 않은 상태에서 
git push --force를 실행하는 git push --force-with-lease를 사용할 수도 있다. 



## 기타

### refusing to merge unrelated histories

git에서는 서로 관련 기록이 없는 이질적인 두 프로젝트를 병합할 때 기본적으로 거부한다. 

```shell
git pull origin `branch` --allow-unrelated-histories
```




## Git 원리 

Git은 데이터를 저장하기 전에 항상 해시값을 구하고, 해시값을 기준으로 데이터를 관리한다. 

- SHA-1 해시 사용

### Objects

- 내용을 주소로 활용 (Content-addressable Key-Value Storage)

40글자의 해시 값 중 앞 두글자를 따서 디렉토리를 생성하고 나머지 38자로 파일을 생성한다.














