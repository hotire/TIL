# version up

## 2.2.0

### Web 
- encoding default utf8로 인해 content-type:application/json;charset=utf8 depreacated
  : Message convert 수정


### Reactive
- encoding default utf8로 인해 content-type:application/json;charset=utf8 depreacated
: codec 수정 

### MySQL-Connector-J 8
5 -> 8로 변경되었다. 

- driver 변경 (com.mysql.jdbc.driver -> com.mysql.cj.jdbc.driver)
- xml기반에서 사용하던 '&amp;' 사용할 수 없다. 
- utf8mb4는 utf8으로 자동 매핑된다. 
- timezone을 명시해야 하는데, 이로 인한 이슈가 존재한다 만약 server / client가 다른 timezone을 사용하였다면 버전업이 상당이 까다롭다.


### JUnit5 
JUnit5 드디어 의존성으로 들어왔다.

### Batch

ItemWriter가 필수 조건으로 바뀌었다.

- NoOpItemWriter() 와 같은 아무것도 하지 않는 Writer를 넣어줘야 한다.
