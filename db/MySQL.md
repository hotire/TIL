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



### Reference

- https://jojoldu.tistory.com/243