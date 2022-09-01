# Java

## TheadDump

1. jps 

Java Virtual Machine 프로세스 목록을 보여준다. 

ps -ef | grep 명령어 조합으로 실행중인 자바 프로세스 찾는는 것과 동일하다. 

- jps -m : 메인 메소드의 args 표시

- jps -v : jvm 파라미터 표시

2. jstack

jstack PID -> threadump.txt



## HeapDump

1. jps 

Java Virtual Machine 프로세스 목록을 보여준다. 

ps -ef | grep 명령어 조합으로 실행중인 자바 프로세스 찾는는 것과 동일하다. 

- jps -m : 메인 메소드의 args 표시

- jps -v : jvm 파라미터 표시

2. jmap

jmap -dump:format=b,file=파일이름.hprof pid 



