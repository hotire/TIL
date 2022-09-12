# MySQL

### 설치 및 실행 

~~~shell
docker pull mysql
~~~

~~~shell
docker run --name mysql-container -e MYSQL_ROOT_PASSWORD=1234 -e MYSQL_DATABASE=flyway -e MYSQL_USER=hotire -e MYSQL_PASSWORD=1234 -d -p 3306:3306 mysql:latest
~~~

- d: 백그라운드 모드 
- p: 포트 포워딩 호스트:컨테이너
- e: 컨테이너 내에서 사용할 환경변수 설정
– name: 컨테이너 이름

### 컨테이너 bash 접속 

~~~shell
docker exec -it mysql-container bash
~~~

- it : interactive terminal 모드

~~~shell
mysql -u root -p
~~~
