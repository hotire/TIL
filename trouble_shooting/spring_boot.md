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