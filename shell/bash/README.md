# Bash

![gradle](https://upload.wikimedia.org/wikipedia/commons/8/82/Gnu-bash-logo.svg)

쉘의 한 종류로 Bourne-agin shell 줄여서, bash라고 부릅니다.


- 쉘스크립트 문법을 체크해주는 사이트 : https://www.shellcheck.net/



### Getting Started

1. bak 디렉토리가 존재하지 않으면 bak 디렉토리를 생성한다.
2. log로 끝나는 파일를 bak 디렉토리로 cp 한다. 

```shell
#! /bin/bash
if ! [ -d bak ]; then
	mkdir bak
fi
echo 'copy log'
cp *.log bak
```



## 변수

쉘은 변수에 기본적으로 문자열을 저장하고 선언 없이도 사용 가능하다.

```shell
$ 변수 = 값
```



### $와 결합된 특수 변수

$와 특수 문자를 결합하면 특수한 의미를 갖는다.

- $# 명령을 제외하고 전달된 옵션과 인자의 개수 

  ```sh
  $ ./test.sh 1 2 3
  ```

  이렇게 할 경우 인자의 개수는 3개이다.

-  $숫자

  ```
  $ ./test.sh 1 2 3
  ```

  - $0은 명령을 의미한다. (./test.sh)
  - $1~ 3까지는 인자를 의미한다. (1, ,2 ,3)









