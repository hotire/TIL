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

- $$ 현재 프로세스의 ID

- $? 직전 명령의 리턴 값, 명령에 따라 값이 다르지만 대부분 성공 시 0을 리턴

### 인용 부호

- \는 Escape 문자로 특수 의미를 갖는 문자를 일반 문자로 해석되도록 한다.

- "" double quotes로 하나의 문자열로 인식되로록 한다. \ $ ' 만 해석한다.

- ''  single quotes로 하나의 문자열로 인식되도록 하고, 모든 특수 문자를 해석하지 않는다. 

  ```shell
  $echo "$USER" -> user
  $echo '$USER' -> $USER
  ```

- ``는 backticks로 명령의 결과로 인식된다. 

  ```
  $ `date +%F` -> 2020-01-12
  ```

  

 







