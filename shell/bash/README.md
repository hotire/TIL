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









