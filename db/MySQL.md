# MySQL

## 인덱스 

인덱스는 결국 지정한 컬럼들을 기준으로 메모리 영역에 일종의 목차를 생성하는 

### 주요 특징 
- 인덱스 탐색은 Root -> Branch -> Leaf -> 디스크 저장소 순으로 진행된다. 
- 인덱스의 두번째 컬럼은 첫 번째 컬럼에 의존해서 정렬된다.


### 인덱스 키 값의 크기 

인덱스 역시 페이지 단위로 관리되며 페이지는 16KB 로 크기가 고정된다.

~~~
만약 인덱스의 크기가 16 Byte 경우 

자식노드(Branch, Leaf)의 주소 12 Byte 정도라고 가정하면 

16*1024 / (16+12) = 585 하나의 페이지에 585개 저장가능하다.

인덱스의 크기가 커짐에 따라서 페이지 성능 이슈가 생긴다.

~~~

### 인덱스 컬럼 기준 

> 카디널리티(Cardinality)란 해당 컬럼의 중복된 수치를 나타냅니다.
> 예를 들어 성별, 학년 등은 카디널리티가 낮다고 얘기합니다.
> 반대로 주민등록번호, 계좌번호 등은 카디널리티가 높다고 얘기합니다.

1. 만약 여러 컬럼으로 인덱스를 잡는다면? :  카디널리티가가 높은순에서 낮은순으로 구성하는게 좋다.
2. 여러 컬럼으로 인덱스시 조건 누락 : 첫번째 인덱스 컬럼이 조회 쿼리에 없으면 인덱스를 타지 않는다는 점을 기억하시면 됩니다.


### 인덱스 조회시 주의 사항

- between, like, <, > 등 범위 조건은 해당 컬럼은 인덱스를 타지만, 그 뒤 인덱스 컬럼들은 인덱스가 사용되지 않습니다.

즉, group_no, from_date, is_bonus으로 인덱스가 잡혀있는데 조회 쿼리를 where group_no=XX and is_bonus=YY and from_date > ZZ등으로 잡으면 is_bonus는 인덱스가 사용되지 않습니다. 

- 반대로 =, in 은 다음 컬럼도 인덱스를 사용합니다.
	- in은 결국 =를 여러번 실행시킨 것이기 때문입니다.
	- 단, in은 인자값으로 상수가 포함되면 문제 없지만, 서브쿼리를 넣게되면 성능상 이슈가 발생합니다.
	- in의 인자로 서브쿼리가 들어가면 서브쿼리의 외부가 먼저 실행되고, in 은 체크조건으로 실행되기 때문입니다.

- AND연산자는 각 조건들이 읽어와야할 ROW수를 줄이는 역할을 하지만, or 연산자는 비교해야할 ROW가 더 늘어나기 때문에 풀 테이블 스캔이 발생할 확률이 높습니다.

- 인덱스로 사용된 컬럼값 그대로 사용해야만 인덱스가 사용됩니다. 

- null 값의 경우 is null 조건으로 인덱스 레인지 스캔 가능



## subquery

서브 쿼리를 사용하면 단위 처리별로 쿼리를 독립시킬 수 있다. 조인처럼 여러 테이블을 섞어두는 형태가 아니라서 쿼리의 가독성도 높아지고, 
복잡한 쿼리도 손쉽게 작성할 수 있다. 하지만 MySQL 서버는 서브 쿼리를 최적으로 실행하지 못할 때가 많다. 가장 대표적으로 FROM 절에 사용되는 서브 쿼리나 WHERE 절의 IN (subquery) 구문은 가장 최신 버전 에서도 그다지 효율적이지 않다.


### 상관 서브 쿼리 (Correlated subquery)

서브 쿼리 외부에서 정의된 테이블의 칼럼을 참조해서 검색을 수행할 때 상관 서브 쿼리라고 한다.

ex ) 

~~~sql

SELECT *

FROM employees e

WHERE EXISTS

    ( SELECT 1

    FROM dept_emp de

    WHERE de.emp_no=e.emp_no

        AND de.from_date BETWEEN '2000-01-01' AND '2011-12-30' )
~~~

- EXISTS 이하의 서브 쿼리에서는 dept_emp 테이블에서 지정된 기간 내에 부서가 변경된 사원을 검색하고 있다. 
상관 서브 쿼리는 외부 쿼리보다 먼저 실행되지 못하기 때문에 일반적으로 상관 서브 쿼리를 포함하는 비교 조건은 범우 지헤나 조건이 아니라 체크 조건으로 사용된다.


### 커버링 인덱스 

이처럼 쿼리를 충족시키는 데 필요한 모든 데이터를 갖고 있는 인덱스를 커버링 인덱스 (Covering Index 혹은 Covered Index) 라고합니다.

좀 더 쉽게 말씀드리면 SELECT, WHERE, ORDER BY, GROUP BY 등에 사용되는 모든 컬럼이 인덱스의 구성요소인 경우를 얘기합니다.

### 인덱스 컨디션 푸시다운 인덱스

https://jojoldu.tistory.com/474

### 인덱스 풀 스캔 (range 스캔이 아님)


### Non Clustered Key와 Clustered Key


- Clustered Key : PK키 (PK가 없을 때 유니크키, 둘다 없을 경우 6byte의 Hidden Key, rowid를 생성함) 테이블당 1개만 존재


- Non Clustered Key : 일반적인 인덱스, 여러개 생성 가능

1. Non Clustered Key (일반적인 인덱스) 에는 인덱스 컬럼의 값들과 Clustered Key (PK) 의 값이 포함되어 있음
2. Clustered Key 만이 실제 테이블의 row 위치를 알고 있음


MySQL에서는 Non Clustered Key에 Non Clustered Key에는 데이터 블록의 위치가 없기 때문에 Clustered Key가 항상 포함된다. 

즉, 인덱스 조건에 부합한 where 조건이 있더라도 select에 인덱스에 포함된 컬럼 외에 다른 컬럼값이 필요할때는 Non Clustered Key에 있는 Clustered Key 값으로 데이터 블록을 찾는 과정이 필요합니다.

커버링 인덱스는 여기서 "2. 실제 데이터 접근" 의 행위 없이 인덱스에 있는 컬럼값들로만 쿼리를 완성하는 것을 이야기 합니다.


### Reference

- https://jojoldu.tistory.com/243
- https://jojoldu.tistory.com/476#recentEntries
